# Configurations for OAuth SDKs {#concept_264755 .concept}

This topic describes the related configurations of some commonly used SDKs of OAuth by providing configuration examples of Spring Boot with OAuth2 and Spring Boot with Pac4J.

## Spring Boot and OAuth2 configuration example {#section_pwc_2kd_832 .section}

To configure the OAuth SDK by modifying the configurations of [Spring Boot and OAuth2](https://spring.io/guides/tutorials/spring-boot-oauth2/), follow these steps:

-   Enter the Alibaba Cloud configuration information in the configuration file.

    ``` {#codeblock_u90_8hq_qgs}
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

-   Modify the redirection URL.

    Replace the callback URL in `OAuth2ClientAuthenticationProcessingFilter` with the URL of the target application. For example, if `http://localhost:8080/login/alibabacloud` is configured for the application, you can replace the callback URL with `/login/alibabacloud`.

    The following is a code example:

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


## Pac4J configuration example {#section_12k_zev_o29 .section}

To configure the OAuth SDK by modifying the configurations of the `spring-webmvc-pac4j` project in [Pac4J](http://www.pac4j.org/), follow these steps:

-   Create an `AlibabaCloudOidcClient` client.

    ``` {#codeblock_gru_1yf_rc4}
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

-   Add the bean configuration to `oidcConfig`.

    ``` {#codeblock_4v8_0cx_c93}
    <bean id="oidcConfiguration" class="org.pac4j.oidc.config.OidcConfiguration">
            <property name="clientId" value=your application id />
            <property name="secret" value=your application secret />
            <property name="useNonce" value="false" />
            <property name="scope" value="openid profile aliuid" />
            <property name="clientAuthenticationMethod" value="client_secret_post" />
    </bean>
    ```

-   Add the bean configuration to `AlibabaCloudOidcClient`.

    ``` {#codeblock_faz_0q7_1sz}
    <bean id="AlibabaCloudOidClient" class="org.pac4j.demo.spring.AlibabaCloudOidcClient">
            <constructor-arg name="configuration" ref="oidcConfiguration" />
            <property name="authorizationGenerator">
                <bean class="org.pac4j.demo.spring.RoleAdminAuthGenerator" />
            </property>
    </bean>
    ```

-   Configure the callbackUrl and client attributes of `bean clients`.

    **Note:** You must configure the callbackUri attribute in the **Callback URL** field in the Alibaba Cloud console.

    ``` {#codeblock_uch_8g2_a6e}
    <bean id="clients" class="org.pac4j.core.client.Clients">
            <constructor-arg name="callbackUrl" value="http://127.0.0.1:8080/callback" />
            <constructor-arg name="clients">
                <list>
                    <ref bean="AlibabaCloudOidClient" />
                </list>
            </constructor-arg>
    </bean>
    ```

-   Add the `oidc` interceptor.

    ``` {#codeblock_7j0_99y_w60}
    <mvc:interceptor>
                <mvc:mapping path="/oidc/*" />
                <bean class="org.pac4j.springframework.web.SecurityInterceptor">
                    <constructor-arg name="config" ref="config" />
                    <constructor-arg name="clients" value="AlibabaCloudOidcClient" />
                </bean>
    </mvc:interceptor>
    ```

-   Access `http://localhost:8080/oidc/index.html`.

