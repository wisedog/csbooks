안녕하세요, 소프트웨어 개발자 김종하 입니다.

## 왜 이 글을 썼는가

지금 연재하는 글은 "부트캠퍼를 위한 컴퓨터 과학" 입니다. 최근 소프트웨어 개발자 수요가 늘어나서 이를 공급하기 위한 코딩 부트캠프가 많이 생겼습니다. 지금 저와 함께 일하는 동료의 대부분도 부트캠프 출신입니다.

인도 카스트 제도처럼 출신에 따른 차별은 아니지만 4년이라는 긴 세월동안 교수님의 잔소리와 막중한 과제, 엄청난 삽질을 견뎌내며 컴퓨터 공학을 배운 학부생과 몇 달 동안 빠르게 코딩 스킬만 익힌 일반인과는 분명 차이가 존재합니다. 이는 부정할 수 없는 사실입니다. 실제로 컴퓨터 공학 전공자와는 달리 부트캠퍼 주니어 개발자 중에 "localhost:80"와 "localhost:8080"의 차이가 뭔지도 모르는 사람도 봤습니다. 이런 기본적인 지식은 차치하더라도 전공자와 부트캠퍼와 가장 큰 차이는 배우는 속도와 피벗(Pivot)을 했을 경우 적응 시간입니다. 기본이 탄탄하면 피벗(Pivot)이 쉽습니다. 하지만 부트캠퍼 프론트엔드 개발자가 Node.js 말고 Rust 같은 언어를, 웹 말고 다른 분야를 도전할때 기초가 없으면 빠르게 적응하지 못합니다. 이론적 바탕이 없는 스킬은 그저 기예에 가깝습니다.

부트캠퍼 개발자들은 십중 팔구 웹 개발일겁니다. API를 개발하는 백엔드 개발자들은 물론이거니와 프론트엔드 개발도 단순히 리액트, CSS만 할 줄 알면 되는게 아니라 컴퓨터 과학 지식이 기반에 깔려야 좀 더 좋은 개발자들이 되리라 확신합니다. 따라서 저는 이 글을 저희 회사 내 부트캠프 출신 주니어 개발자를 독자로 상정하고 썼습니다. (송성현님, 조형근님 보고 있나요!!!?)

## 후원안내

사실 그냥 쓰다보니 별 보람이 없어서 허탈함이 오는 경우가 많았습니다. 그래서 약간의 보람이라도 느끼고자 광고를 달까 했는데, 굳이 사용자 경험을 해치고 싶지 않았습니다. 만약 글이 읽을만한 가치가 있고 다음 편을 위해 응원을 해주시고 싶으시다면 아래 카카오페이로 QR코드로 커피값 1,000원(더 주셔도 됩니다...) 후원 부탁드리겠습니다.

![후원QR](./kakao_qr.png)

방법은 카카오톡 더보기 메뉴(우측 하단 ...) - 카카오 페이 - 결제 화면 상단의 QR 버튼을 누르시면 됩니다.

## 어떻게 썼는가

이 글은 컴퓨터 공학 전문적인 영역을 깊게 파고드는게 아니라 컴퓨터 교양 수업에 가깝게 쓰도록 노력했습니다. 사실 학부생에 불과한 제가 깊게 써봤자 얼마나 깊게 쓰겠습니까. 다만 컴퓨터 공학 전공자분들은 하찮은 내용이라고 무시하지 마시고 사실이 아닌 부분에 대해서 많이 의견 주시면 감사하겠습니다. 특히 1학년때 배운 디지털 회로같은 과목은 들은지 10년이 훨씬 넘었으니까 틀렸을 수도 있습니다.

또한 이 글은 퇴고와 내용 변경이 수시로 일어나니 이 점 참고하시기 바랍니다.

## 전공자와 비전공자

