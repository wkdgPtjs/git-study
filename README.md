# git-study
- GitHub Actions을 사용해서 파이썬 3.8 ~ 3.10 버전 별로 출력 결과를 저장
- upload-artifact을 사용해서 출력된 결과물을 아티팩트로 저장


###Github actions
- 자동으로 repository에 어떤 이벤트가 발생하면 특정 작업이 발생하게 하거나 주기적으로 원하는 작업을 반복 실행할 수 있음.
- 반복 작업(CI/CD) 자동화
- 하나의 코드 저장소 범위 내 

<h3>Workflows</h3>
- 가장 상위 개념
- 자동화 해놓은 작업 과정
- ./github/workflows
- 해당 폴더 하위에 있는 YAML 파일로 설정
- 하나의 레포지토리에 여러개의 워크플로우 생성 가능

<h3>YAML</h3>
- on : 언제 이 워크플로우가 실행되는 지 정의하는 것
- jobs : 워크플로우가 어떤 작업을 해야하는 지 작성
- steps : 여러 작업(jobs)를 단계(steps)으로 모델링
- run : command나 script 실행 시 사용
- uses : actions 사용 시
