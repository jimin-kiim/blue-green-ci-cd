## Blue Green CI/CD

### 0. 무중단 배포 전략의 종류
   Zero-downtime deployment, 무중단 배포는 배포 시 서비스 중단 없이 어플리케이션을 업데이트해 서비스의 가용성을 높이는 배포 방식으로 크게 세 가지 전략이 있다; Blue/Gree, Rolling, Canary.
   
 - #### Blue/Green Deployment:
   현재 사용자가 접속 중인 운영 환경을 Blue, 새롭게 배포되는 버전으로 전환 대기 중인 운영 환경을 Green으로 칭해 독립된 두 환경을 운영하면서 트래픽을 Blue에서 Green으로 전환해 서비스 중단 없이 배포하는 방식이다.  
 - #### Rolling Deployment
   일정 수 이상의 인스턴스를 서비스 상태로 유지하면서 기존의 인스턴스들을 점진적으로 새 인스턴스로 교체해 배포하는 방식이다.
 - #### Canary Deployment
   서비스 상태인 인스턴스에 배포할 새 인스턴스를 추가하여 새 인스턴스로의 트래픽의 비율을 점진적으로 증가시켜가며 배포하는 방식이다.


</br>

### 1. Blue/Green 배포

   그 중 Blue/Green Deployment는 현재 사용자가 접속하는 운영 환경과 새로 배포할 운영 환경을 운영하면서 트래픽을 현재 서비스 운영 환경에서 배포할 운영 환경으로 전환하여 무중단 배포를 수행하는 방식이다.
   
   1. Blue 운영 중
   2. Green 추가 운영 및 트래픽 대기
   3. Blue에서 Green으로의 트래픽 전환
   4. Blue 운영 종료 혹은 대기.
     * 전환 후 문제 발생 시 Blue로 즉시 롤백
       
  위 순서로 진행되며 아래와 같은 장점을 갖는다. 
  
   - 트래픽 전환 방식이라는 단순한 방법으로 구현 가능, 배포 흐름이 명확하여 자동화에 용이.
   - 즉시 복구 가능
   - 두 환경은 서로 독립된 환경으로 분리된 상태에서 배포 및 테스트 수행이 가능하다.

  ### 테스트 결과 
  |2차 배포 - green|<img width="1800" height="1169" alt="스크린샷 2025-11-25 오후 3 51 39" src="https://github.com/user-attachments/assets/2ecf3061-6eb4-46ed-bef3-86f29ec87adb" />|
|------|---|
|3차 배포 - blue|<img width="1800" height="1169" alt="스크린샷 2025-11-25 오후 3 52 06" src="https://github.com/user-attachments/assets/c1e46829-e18d-4825-a402-774eb2541992" />|
  
