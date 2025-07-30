# 🌐 API Gateway - PokeMicroServicios

Este proyecto es el **API Gateway** de la arquitectura de microservicios de la 🐱‍👤 PokeAPI personal.  
Construido con **Spring Cloud Gateway**, se encarga de:

- 🔀 Redirigir el tráfico a los microservicios registrados en **Eureka**.
- 📄 Exponer una **documentación Swagger centralizada**.
- 🎯 Controlar las rutas de acceso mediante predicados (`Path`).

---

## 🚀 Tecnologías

| Herramienta             | Descripción                             |
|-------------------------|-----------------------------------------|
| 🧰 Spring Boot 2.7.18    | Framework principal                     |
| 🌉 Spring Cloud Gateway | Redirección y filtrado de rutas         |
| 🧭 Eureka Client        | Registro automático en Discovery Server |
| 📘 Swagger UI (springdoc-openapi) | Documentación centralizada de APIs |

---

## 🗺️ Estructura de rutas

Las rutas están definidas en `application.yml` usando el `lb://` para balanceo vía Eureka:

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: pokemon-service
          uri: lb://pokemon-service
          predicates:
            - Path=/api/pokemon/**, /pokemon/**, /pokemon/v3/api-docs, /pokemon/swagger-ui.html, /pokemon/swagger-ui/**
```

Swagger centraliza todo con:
```yaml
springdoc:
  swagger-ui:
    urls:
      - name: pokemon-service
        url: /pokemon/v3/api-docs
```
## 🧪 Cómo levantarlo
1. Asegúrate de que discovery-service y pokemon-service están arriba.
2. Corre este proyecto:
   ```yaml
   ./mvnw spring-boot:run
   ```

