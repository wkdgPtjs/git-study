# git-study
- GitHub Actions을 사용해서 파이썬 3.8 ~ 3.10 버전 별로 출력 결과를 저장
- upload-artifact을 사용해서 출력된 결과물을 아티팩트로 저장

### Github actions
+ 자동으로 repository에 어떤 이벤트가 발생하면 특정 작업이 발생하게 하거나 주기적으로 원하는 작업을 반복 실행할 수 있음.
+ 반복 작업(CI/CD) 자동화
+ 하나의 코드 저장소 범위 내

### Workflows
- 가장 상위 개념
- 자동화 해놓은 작업 과정
- ./github/workflows
- 해당 폴더 하위에 있는 YAML 파일로 설정
- 하나의 레포지토리에 여러개의 워크플로우 생성 가능

### YAML
- on : 언제 이 워크플로우가 실행되는 지 정의하는 것
- jobs : 워크플로우가 어떤 작업을 해야하는 지 작성
- steps : 작업의 실행 단계 정의
  - 여러 작업(jobs)를 단계(steps)으로 모델링
- run : command나 script 실행 시 사용
- uses : actions 사용 시

----
### 코드 리뷰
- 총 3개의 작업이 있지만 동일 작업이기 때문에 하나의 작업만 설명
  
<pre><code>
  {
  name: Python

on: workflow_dispatch //수동 실행 

jobs: //수행 작업 정의
  build1:
    runs-on: ubuntu-latest //작업이 ubuntu 환경에서 실행됨을 지정
    strategy: //python 버전에 대한 matrix 값 사용
      matrix:
        python-version: ["3.8"]

    steps: //실행 단계 정의
      - uses: actions/checkout@v3 //현재 레포 체크아웃
      - name: Set up Python ${{ matrix.python-version }} //사용할 파이썬 버전 설정
        uses: actions/setup-python@v4 
        with:
          python-version: ${{ matrix.python-version }}
      - name: Display Python version
        //파이썬 명령어로 버전 확인하고 결과 파일에 저장
        run: python -c "import sys; print(sys.version)" > git_study1.txt
      - name: git 
        uses: actions/upload-artifact@v1 //artifact로 업로드
        with:
          name: python3.8
          path: git_study1.txt
  }
</code></pre>

### 결과
- workflows를 실행하면 아래와 같이 빌드가 되고 결과물이 파일로 저장된다.
![image](https://github.com/wkdgPtjs/git-study/assets/138555078/a7379c83-903e-4ee2-8008-75d12d7f6803)
![image](https://github.com/wkdgPtjs/git-study/assets/138555078/cd7544f2-bf0a-4bb0-a515-e8c09ae34f62)

- 파일 내용

![image](https://github.com/wkdgPtjs/git-study/assets/138555078/5dfb4ed7-5984-45fe-b85f-a338f49de788)