회사 생활 연차가 두 자리를 넘어가는 동안 수 백명의 개발자를 만나봤습니다. 고등학교 갓 졸업한 사람, 부트캠퍼, 국비학원, 컴퓨터 공학사, 컴퓨터 공학 석사/박사, 문과 전공 개발자 등등. 그 결과 컴퓨터 공학 지식이 좋은 개발자가 되기 위해서 반드시 필요한 조건은 아니라는 사실을 깨달았습니다. 물론 알면 좋습니다. 하지만 일반적인 개발 업무를 처리하는데에는 컴퓨터 공학 지식이 차지하는 영역은 크지 않습니다. 그것보다 커뮤니케이션, 문서화, 도메인 지식, 견고한 코드 짜기 등등 평소 업무에 사용하는 스킬은 극단적으로 말하면 컴퓨터 공학 지식이 없어도 할 수 있습니다.

그러니 비전공자 여러분, 너무 자격지심 가지실 필요 없습니다.

## 전공자의 길

컴퓨터 공학 전공자는 그럼 무엇을 무기로 비전공자들과 싸워야 하느냐라고 반문할 수도 있습니다. 하지만 부트캠퍼가 응용 계층에 주력한다면 공학 전공자는 좀 더 전문적인 부분에서 두각을 나타낼 수 있습니다. 운영 체계, 정적 코드 분석(Static Code Analysis), 컴파일러, 코덱 등 기초 분야가 좋은 예입니다. 저도 몇 년 동안 정적 코드 분석 분야에서 일했습니다. 이 분야는 컴파일러나 프로그래밍 언어론 지식이 필요하며, 특히 컴파일러는 대학교 4년 동안 배운 지식을 총 동원해도 겨우 할까 말까할 부분입니다. 이런 분야는 부트캠퍼 개발자가 일하기 매우 매우 힘들며 사실 학사 출신도 쉽지 않습니다. 이런 분야는 프로그래밍 언어/컴파일러 랩실 출신 석박사들이 주력이죠. (정영범 박사님, 진민식 박사님 사랑합니다)

그 외에도 일반적인 서비스 기업에서도 트래픽이건 데이터건 인프라건 규모가 커지면 공학의 중요성이 커집니다. 데이터가 커지면 알고리즘 복잡도가 n에서 log(n)으로만 가도 엄청난 성능 향상을 기대할 수 있으며 수 많은 트래픽을 받아내기 위해서 스케일 업 작업이라던가 네트워크의 깊숙한 부분까지 만져야 할 수도 있으며 파서를 설계할 일이 생길 수도 있습니다.

이럴때 배워뒀던 컴퓨터 공학이 빛을 발할 수 있습니다.

## 저자

김종하
- 현) 셀러노트 CTO
- email: kim.jongha 지메일
- twitter: @jongha_the_dev

## 주의점

- 순서나 글의 내용은 예정 없이 변경될 수 있습니다.
- 글에 대해 문의점, 오타, 잘못된 내용이 있을 경우 [여기](https://github.com/wisedog/csbooks/issues)에 이슈 제기를 해주시거나 Pull Request를 날려주십시오.

## 저작권

- 이 글의 저작권은 저에게 있습니다.
- 글의 내용을 복제하여 위키, 나무위키, 블로그, 웹사이트 등에 게시할 수 없습니다.
- 링크 및 SNS 공유는 허용합니다.
- 글의 내용을 재가공할 수 없습니다.
- 글의 내용을 상업적으로 사용할 수 없습니다.
- 글의 내용을 어떠한 형태로든 재배포할 수 없습니다.
- 웹 배포는 csbook.wisedog.net 외에는 할 수 없습니다

## Release Note

여기 계신 분들은 버전명이 0. 으로 시작된다는 의미를 아시리라 생각됩니다.
- 0.3
3장 네트워크/인터넷 1차 완성
- 0.2
2장 컴퓨터 구조와 기초 완성
- 0.1
init. 1장 들어가기에 앞서, 2장 컴퓨터 구조와 기초 일부

## Release Candidate

- 0.3.1
DNS 추가(1월 중)
- 0.3.2
라우팅, 클라우드 컴퓨팅 추가(1 ~ 2월 중)