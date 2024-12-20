
# EC2란?

**Amazon Elastic Compute Cloud (EC2)**는 안전하고 크기 조정이 가능한 컴퓨팅 파워를 클라우드에서 제공하는 웹 서비스입니다.  
개발자가 더 쉽게 인터페이스를 통해 웹 규모의 클라우드 컴퓨팅 작업(용량 확보 및 구성 등)을 수행할 수 있도록 설계되었습니다.  
또한, 검증된 컴퓨팅 리소스에 대한 포괄적인 제어권을 제공합니다.

---

## EC2의 사용 사례

- **서버 구축**: 새로운 서버 환경을 손쉽게 설정 가능
- **어플리케이션 사용 및 호스팅**:  
  - 데이터베이스(DB)  
  - 코인 채굴  
- **고성능 연산 작업**:  
  - 그래픽 렌더링  
  - 게임 개발 및 호스팅  

---

## EC2의 특성

1. **온디맨드 모델**:  
   - 가격이 초 단위로 계산됩니다.  
   - 서비스 요금은 선입금이나 약정 없이 사용한 만큼만 과금됩니다.  

2. **빠른 구축 속도와 확장성**:  
   - 전 세계적으로 분 단위로 수백 대의 인스턴스를 생성 가능  

3. **다양한 구성 타입과 과금 모델 제공**:  
   - 사용자의 요구에 따라 인스턴스 유형 및 요금제를 선택할 수 있습니다.

4. **AWS 서비스와의 연동성**:  
   - EC2는 다른 AWS 서비스와 쉽게 통합 및 연동하여 효율적인 클라우드 환경을 제공합니다.  

---

## EC2의 구성 요소

1. **인스턴스 (Instance)**:  
   - 클라우드에서 사용하는 가상 서버로, CPU, 메모리, 그래픽 카드 등 연산을 위한 하드웨어를 담당합니다.

2. **EBS (Elastic Block Storage)**:  
   - EC2에서 사용하는 가상 하드디스크로, 데이터를 저장하고 관리하는 데 사용됩니다.

3. **AMI (Amazon Machine Image)**:  
   - EC2 인스턴스를 실행하기 위한 정보를 담고 있는 이미지입니다.

4. **보안 그룹 (Security Group)**:  
   - 네트워크 트래픽을 제어하기 위한 가상의 방화벽 역할을 합니다.

---

## 실습 순서

* 목표 : EC2 한대를 프로비저닝 하여 웹 서버 구성하기

0. EC2 - 인스턴스 - 인스턴스 시작 - AMI(Amazon Machine Image) 리스트 확인
1. EC2를 구성하기 위한 AMI 선택 - Amazon Linux 선택 (아마존에서 만든 리눅스)
2. EC2 인스턴스 유형과 사이즈 선택 - vCPU 및 메모리를 설정, 프리티어는 t2.micro를 Default로 사용
3. EBS 세부정보 설정 (스토리지 정보) 
4. 이름 및 태그 설정 - 별칭 등록, Key 값의 처음은 대문자
5. 보안 그룹 설정 - HTTP 규칙 추가
6. 키페어 설정 - 웹서버에 접속하기 위해 필요하며 설정 시 자동으로 *.pem 파일을 다운로드
7. EC2 생성
8. EC2 접속 - 우측 상단의 '연결' - 웹브라우저에서 직접 EC2 인스턴스로 접속(EC2 Connect)
9. EC2 권한 획득 - EC2 인스턴스 명령어 프롬프트에서 `sudo -s` (권한 획득)
10. EC2 내 웹서버 설치 및 웹 서버 실행 - `yum install httpd -y` => `service httpd start` (아파치 웹서버)
11. 웹 브라우저에서 접속 테스트 - public ip 주소를 새창에서 접속해보기
12. 웹서버 첫 페이지 내용을 변경 (index.html 변경) - `nano /var/www/html/index.html`
13. 인스턴스로 돌아가 만들어진 EC2를 종료하기 - 삭제가 아닌 정지 시 하드디스크 요금이 발생, 프리티어는 요금제는 실행 기준 하루에서 이틀정도만 커버 가능
