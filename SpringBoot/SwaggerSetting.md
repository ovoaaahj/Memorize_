<h1>Swagger Setting 정리</h1> <br>

gradle 에 관련 항목 추가하기
```
implementation 'org.springdoc:springdoc-openapi-starter-webmvc-ui:2.0.2'
```

SwaggerConfig 파일 생성하기
```
@OpenAPIDefinition(
        info = @Info(title = "드로롱 서비스 API 명세서",
                description = "드로롱 서비스 API 명세서",
                version = "v1"))
@Configuration
public class SwaggerConfig {

    //jwt 기능 활성화 
    @Bean
    public OpenAPI openAPI(){
        SecurityScheme securityScheme = new SecurityScheme()
                .type(SecurityScheme.Type.HTTP).scheme("bearer").bearerFormat("JWT")
                .in(SecurityScheme.In.HEADER).name("Authorization");
        SecurityRequirement securityRequirement = new SecurityRequirement().addList("bearerAuth");

        return new OpenAPI()
                .components(new Components().addSecuritySchemes("bearerAuth", securityScheme))
                .security(Arrays.asList(securityRequirement));
    }

}
```

JWT 기능은 추후에 더 알아보고 내용 추가하기
