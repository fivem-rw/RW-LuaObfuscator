```diff
- 해당 API는 테스트 버전 입니다. Production 버전에서 이용하지 마십시오.
- 해당 API는 테스트 단계이므로 API서버에 접속이 원활하지 않을 수 있습니다.
```

## 소개

RW-LuaObfuscator API는 강력한 LUA 난독화 도구 입니다.<br>
- [lua-sdk](https://github.com/fivem-realw/RW-LuaObfuscator/tree/main/lua)
- [node-sdk](https://github.com/fivem-realw/RW-LuaObfuscator/tree/main/node)
<br><br>
## API 엔드포인트

```
https://api.realw.kr/obfuscate/v1
```

### 사용자 인증
API 호출시 `리얼월드`로 부터 발급받은 `API Key` 를 `X-API-Credential` 헤더로 전송해야 합니다.<br>
해당 헤더가 존재하지 않거나 올바르지 않은 `API Key` 가 전송되면 API 호출이 서버 대기열에서 삭제됩니다.

### 요청 빈도 제한
API 호출은 IP별 분당 100회로 제한됩니다. 더 많은 빈도 제한을 원하면 `discord.gg/realw` 로 문의 바랍니다.

### HTTP 반환 코드
- HTTP 4XX 반환 코드는 잘못된 요청에 사용됩니다. 문제는 호출자 측에 있습니다.
- HTTP 403 반환 코드는 WAF 제한(웹 응용 프로그램 방화벽)을 위반했을 때 사용됩니다.
- HTTP 429 반환 코드는 요청 속도 제한을 위반할 때 사용됩니다.
- HTTP 418 반환 코드는 코드를 받은 후 요청을 계속 보내기 위해 IP가 자동 금지되었을 때 사용됩니다.
- HTTP 5XX 반환 코드는 내부 오류에 사용됩니다. 문제는 API 서버측입니다.
<br>

## API 목록

- 모든 API 호출에는 `X-API-Credential` 헤더가 포함되어야 합니다.

### 난독화
```
POST /new
```

- 매개변수
<table>
  <thead>
    <tr>
      <td>매개변수 명</td>
      <td>매개변수 타입</td>
      <td>필수값</td>
      <td>설명</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>fileName</td>
      <td>STRING</td>
      <td>예</td>
      <td></td>
    </tr>
    <tr>
      <td>script</td>
      <td>STRING</td>
      <td>예</td>
      <td></td>
    </tr>
    <tr>
      <td>options</td>
      <td>OBJECT</td>
      <td>아니요</td>
      <td></td>
    </tr>
  </tbody>
</table>

### 난독화 진행 정보
```
GET /status
```

- 매개변수
<table>
  <thead>
    <tr>
      <td>매개변수 명</td>
      <td>매개변수 타입</td>
      <td>필수값</td>
      <td>설명</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>id</td>
      <td>STRING</td>
      <td>예</td>
      <td></td>
    </tr>
  </tbody>
</table>

### 난독화 파일 다운로드
```
GET /download/{id}
```

- 매개변수
<table>
  <thead>
    <tr>
      <td>매개변수 명</td>
      <td>매개변수 타입</td>
      <td>필수값</td>
      <td>설명</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>format</td>
      <td>STRING</td>
      <td>아니요</td>
      <td>출력할 포맷을 지정합니다. text, file (기본값: file)</td>
    </tr>
  </tbody>
</table>