# Deno

## Deno란

> V8을 사용하고 Rust로 구축된 JavaScript, TypeScript 및 WebAssembly를 위한 간단하고 현대적이며 안전한 런타임



## Node.js와 비교

* NPM 불용, URL 또는 파일 경로로 참조되는 모듈을 사용

* Package.json 모듈 확인 알고리즘 불용

* 모든 비동기 작업은 Promise 반환. 따라서 Deno는 Node.js와 다른 API 제공

* 파일, 네트워크 및 환경 액세스에 대한 명시적 권한 필요

* 예상할 수 없는 에러 발생시 항상 죽음

* ES Modules을 사용하여 require() 미지원, 서드 파티 모듈들은 Import 사용

  * ```typescript
    import * as log from "https://deno.land/std@0.154.0/log/mod.ts";
    ```

|                    | Node.js                        | Deno                        |
| ------------------ | ------------------------------ | --------------------------- |
| Base Language      | C++, JavaScript                | Rust, TypeScript            |
| Language           | JavaScript                     | JavaScript, TypeScript      |
| Package Manager    | NPM                            | URL (.ts/.js modules)       |
| importing Package  | CommonJS                       | ES Modules                  |
| Async              | CallBacks(no plans to upgrade) | Promises(modern ECMAScript) |
| Security           | Full Access                    | Permissioned Access         |
| TypeScript Support | Not Built In                   | Built In                    |
| Upgrade            | Installer                      | Command                     |



## 보안

Node.js는 파일 시스템, 외부로 나가는 요청, 환경변수 등에 제한 없이 접근할 수 있다. 이런 방식은 편하지만 개발 환경이나 운영 중인 환경에서 심각한 보안 문제를 초래할 수도 있다는 단점이 존재한다.

* --alow-net 옵션을 사용해야 네트워크를 사용할 수 있다.
* 권한을 허용/제한할 때 커맨드라인 옵션을 사용한다.
* 예외를 적용하면 폴더에서 코드를 읽을 수 있다.
* 커맨드라인에서 스크립트 파일을 실행할 때 권한을 허용하려면 플래그를 사용해야 한다.

## 패키지 관리

Node.js는 NPM으로 패키지를 관리했지만 Deno는 패키지를 설치하거나 외부 링크로 패키지를 로드할 떄 모두 URL을 사용한다. 그렇기 대문에 packae.json 파일이 없으며 node_modules 폴더 또한 존재하지 않는다.

아무 곳에서나 모듈을 로드해 사용할 수 있지만 취약점이 확인되지 않은 서드 파티 모듈을 사용할 때에도 제한이 없다.