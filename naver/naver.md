###마크업 구조
1. 아이디 입력/비밀번호 입력/로그인 버튼을 form으로 묶어줌
2. 로그인 상태유지 체크박스와 IP보안 링크 및 스위치는 ul로 묶어줌


###스타일링
#로그인 상태유지 체크박스와 IP보안 링크 및 스위치
- flex 사용하여 가로로 배치
- flex-flow: row nowrap;
  justify-content: space-between; 
  -> IP 보안 관련 요소 오른쪽 정렬

#IP 보안 ON/OFF
1. 기본 라벨이 'OFF'인 체크박스 삽입
2. 가상선택자(::before) 이용하여 checked 된 경우 'ON' 삽입 -> 이때 'OFF'는 font-size를 0으로 함


###보완 사항
1. 데스크탑 스타일 구현
2. focus 될 때 아웃라인 사이즈 맞지 않는 요소 수정
3. svg 파일 png로 export 하여 svg 지원하지 않는 브라우저에서 png형식으로 보여지도록 구현