# RESTful API 설계

## REST(Representational State Transfer) 원칙

1. **자원 기반 설계**: URI(Uniform Resource Identifier)로 자원을 식별
2. **표현을 통한 상호작용**: 자원을 JSON, XML 등의 형태로 전송
3. **상태 없는 통신**: 요청은 클라이언트의 상태를 서버에 저장하지 않고 독립적으로 처리
4. **표준 HTTP 메서드 사용**: CRUD 작업을 GET, POST, PUT, DELETE 등의 메서드로 수행
5. **캐시 가능**: 응답은 캐시 가능해야 하며 성능 향상
6. **계층화 시스템**: 클라이언트는 중간 레이어를 통해 서버와 통신
7. **일관된 인터페이스**: API는 일관성 있게 설계되어야 함

## RESTful API

- **정의**: REST API 설계 규칙을 준수하는 시스템을 RESTful하다고 함.
- **목표**: 이해하기 쉽고 사용하기 쉬운 API를 제공하는 것.

## RESTful API 설계 규칙

1. **리소스 중심의 URI**
   - URI는 명사 형태로 리소스를 식별
     - 예: `/users`, `/users/{userId}`

2. **HTTP 메서드 사용**
   - **GET**: 조회
   - **POST**: 생성
   - **PUT**: 전체 업데이트
   - **PATCH**: 부분 업데이트
   - **DELETE**: 삭제

3. **일관된 인터페이스**
   - 모든 엔드포인트는 일관되게 설계

4. **상태 코드 사용**
   - 적절한 HTTP 상태 코드를 사용하여 요청 결과를 전달
     - 예: `200 OK`, `201 Created`, `204 No Content`, `400 Bad Request`, `404 Not Found`

5. **무상태성 (Statelessness)**
   - 서버는 클라이언트의 상태를 저장하지 않음

6. **캐시 가능성 (Cacheability)**
   - 응답은 캐시 가능해야 함

7. **계층화 시스템 (Layered System)**
   - 중간 계층(프록시 등)을 통해 확장성과 보안 강화

8. **코드 온 디맨드 (선택 사항)**
   - 서버가 클라이언트에 실행 가능한 코드 제공 가능

### 추가 고려 사항

- **버전 관리**: API의 버전을 관리하여 변경 사항을 제어
- **보안**: HTTPS 및 인증 메커니즘 구현
- **문서화**: API 문서화 (예: Swagger, OpenAPI)
