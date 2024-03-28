<h1>SpringBoot Mybatis Setting</h1>
<h3>1. Gradle 추가하기</h3>
알맞은 DB 관련 Gradle도 추가하기 <br><br>

```
testImplementation 'org.mybatis.spring.boot:mybatis-spring-boot-starter-test:3.0.3'
runtimeOnly 'org.mariadb.jdbc:mariadb-java-client'
```

<h3>2. application.properties Setting </h3>
maria DB 사용해서 mariaDB 관련 세팅임

```
spring.jpa.hibernate.ddl-auto=update
spring.datasource.driverClassName=org.mariadb.jdbc.Driver
spring.datasource.url=jdbc:mariadb://서버주소:3306/데이터베이스
spring.datasource.username=사용자명
spring.datasource.password=비밀번호
mybatis.type-aliases-package= DTO위치(파라미터나 리턴타입으로 쉽게 사용하기 위함)
mybatis.mapper-locations= classpath:/mapper/**/*.xml (mapper 위치)
```


<h3>3. mapper 생성하기</h3>
/resources/mapper 폴더 생성후 mapper.xml 파일 만들기

```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">


<mapper namespace="mapper 정보가진 java 위치(ex :: com.drolong.drolong.mapper.LoginMapper)">


</mapper>
```
