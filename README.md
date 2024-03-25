# Cross-origin resource sharing(CORS) implementation Spring boot 3.2.4
This application is build on Spring Boot 3.2.4
1. In the configuration class create CorsConfigurationSource bean
     
        @Bean
        CorsConfigurationSource corsConfigurationSource(){
          CorsConfiguration corsConfiguration = new CorsConfiguration();
          corsConfiguration.setAllowedOrigins(Arrays.asList("http://localhost:4200"));
          corsConfiguration.setAllowedMethods(Arrays.asList("GET","POST","PUT","PATCH","DELETE","OPTIONS"));
     
          UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
          source.registerCorsConfiguration("/**",corsConfiguration);
          return source;
        }
2. Disabling cors


       @Bean
         SecurityFilterChain defaultSecurityFilterChain(HttpSecurity httpSecurity) throws Exception {
            httpSecurity/*.cors(cors -> cors.disable())*/
                        .csrf(csrf -> csrf.disable())
            .authorizeHttpRequests(auth -> auth
               .requestMatchers("/api/v1/notice",
                      "/api/v1/contact",
                     "/api/v1/register")
                     .permitAll()
               .requestMatchers("/api/v1/myAccount",
                      "/api/v1/myCards",
                        "/api/v1/myBalance",
                        "/api/v1/myLoans")
               .authenticated()
            )
            .httpBasic(withDefaults());
            return httpSecurity.build();
         }

https://www.linkedin.com/in/tatekahmed/   
    
