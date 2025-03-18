# 알림 Front 서버 


## 지원자 정보
- 2495-000001_김진희_서버개발자-대고객서비스


## 프로젝트 환경
- Java 17
- Gradle 8.13
- Spring Boot 3.0.4


## 주요 기능
1. **알림 발송 등록 API**
   - **즉시 발송**: 등록 즉시 알림 발송 이벤트 발생  
   - **예약 발송**: 요청받은 시각(yyyyMMddHHmm) 기반 예약 발송 처리  
   - 장애 발생 시, 발송 실패한 알림에 대해 재전송 요청

2. **알림 내역 조회 API**
   - 고객별 최근 3개월간 정상적으로 발송된 알림 내역 조회 (페이징 처리)
   - 빠른 응답을 위해 캐싱(Caffeine) 적용
  
## 디렉토리 구조
```plaintext
com
└── example
    └── notification
        ├── NotificationApplication.java   // 스프링 부트 애플리케이션 진입점
        ├── client                           // 외부 알림 발송 API 연동 (Feign 클라이언트)
        ├── common                           // 공통 예외 및 응답 처리
        ├── config                           // 애플리케이션 설정 (Feign, 캐시, Swagger, 스케줄러, 비동기 등)
        ├── controller                       // 알림 API 엔드포인트 정의
        ├── domain                           // 도메인 관련 클래스 (DTO, Enum 등)
        ├── entity                           // JPA 엔티티 (알림 데이터)
        ├── event                            // 알림 발송 이벤트 및 이벤트 핸들러
        ├── repository                       // 데이터베이스 접근 (JPA Repository)
        ├── scheduler                        // 예약 발송 및 재전송 스케줄러
        └── service                          // 비즈니스 로직 (알림 등록, 조회, 발송 처리)
 ```

## 라이브러리
- Spring Boot 3
- Spring Data JPA
- H2 Database
- Spring Cloud OpenFeign
- Lombok
- Springdoc OpenAPI
- Caffeine
- OkHttp

## API 명세
- http://localhost:8080/swagger-ui/index.html

## Executable jar
- https://github.com/kimjinheeee/20250319_2495-000001/tree/main/build/libs
1. $ ls build.libs
2. $ java -jar notification-front-server.jar
