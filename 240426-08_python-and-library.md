- 추후 수정 추가 예정
  
# 240426-08_python-and-library.md
> [한 번에 따라하는 파이썬 데이터 분석 기초 완주반 - Selena]의 내용을 학습, 수정, 추가 하였음. 아는 내용이 많을 땐 학습보다 정리에 가까움

## 1 파이썬 기본 복습
- 변수 이름 규칙
  + [영문자] 혹은 [_]로 시작 / [숫자] 시작 불가

- 순서 자료형 : number, string, list, tuple
- 비순서 자료형 : dictionary, set, (bool) 


- 문자열에서 \ : \ 바로 뒤에 오는 엔터를 줄바꿈으로 작용 안하게함 

- 문자열 예시
  + "%d" % 30   #  2개 : % (30,20)
    > sentence = "나는 %d호선을 타고 다녀." % 6 #  2개 : % (30,20)

  + "{0}".format(7)
    > print("나는 {2}{1}{0}호선을 타고 다녀.".format(6,7,8))

- 문자열 관련 함수
  > .split() : 문자열 나누기  
    .count('샤브') : 문자 개수 세기    
    .replace('a', 'b') : 문자열 바꾸기
    .upper() : 소문자를 대문자로 바꾸기  
    .lower() : 대문자를 소문자로 바꾸기
  
  + .find('a') : "위치" 알려주기  
  + 'a'.join(x) : 문자열 삽입    


- 리스트 관련 함수
  > .reverse() : 리스트 뒤집기
  > .extend(X) : 리스트 확장
  > .pop(i) : i번째 리스트 요소 끄집어내기
  > .count(x) : 리스트에 포함된 요소 x의 개수 세기
  
  + .insert(a, b) : 리스트 요소 삽입, 리스트 a번째 위치에 b를 삽입
  + .remove(x) : 리스트 요소 앞부터 **한 개** 제거
    
- 튜플 
  > tup1=1,2,3  # 초기화 생성 때 괄호 기호 생략 가능 

  + 추가, 삭제, 수정 불가 (에러)
    + 경유하여 추가 가능 : tup1 = tup1 + (4,)   
       ( 두 튜플을 합친 것을 새로운 변수에 할당 ) 
  + 1개의 요소를 가질 시 ',' 안하면 숫자로 인식함 : (4,)

- 딕셔너리 
  + 키 : 부울, 숫자, 문자열 등
  + 함수  
    > 문법 창고에 개인 필기해뒀던 거라 형식 좀 다름 

    + ```
    >> 1긴 딕셔너리 생성 : [dict(zip())]
    : 1) target=dict(zip( key_list, value_list))
        + list로 입력 줄 때, [0 ]*k 하면 값 동기화 되는지 체크 

    : 2) value를 같은 값으로 만들어줄 때 * value를 
      + dict1=dict1.fromkeys( key_list, 3_저장) 
      + fromkeys는 반환형. 
      + 3_디폴트 None 
      + 3_value에 list형 저장하지 마삼. 공유돼버림. 
        + [0]*k는 요소인 0을 복사하는 거라 괜찮지만 [[0]*k]*m에서 m은 요소인 list를 참조해버려서 값이 동기화돼버림. 

    >> 2수정&없으면 추가 : [x.update([  [2,'aa'], [3, 'bb'] ]) ]
    : 1) dict1["new"]=1 # new로 하면 변수명으로 인식.
    : 2) x.update( ~ )
    : 2.1) x.update( {1: 'sa' , 3:'a'}) 
    :   input : 한 개의 딕셔너리

    : 2.2) x.update([  [2,'aa'], [3, 'bb'] ])
    :   input : 2차원 행열 /  각 행 =[키, 벨류]  
    :   x.update( zip ([2,3], ['aa','bb']) ) # zip_튜플 

    : X_2.3) ((키가 문자열일 때))  : x.update(e=90,a=10)  # 1) # 따옴표 빼야함

    # 샛기~~셋겟
    >> 3'에러 없는'조회 & 없으면 특정값을 출력&**저장** : [dict1.setdefault(key, 11)]
    : 1) dict1.setdefault(key, 11) 
      >  value 출력, 없는 키면 특정값을 출력 & 저장
      + 해당 키 없으면 원하는 값 반환 가능 

    >> 4조회만 & 없으면 특정값을 출력 :[x.get('a',0)]
    : 1) x.get('a',0) # value 출력, 없는 키면 에러 없이 0 출력
    : > <-> dict1[key1]은 원하는 값 반환은 없음

    >> 5삭제 
      +  없는 에러 대비 if문 필요. # -> 없을 시 -1을 저장하던지
    : 1) 무조건 특정 키 : dict1.pop('b') # 키라서 얘도 인덱스임
    : 2) 맨 위만 .popitem() 
        + python 3.7부터 공식적으로 딕셔너리 순서 있대[GPT]
        + 딕셔너리의 마지막 항목을 제거 & 그 항목을 튜플 형태로 반환

    : 3) del dict1['a'] 
    : 4) 전부 삭제 : dict1.clear()
    ```

