# OAuth 常用的 SDK 示例 {#concept_264755 .concept}

本文基于 Spring Boot OAuth2 和 Pac4J，为您介绍 OAuth 常用的 SDK 示例的相关配置。

## Spring Boot OAuth2 示例 {#section_pwc_2kd_832 .section}

参考 [Spring Boot and OAuth2](https://spring.io/guides/tutorials/spring-boot-oauth2/)文档及示例，主要做以下两点修改：

-   配置文件改为阿里云对应的配置。

    ``` {#codeblock_u90_8hq_qgs}
    aliyun:
        client:
          clientId: 4151950823846923577
          clientSecret: 6EwN4qutnZuchG6n677Ie33SsjAhwyTpcOMSoIo6v0gqJtw4QcHhERVXfqzcWgMB
          accessTokenUri: https://oauth.aliyun.com/v1/token
          userAuthorizationUri: https://signin.aliyun.com/oauth2/v1/auth
          tokenName: access_token
          authenticationScheme: query
          clientAuthenticationScheme: form
        resource:
          userInfoUri: https://oauth.aliyun.com/v1/userinfo
    ```

-   修改重定向 URI。

    修改`OAuth2ClientAuthenticationProcessingFilter`中的回调地址，改成与应用中的配置相同。 例如：应用配置的是`http://localhost:8080/login/aliyun`，则把代码中的回调地址替换为`/login/aliyun`。

    整体示例代码如下：

    ``` {#codeblock_zfa_953_d30}
    public class WebApplication extends WebSecurityConfigurerAdapter {
    
      @Autowired
      OAuth2ClientContext oauth2ClientContext;
    
      @RequestMapping("/user")
      public Principal user(Principal principal) {
        return principal;
      }
    
      @Override
      protected void configure(HttpSecurity http) throws Exception {
        // @formatter:off
        http.antMatcher("/**").authorizeRequests().antMatchers("/", "/login**", "/webjars/**").permitAll().anyRequest()
            .authenticated().and().exceptionHandling()
            .authenticationEntryPoint(new LoginUrlAuthenticationEntryPoint("/")).and().logout()
            .logoutSuccessUrl("/").permitAll().and().csrf()
            .csrfTokenRepository(CookieCsrfTokenRepository.withHttpOnlyFalse()).and()
            .addFilterBefore(ssoFilter(), BasicAuthenticationFilter.class);
        // @formatter:on
      }
    
      public static void main(String[] args) {
        SpringApplication.run(WebApplication.class, args);
      }
    
      @Bean
      public FilterRegistrationBean oauth2ClientFilterRegistration(OAuth2ClientContextFilter filter) {
        FilterRegistrationBean registration = new FilterRegistrationBean();
        registration.setFilter(filter);
        registration.setOrder(-100);
        return registration;
      }
    
      private Filter ssoFilter() {
        OAuth2ClientAuthenticationProcessingFilter aliyunFilter = new OAuth2ClientAuthenticationProcessingFilter(
            "/login/aliyun");
        OAuth2RestTemplate aliyunTemplate = new OAuth2RestTemplate(aliyun(), oauth2ClientContext);
        aliyunFilter.setRestTemplate(aliyunTemplate);
        UserInfoTokenServices tokenServices = new UserInfoTokenServices(aliyunResource().getUserInfoUri(),
            aliyun().getClientId());
        tokenServices.setRestTemplate(aliyunTemplate);
        aliyunFilter.setTokenServices(tokenServices);
        return aliyunFilter;
      }
    
      @Bean
      @ConfigurationProperties("aliyun.client")
      public AuthorizationCodeResourceDetails aliyun() {
        return new AuthorizationCodeResourceDetails();
      }
    
      @Bean
      @ConfigurationProperties("aliyun.resource")
      public ResourceServerProperties aliyunResource() {
        return new ResourceServerProperties();
      }
    
    }
    ```


## Pac4J 示例 {#section_12k_zev_o29 .section}

参考[Pac4J](http://www.pac4j.org/)的 spring-webmvc-pac4j 示例，进行以下操作：

-   创建`AliyunOidcClient`。

    ``` {#codeblock_gru_1yf_rc4}
    public class AliyunOidcClient extends OidcClient<OidcProfile, OidcConfiguration> {
        public AliyunOidcClient() {
    
        }
    
        public AliyunOidcClient(OidcConfiguration configuration) {
            super(configuration);
        }
    
        @Override
        protected void clientInit() {
            CommonHelper.assertNotNull("configuration", this.getConfiguration());
            this.getConfiguration().defaultDiscoveryURI("https://oauth.aliyun.com/.well-known/openid-configuration");
            OidcProfileCreator<OidcProfile> profileCreator = new OidcProfileCreator(this.getConfiguration());
            profileCreator.setProfileDefinition(new OidcProfileDefinition((x) -> {
                return new OidcProfile();
            }));
            this.defaultProfileCreator(profileCreator);
            super.clientInit();
        }
    }
    ```

-   添加`oidcConfig`的bean。

    ``` {#codeblock_4v8_0cx_c93}
    <bean id="oidcConfiguration" class="org.pac4j.oidc.config.OidcConfiguration">
            <property name="clientId" value=your application id />
            <property name="secret" value=your application secret />
            <property name="useNonce" value="false" />
            <property name="scope" value="openid profile aliuid" />
            <property name="clientAuthenticationMethod" value="client_secret_post" />
    </bean>
    ```

-   添加`aliyunOidcClient`的bean。

    ``` {#codeblock_faz_0q7_1sz}
    <bean id="aliyunOidClient" class="org.pac4j.demo.spring.AliyunOidcClient">
            <constructor-arg name="configuration" ref="oidcConfiguration" />
            <property name="authorizationGenerator">
                <bean class="org.pac4j.demo.spring.RoleAdminAuthGenerator" />
            </property>
    </bean>
    ```

-   配置`bean clients`的callbackUrl以及client属性。

    **说明：** 其中callbackUri需要配置在阿里云控制台中应用的回调地址里。

    ``` {#codeblock_uch_8g2_a6e}
    <bean id="clients" class="org.pac4j.core.client.Clients">
            <constructor-arg name="callbackUrl" value="http://127.0.0.1:8080/callback" />
            <constructor-arg name="clients">
                <list>
                    <ref bean="aliyunOidClient" />
                </list>
            </constructor-arg>
    </bean>
    ```

-   添加`oidc`拦截器。

    ``` {#codeblock_7j0_99y_w60}
    <mvc:interceptor>
                <mvc:mapping path="/oidc/*" />
                <bean class="org.pac4j.springframework.web.SecurityInterceptor">
                    <constructor-arg name="config" ref="config" />
                    <constructor-arg name="clients" value="AliyunOidcClient" />
                </bean>
    </mvc:interceptor>
    ```

-   启动示例，访问`http://localhost:8080/oidc/index.html`。

