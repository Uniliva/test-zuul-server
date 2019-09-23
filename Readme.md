02 - Spring Cloud Zuul

#### O que é

![0d9a24f369e164366aa919b6bda24a34.png](_resources/363f3d474f91479894453b32b849b15b.png)
![5405c175e12959a52ca0acfb76e1d463.png](_resources/cdd123fe995a482b91eef3f030deb4dc.png)
![aabc558b9c43c6139b389cae40f8cbb3.png](_resources/fa06d7ab4c4b431ca46fd22af1d0403f.png)

#### Spring Cloud Zuul

- Padrão para a utilização de micro serviços
- Load balancing no lado do servidor
- roteamento dinamico
- Facilidade para geração de logs de acesso
- Totalmente integrado com o Eureka


#### Criando um projeto com Spring Cloud Zuul

1. **Baixe um projeto do https://start.spring.io/**

![3459f2e7f64b9dcc5014fe9788e0a74d.png](_resources/dbcc5ac1dded4d79a9caca83ba9fd774.png)

ou adicione no pom 

```xml
<dependencies>
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.cloud</groupId>
			<artifactId>spring-cloud-starter-netflix-zuul</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<dependencyManagement>
		<dependencies>
			<dependency>
				<groupId>org.springframework.cloud</groupId>
				<artifactId>spring-cloud-dependencies</artifactId>
				<version>${spring-cloud.version}</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
		</dependencies>
	</dependencyManagement>
```


2.  importe com o eclipse
3. Adicione a anotação na classe de aplicação

```java
@EnableZuulProxy
@EnableEurekaClient
@SpringBootApplication
public class ZuulServerApplication {
	public static void main(String[] args) {
		SpringApplication.run(ZuulServerApplication.class, args);
	}
}
```



![b05423fed23325fca4b3107866e80520.png](_resources/130f8240a0c84a5784cd45eae0123b54.png)


4. add as propriedades no arquivo `application.yml`

```
spring:
  application:
    name: zuul
  
eureka:
  client:
    serviceUrl:
      defaultZone: ${EUREKA_URI:http://localhost:8761/eureka}
```

![f1d94cc30268b63d6a62572b6a7c9911.png](_resources/c3ff36fc6ed04bcca79034b8e67c26c3.png)



























