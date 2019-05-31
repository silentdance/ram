# OAuth 常用的 SDK 示例 {#concept_264755 .concept}

本文基于 Spring Boot OAuth2 和 Pac4J，为您介绍 OAuth 常用的 SDK 示例的相关配置。

## Spring Boot OAuth2 示例 {#section_pwc_2kd_832 .section}

参考 [Spring Boot and OAuth2](https://spring.io/guides/tutorials/spring-boot-oauth2/)文档及示例，主要做以下两点修改：

-   配置文件改为阿里云对应的配置。

    ``` {#codeblock_upr_q4h_86e}
    alibabacloud:
        client:
          clientId: 4151950823846923577
          clientSecret: 6EwN4qutnZuchG6n677Ie33SsjAhwyTpcOMSoIo6v0gqJtw4QcHhERVXfqzcWgMB
          accessTokenUri: https://oauth.alibabacloud.com/v1/token
          userAuthorizationUri: https://signin.alibabacloud.com/oauth2/v1/auth
          tokenName: access_token
          authenticationScheme: query
          clientAuthenticationScheme: form
        resource:
          userInfoUri: https://oauth.alibabacloud.com/v1/userinfo
    ```

-   修改重定向 URI。

    修改`OAuth2ClientAuthenticationProcessingFilter`中的回调地址，改成与应用中的配置相同。 例如：应用配置的是`http://localhost:8080/login/alibabacloud`，则把代码中的回调地址替换为`/login/alibabacloud`。

    整体示例代码如下：

    ``` {#codeblock_gc5_cw3_595}
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
        OAuth2ClientAuthenticationProcessingFilter alibabacloudFilter= new OAuth2ClientAuthenticationProcessingFilter(
            "/login/alibabacloud");
        OAuth2RestTemplate alibabacloudTemplate = new OAuth2RestTemplate(alibabacloud(), oauth2ClientContext);
        alibabacloudFilter.setRestTemplate(alibabacloudTemplate);
        UserInfoTokenServices tokenServices = new UserInfoTokenServices(alibabacloudResource().getUserInfoUri(),
            alibabacloud().getClientId());
        tokenServices.setRestTemplate(alibabacloudTemplate);
        alibabacloudFilter.setTokenServices(tokenServices);
        return alibabacloudFilter;
      }
    
      @Bean
      @ConfigurationProperties("alibabacloud.client")
      public AuthorizationCodeResourceDetails alibabacloud() {
        return new AuthorizationCodeResourceDetails();
      }
    
      @Bean
      @ConfigurationProperties("alibabacloud.resource")
      public ResourceServerProperties alibabacloudResource() {
        return new ResourceServerProperties();
      }
    
    }
    ```


## Pac4J 示例 {#section_12k_zev_o29 .section}

参考 [Pac4J](http://www.pac4j.org/) 的 spring-webmvc-pac4j 示例，进行以下操作：

-   创建`AlibabaCloudOidcClient`。

    ``` {#codeblock_big_0e9_gyv}
    public class AlibabaCloudOidcClient extends OidcClient<OidcProfile, OidcConfiguration> {
        public AlibabaCloudOidcClient() {
    
        }
    
        public AlibabaCloudOidcClient(OidcConfiguration configuration) {
            super(configuration);
        }
    
        @Override
        protected void clientInit() {
            CommonHelper.assertNotNull("configuration", this.getConfiguration());
            this.getConfiguration().defaultDiscoveryURI("https://oauth.alibabacloud.com/.well-known/openid-configuration");
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

-   添加`AlibabaCloudOidcClient`的 bean。

    ``` {#codeblock_c62_xcw_ovn}
    <bean id="AlibabaCloudOidClient" class="org.pac4j.demo.spring.AlibabaCloudOidcClient">
            <constructor-arg name="configuration" ref="oidcConfiguration" />
            <property name="authorizationGenerator">
                <bean class="org.pac4j.demo.spring.RoleAdminAuthGenerator" />
            </property>
    </bean>
    ```

-   配置`bean clients`的 callbackUrl 以及 client 属性。

    **说明：** 其中 callbackUri 需要配置在阿里云控制台中应用的回调地址里。

    ``` {#codeblock_tps_okr_ske}
    <bean id="clients" class="org.pac4j.core.client.Clients">
            <constructor-arg name="callbackUrl" value="http://127.0.0.1:8080/callback" />
            <constructor-arg name="clients">
                <list>
                    <ref bean="AlibabaCloudOidClient" />
                </list>
            </constructor-arg>
    </bean>
    ```

-   添加`oidc`拦截器。

    ``` {#codeblock_b6f_efg_i51}
    <mvc:interceptor>
                <mvc:mapping path="/oidc/*" />
                <bean class="org.pac4j.springframework.web.SecurityInterceptor">
                    <constructor-arg name="config" ref="config" />
                    <constructor-arg name="clients" value="AlibabaCloudOidcClient" />
                </bean>
    </mvc:interceptor>
    ```

-   启动示例，访问`http://localhost:8080/oidc/index.html`。

