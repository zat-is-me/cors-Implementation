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


https://www.linkedin.com/in/tatekahmed/   
    
