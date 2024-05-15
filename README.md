# Spring_SpriingSecurity2

![Capture](https://github.com/SDguyleroc/Spring_SpriingSecurity2/assets/126127721/7de74207-1459-41a6-9a5e-828998807cff)


## what about Spring Security

* Provides J2EE (now called jakrta EE application space) application security services
* Designed for enterprise applications and internet-facing applications
  * can be used with traditional Spring-based WAR aplications or raw java applications
* Provides the authentication (who) and authorization (what)

## Understanding Authentication and Authorization

#### Authentication
* process of veryfying a principal ( determining that a principle is who they say they are)
* Principals can be humans or machines

#### Authentication Support
- HTTP basic and digest, x509, and form-based authentication
- LDAP and Active Directory
- OpenID, Jasig CAS ( Central Authentication Service), and JAAS
- OAuth and Oauth 2
- Kerberos and SAML

#### Authorization (AthZ 
- Determines what the principal can or cannot do
- Authorization is based on authenciation
- Authorization is often called access control

#### Authorization Support

- Web request based authorizations
- method invocation
- Domain object access control

## Project Introduction

#### model/Customer

![model-customer](https://github.com/SDguyleroc/Spring_SpriingSecurity2/assets/126127721/8bcec304-4a5c-4a0b-ba9b-97434d6a4a60)

#### model/order

![model-order](https://github.com/SDguyleroc/Spring_SpriingSecurity2/assets/126127721/a4c171c9-699d-4b2f-ab97-fb4ef5058e08)

Schema.sql

![schema](https://github.com/SDguyleroc/Spring_SpriingSecurity2/assets/126127721/b89085cc-8171-41cb-9f60-ec74f38f5066)

## Impementing In-Memory Basic Authentication
##### non of this should be used in the real world it just to show how easy basic spring security is



* in our base java package creat a new package called config
* in the config package creat a new java class called WebSecurityConfig
* Annotate it with @Configuration and @EnableWebSecurity
* Then extend WebSecurityConfigurerAdapter
* Overide a method configure(HttpSecurity http) throws Exception
* create another method and annotate with bean and overrride and is the UserDetailedService we will call it userDetailedService
```java
@Configuration
@EnableWebSecurity
public class WebSecurityConfig extends WebSecurityConfigurerAdapter {

@Override
protected void configure(HttpSecurity http) throws Exception{

      http.authorizeRequests().antmatchers("/", "/home").permitAll().anyRequest().authenticated().and().httpBasic();

}

@Bean
@Override
public UserDetailsService userDetailsService(){
                      // only for testing purposes
    UserDetails user = User.withDefaultPasswordEcnoder()Username("user).password("password").roles("User").build();

    return new InmemoryUserdetailsManager(user)


}


}
  
  ```



