- set
  + 생성  set set([10, 11, 12])    (다른 문자형에 set(씌우기)  
    set2 = set("selena") 
  + 추가 set1.update([11, 13])

- 파일 다루기
  + myFile = open("python.txt", "w") #파일 객체 = open(파일 경로, 열기 모드)
  + myFile.write("Programming!")
  + myFile.close()

  - "r" : 읽기 모드  
  
  + text = myFile.readline() : 재실행할 때마다 아직 안 읽었던 거 한 줄씩 반환
    > 빈줄 출력 체크

  + all_text = myFile.reandlines() : 모든 줄 읽어서 각 줄을 요소로 가지는 리스트 반환
  + = read_file.readline().strip() : \n제거용

- 가변 매개변수 : [*매개변수]
  + 체크 
    + 가변 매개변수 뒤에 일반 매개변수 올 수 없음
    + 가변 매개변수는 1개만 사용 가능
  + 인자의 개수를 고정하지 않고 변동성 있게 받을 수 있음
  + 함수 속 가변 매개변수 : 튜플형 나옴

  + ```python
    def menu(*values):
        print('카페 메뉴는?')
        print( values ) # 튜플형
        
    menu('아메리카노','초코라떼')
    # >> 인수로 2가지 메뉴 입력
    ```


- 클래스
  > 클래스 객체도 리스트의 요소 자리 가능
  
  + constructor[생성자] :  ``` def __init__ ```
    > 인스턴스 생성될 때 자동 실행
    
    + 클래스 내부 함수의 첫 번째 매개변수는 반드시 self 입력




- 상속
  + 선언 : 속성, 메소드 상속
  + 메소드 오버라이딩 : 부모 클래스의 메소드를 자식 클래스에서 재정의 하는 것

  + 부모와 자식에게 동일한 메소드 있을 시, 기본적으론 자식 클래스의 메소드 불러짐

  + ```python
    #[부모 클래스 선언]
    class Jelly :
  
    # [자식 클래스 선언] : 자식클래스(부모클래스)
    class TeddyBearJelly(Jelly, Jelly2) # 다중 상속
      def print_info(self):
        super().print_info()
        # super(). 부모의 해당 메소드 쌓아짐 (코드 라인에서)
        # 부모와 이름이 같은 메소드 있을 때 특히 유용
    ``` 

- 모듈, 병렬 파일
  + import module1 # 같은 폴더 위치에 잇는 py파일의 이름 부분
- 패키지
  + 모듈이 모여서 구조를 이룬 것
    
- try: except: else: finally:(예외 발생했든 안했든 무조건 실행)

## 2 파이썬 라이브러리 활용
- 드라이브 연결, 드라이브의 파일 읽기
  + ```python
    from google.colab import drive
    drive.mount('/content/drive')
  
    # csv 파일 읽어오기
    !pip install pandas 
    import pandas as pd
    titanic = pd.read_csv("/content/drive/MyDrive/titanic.csv")
    # -> 좌측 파일에 drive 폴더 보이게됨
    ``` 

### 2.1 matplotlib
+ ```
  !pip install matplotlib
  import matplotlib.pyplot as  plt
  import numpy as np
  
  # - 이름
  # plt.xlabel('Xlabel')
  # plt.ylabel('Ylabel')
  # plt.title( 'Graph Title', loc = 'center', pad =100      ) 
  # > loc : 'center' , 'left', 'right'
  # > pad : 타이틀과 그래프와의 간격 설정 [point 단위]

  # - 범례
  # plt.legend(loc='upper right', ncol=2) # 범례의 열 수

  # - 마커
  #   + 포맷 문자열 활용
   
  # plt.plot([1, 2, 3], "ro") 
  # plt.plot([0, 1, 2], marker='$A$') # A말고도 아무문자 가능
  
  # 'ro' : 빨간색 (‘red’)의 원형 (‘circle’) 마커
  # 'k^’ : 검정색 (‘black’)의 삼각형 (‘triangle’) 마커
  

  # - 축 범위
  # M1) plt.xlim([0,5]) # ylim
  # M2) plt.axis([0,6,0,20]) # x1, x2 , y1, y2



  # - 눈금 이름 변경 : 이미 plot_x,y 실행된 plt의 눈금 다른 걸로 변경
  # plt.xticks(x, ticks)


  # - .plot 모양 커스터마이징
  #   + Ex)
  # plt.plot([1, 2, 3], [4, 4, 4],'-s', color ='C0', label=" it is Solid", markersize=7, linewidth=5, alpha=0.7 ) 
  #  > -s(solid __line__ style + square __marker__), alpha(투명도)
  # plt.plot([1, 2, 3], [3, 3, 3],linestyle='dotted')

  #   + (1) linestyle
  #   + M1) '-' (solid), '- -' (dashed), ' : ' (dotted), ' -. ' (dashdot)

  #   + M2) 튜플과 값을 이용하여 선의 종류 미세조정
  # (0, (1, 1)) [dotted], (0, (5, 5)) [dashed], (0, (3, 5, 1, 5)) [dashdotted]
  #   + (2) color : 'C0' , 'C1'
  #   + (3) label : '~'

  
  # - 기타 plot 모양
  # + 막대 
  # plt.bar(x, y, color=['r', 'g', 'b'], width=0.4) 
  # > width 기둥 가로 너비

  # + 산점도
  # plt.scatter(x, y, s=size, c=colors) 
  # > size, colors : nparray로 각각 다르게 줄 수 있음
  #    np.random.seed(0)
  #   size = (np.random.rand(n) * 20)**2
  #   colors = np.random.rand(n)

  # - subplot : plt.subplot(행, 열, 행*열 index 중 누구)

  # - np.linspace(0, 10) : 0부터 10까지 50등분한 결과를 배열로 반환
  # x1 = np.linspace(0, 10)


  # - y축 값의 범위 다른 그래프 한 번에 그리기
  #   + .suplots() & ax1.twinx()
  # fig, ax1 = plt.subplots() # 객체 생성 plt.subplots(nrows=1, ncols=1)   
  # > figure와 axes(2개의 그래프가 있으면 a1, a2)를 반환해줌
  ax1.plot(x, y1)
  ax2 = ax1.twinx() # .twinx() 함수는 ax1과 축을 공유하는 새로운 Axes 객체 생성
  ax2.bar(x, y2, color='deeppink', alpha=0.7, width=0.7)
  # > ax.임 plt.아님

  # - tight_layout() 함수는
  #  + ((서브플롯)) 모서리와 서브플롯의 모서리 사이의 여백(padding)을 설정
  # plt.tight_layout()


  # x는 X축에 표시될 연도이고, y1, y2는 y 값 
  x = ['2022', '2023', '2024']
  y1 = np.array([1, 7, 14])
  y2 = np.array([1, 3, 9])

  # plt.subplots() 함수는 여러 개 그래프를 한 번에 가능, 객체 생성
  # plt.subplots(nrows=1, ncols=1) = plt.subplots()
  fig, ax1 = plt.subplots()

  # -s(solid line style + square marker), alpha(투명도)
  ax1.plot(x, y1, '-s', color='green', markersize=7, linewidth=5, alpha=0.7)

  # .twinx() 함수는 ax1과 축을 공유하는 새로운 Axes 객체 생성
  ax2 = ax1.twinx()
  ax2.bar(x, y2, color='deeppink', alpha=0.7, width=0.7)

  #plt.twinx()
  #plt.bar(x, y2, color='deeppink', alpha=0.5)


  plt.show()
  ``` 
  
### 2.2 seaborn
- 통계 기반 그래픽을 그리기 위한 고급 인터페이스

+ ```python
  # 설치
  !pip install seaborn
  import seaborn as sns

  # 데이터 로드
  titanic = sns.load_dataset('titanic')

  # 데이터 살피기
  titanic.head()
  titanic.info() # 전반적 정보 (행과 열의 크기, 컬럼명, 컬럼별 결측치, 컬럼별 데이터 타입)
  
  # swarmplot()
  # 데이터의 분산까지 고려하여 데이터 포인트가 서로 중복되지 않도록 시각화. 즉, 데이터가 퍼져 있는 정도를 입체적으로 파악 가능
  # swarmplot( ) 함수의 매개변수
  # x축 변수
  # y축 변수
  # 데이터 셋
  # hue : 특정 열 데이터로 색상을 구분하여 출력
  ```

### 2.2 beautifulSoup
- 웹 데이터 수집 | HTML 및 XML에서 데이터를 쉽게 처리함
- HTML은 태그, 수많은 공백과 변화하는 소스들 때문에 오류가 있을 가능성이 높은데 이 라이브러리를 사용하면 이런 오류를 고쳐서 줌


### Scikit Learn
  + 머신러닝을 위한 가장 쉽고, 효율적인 개발 라이브러리
  + 머신러닝 = Scikit-Learn일 정도로 오랜 기간 파이썬 영역에서 인정 받아 옴
  + R에 비견될 수 있는 __분석__ 라이브러리
  + __ML을 위한 다양한 알고리즘, 개발을 위한 프레임워크, API 제공__
  + __데이터 전처리, 모델, 성능 측정 등__

###  Numpy[STEP 11]
- 정리 옮기기 지금은 pass #~

###  Pandas[STEP 12]
- 정리 옮기기 지금은 pass #~
- 데이터 처리

## Self Feedback   
- 정리 시간
  > 정리 장점을 발휘 좋은데 그 정도 이상으로도 압축하려고 & 틀에 넣으려고 시간을 많이 쓰게됨. 자료제작과 스스로 공부용 정리는 소비 시간이 다른데 깃허브 공개 위치라 그런지 더 깔끔하게 저장하려고 하게 되네.

  + sol) 긴 정리는 형식 좀 살살하자. 덜 깔끔 압축이어도, 코딩 빨리 풀려고 의식적으로 해보듯 빨리 하려하는 것을 연습하자
  + sol) 암기 에도 시간 좀 배분하기!! (지금 당장 필요한 것) <-- 정리 자체 & 압축을 통해 여러 번 볼 때 효율적으로 하기
  + sol) __아는 내용이면 & 꼭 암기해야할 내용 아니면, 정리하려고 시간 쓰지 말자. 적당히 일정 부분 넘어가기__

## Reference 
[1] 한 번에 따라하는 파이썬 데이터 분석 기초 완주반 - Selena  
