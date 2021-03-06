# software 설계 

## 설계 목차
- SW 설계 개념 및 원칙
- SW 설계의 실제
- SW 아키텍처 개념
- SW 아키텍처 뷰와 문서화

## SW 설계 개념 및 원칙
- 설계 --> 어떻게 만들까를 고민하는 과정. 수많은 대안 중에 하나를 선택하는 것
- 문제에 대한 해결(solution)을 도출하는 과정 
- 최악의 경우를 전제로 설계를 검증
- 좋은 설계는 설계 변경으로 인한 rework을 최소화하는 것
- 완벽한 설계는 좋은 설계의 적일 수도 있음  
  당장은 좋을 수 있지만, 설계 변경으로 인한 rework을 최소화 하는 것

### 설계에 대한 사실
-  SW 문제에 대해 최상의 솔루션이 하나인 경우는 없음
- 설계는 복잡하고 반복적인 프로세스. 초기 설계 솔루션은 잘못되었을 가능성이 크고, 최적의 상태도 아님

### 문제 해결 접근 방법
- 해결책이 있는 문제로의 매핑을 통한 문제 해결
- 기존의 해결책을 이용하지 않는 문제 해결
- 기존의 해결책을 일부 이용한 문제 해결 --> 일반적으로 패턴이 존재
- 재귀적 분할 정복에 의한 설계
- ** 설계는 기본적으로 분할하여 접근하는 것이 기본이다.
- 합성과 분석의 반복으로서의 설계
- 경험과 창의성의 결합
- 상하향식 절차로서의 설계

### 설계 원천 기법의 이해 
#### 관심사의 분리
- 관심사를 분리 -> 복잡도를 획기적으로 감소 -> 유지보수성 향상
- ex) Layered Architecture
- User Interface : 사용자에게 화면을 제시하고 입력을 받아 들이는 역할
- Application Layer : 해당 SW제품이 해야 할 임무를 수행하며, Domain Object들이 해야 할 업무를 주도함
- Domain Layer(Model) : 업무의 개념을 구현하는 계층으로 실제 업무의 제어와 규칙이 정의됨
- Technical Layer : 일반적 기술적 업무를 수행함. 예를 들어 메시지 핸들링, 그래픽스, 디바이스 제어 등

### 모둘화
- 프로그램 구성요소 간의 경계를 구분 --> 복잡성 감소
- 논리적인 구조를 물리적으로 형상화 하는 것
  - class : 독립적으로 관리되는 논리적 소스코드 단위
  - module : 독립적으로 관리되는 물리적 소스코드 단위

### 추상화(Abstraction)
- 객체화, 클래스화
  - 부모 클래스와 자식 클래스와의 관계 
  - 부모 모듈을 확장하거나 구체화 할 때 자식 객체를 생성
  - Inheritance 관계를 이용하면 Association 관계를 줄여 유지보수에 향상시킴


## SW 설계의 실제

### SW 설계 유형
- 상위/개략 설계
- 하위/상세 설계
- 구조(아키텍처) 설계
- 데이터 설계
- 사용자 인터페이스 설계
- 절차 설계

### SW 설계 과정
- 요구사항 정의 -> 구조 설계 -> 상세 설계 -> 구현 -> 시험
- 요구사항 정의와 구조 설계를 동시에 진행하거나, 상세설계와 구현을 동시에 진행하는 경우가 꽤 많음

### 구조 설계와 상세 설계
#### 구조 설계
- 시스템 수준에서 구성 컴포넌트들 간의 관계로 구성된 시스템의 전체적인 구조
- 비즈니스 요구사항을 기술로 해석
- 개발 방향을 알려주는 지도
- 의사소통의 매개체
- 정답은 없음. 수준에 맞게 이해할 수 있는 수준으로, 모든 내용은 다 담아야 함

#### 상세 설계
- 시스템 각 구성 요소들의 내부 구조, 동적 행위 등을 결정
- 구성 요소의 제어와 데이터들간의 연결에 대한 구체적인 정의를 하는 것
- 알고리즘, 데이터 구조, 클래스 내부 디자인, etc

### 구조 설계 접근법
- 크게 3가지만 기억하면 됨(용어를 기억하자)
- Static 설계  
  시스템을 구성하는 컴포넌트들과 그 기능들을 정의
- 인터페이스 설계  
  컴포넌트들의 상호 연결 구조를 정의
- Dynamic 설계  
  시스템 구성 컴포넌트들이 언제, 어떠한 순서로 상호작용하는지 정의


### Static 설계
- 시스템 보다 한단계 낮은 것들은 부르는 용어가 다름
- ex) 컴포넌트, 모듈, 유닛, 서브시스템...
- 더이상 나누어 지지 않는 것들은 반드시 유닛이라고 
- 가능한 독립성을 높이는 방향으로 함  
  why? 인터페이스가 많으면 좋지 않음. 변경시 불리함
- Static 설계 단위
  - 소프트웨어 -> 컴포넌트 -> 모듈 -> 유닛
- 컴포넌트 사이즈를 고려해야함
- 인터페이스 수를 제한하여 단순하게 하는 것이 중요
- 각 컴포넌트 관련 요구사항을 할당함  
  비기능 요구사항은(ex) 성능..) 단일 또는 다수 컴포넌트 또는 상위 컴포넌트에 할당 가능
- 컴포넌트 Hirarchy가 너무 넓거나 너무 깊으면 좋지 않음
- 컴포넌트 기능 설명을 표로 정리할 수 있음  
  획득 형태, 신규, 재사용, 수정재사용, 구매 .. 등

### 인터페이스 설계 
- 컴포넌트들의 상호 연결 구조를 정의
  - 연결(connectivity) : 컴포넌트 증가 시, 인터페이스 비용이 높아지고 신뢰도가 낮아짐
  - 결합(coupling) : 타 컴포넌트에 대한 의존도. 낮을수록 더 좋음
  - 응집(cohesion) : 기능적으로 유사한 컴포넌트들끼리의 관계 정도. 높을수록 더 좋음
- 결합도(coupling)
  - 모듈간의 관계의 강도를 표시
  - 결합도 종류가 다양함.  
    가장 안좋은 것은 내용 결합 --> 다른 모듈의 내부를 직접 참조 또는 공유하고 있음
- 응집도(Cohesion)
  - 우빌적 응집이 가장 응집도가 낮은 것
  - 기능적 응집이 가장 응집도가 높음 
- 계속 응집도를 높이고 결합도를 낮추는 방식을 반복하여 설계함.  


### dynamic 설계
- sequence chart(사다리 타기) 예
- 시스템 구성 컴포넌트들이 언제, 어떠한 순서로 상호작용하는지 정의
- 시나리오 별로 그리다 보면 컴포넌트들을 잘 만들었는지 확인 가능

### 상세 설계
- unit에 대한 문제. unit 하나하나가 어떤식으로 정의되어 있는지?
- 형태 : prototype, flow chart, entity relationship, diagram, pseudo code 등
- 포함 내용
  - input/output data 포멧
  - 인터럽트 정의(우선순위 포함)
  - 데이터 구조 포맷 정의
  - 처리 알고리즘
  - 데이터 필드 및 각 데이터 요소의 목적
  - 프로그램 구조 명세
- 최근 SW의 경우 상세 설계를 안쓰려고 함. 상세 설계와 구현을 함께 하는 경우가 많음
- 주석이 달린 코드를 읽어 문서를 생성

### 상세 설계 원칙
- function이나 subprogram에서 하나의 entry와 exit(return 문장이 하나로 만드는 것이 좋다는 의미)
- 동적 변수 X
- Initialization of variables(변수 초기화)
- 동일 변수명 불사용
- 전역 변수 불사용
- 포인터 사용 제한
- 암묵적 형 변환 금지
- No hidden data flow or control flow
- No uncondotional jumps
- No recursions

## SW 아키텍처
### SW 아키텍처 개요
- SW 시스템이 요구되는 기능과 품질을 갖고,  
  SW 시스템을 용이하게 구축하고 지속적인 운용과 개선을 위하여 필요한 진화성을 갖도록 하는  
  SW 시스템 구조 및 개발 전 공정에 대한 중요한 결정들
- 구성요소  
  서브시스템, 패키지, 컴포넌트와 같은 모듈

### SW 아키텍처의 특징
- 일정, 예산까지 고려
- 어떤 것들을 강조할 것이냐?가 중요

### SW 아키텍처의 필요성
- 이해관계자와의 대화 수단
- 초기 설계 결정 사항
  - 아키텍처는 개발 구조에 대한 전체적인 결정으로 개발 시에 지켜야할 제약 사항을 정함
  - 특정 시스템 품질의 달성 여부 및 수준 또한 결정.  
    아키텍처 설계를 통해 기능성 외에 성능, 변경용이성, 보안, 시스템규모 가변성, 재사용성 등의 품질속성들은 장려,억제 가능  
- 이전 가능한 재사용 모델(타 시스템 적용 가능한 시스템 추상화)  
  물리적으로는 프레임워크, 플랫폼의 형태로 구체화되어 여러 시스템에 적용되기도 함

### SW 아키텍처 결정 요인
- 기능 요구사항 : 시스템이 반드시 수행되야 되는 기능들
- 비기능 요구사항 : 제약 사항(기간, 비용), 품질 속성(가용성, 성능, 보안, 유지보수성)

### 품질 속성 시나리오
- Source of stimulus -> Stimulus -> Artifact -> Response -> Response measure

### 가용성 시나리오
- 가용성 일반 시나리오를 그려서 한번 생각해보는 것이 중요
- 잘못된 메세지 전달에서 적절히 대응하며 정상 동작하는 가용성 시나리오 사례

## 아키텍처 설계 뷰 작성
### 설계 전술(tactic)
- 아키텍처의 결정을 tactic이라고 말함
- 추구하는 품질 속성이 달성될지 여부는 설계 결정사항에 달림
- 설계 결정사항 = 설계 전술(tactic)
- 아키텍처 패턴 = 설계 전술을 일정 방식으로 묶은 패키지

### 가용성 설계 전술
- 결함 탐지
- 결함 복구
- 결함 방지

## Publisher-Subscriber(발행자 - 구독자) 예
- 한번의 호출로 다수의 협력 컴포넌트의 상태를 변경해야 하는 경우
- 특정 컴포넌트에서 발생하는 상태 변경 정보를 하나 이상의 컴포넌트에서 수신해야 함
- 해법
  - 하나의 컴포넌트를 Publisher로 두고 상태 변경을 받을 컴포넌트를 subscriber로 둠
  - Subscriber는 Publisher에서 제공하는 인터페이스를 통해 등록
  - Publisher 상태가 변경되면 등록된 subscriber에게 변경 상태를 전송

## SW 아키텍처 Views
- 뷰 포인트(관점) : 소프트웨어 시스템을 바라보고자 하는 방향
- 뷰 : 특정 뷰포인트를 가지고 시스템을 바라본 특정 형태 
- 뷰 타입 :  뷰에 종류를 구분하는 방법

## SW 아키텍처 관점의 정의
- 개념적 수준 : 사용 시나리오 관점, 기능 관점
- 논리적 수준 : 논리적 관점, 모듈 관점
- 물리적 수준 : 실행 관점, 코드 관점
- 배치 수준 : 물리적 실행 요소 배치 관점, 코드 요소의 배치 관점

## 4+1 View Model
- Logical View : 논리적 구조. 핵심 추상화, 객체와 객체 클래스로 표현. 
- Implementation View : 개발관점, 모듈과 라이브러리, 개발 단위의 구조
- Process View : 프로세스 관점, 동시성과 기능 분산에 초점. 컴포넌트와 커넥터 뷰
- Deployment View : 물리 관점. 소프트웨어 요소들이 대응되는 프로세스와 노드를 표현

## SW 아키텍처 평가
### ATAM(Architecture Tradeoff Analysis Model)
- 설계된 아키텍처가 이해관계자가 의도한대로 설계되었는지 확인하는 아키텍처 분석 및 평가 방법론
- 아키텍처 설계 접근 방법에 대한 Tradeoff, sensitivities, Non-Risk, Risk 분석


## 시험
### 시험 개념
- 시험  
  결합에 의해 발생될 장애를 드러내는 활동
- 디버김  
  결함의 원인을 밝히는 개발 활동
- 저 비용으로 중요한 결함을 찾아내는 것이 중요

### 시험활동에 대한 인식 변화 
- 시험 단계만의 활동 -> 전 개발 단계 활동
- 정상 수행 확인 -> 오류 발견
- 기능 확인 중심 -> 품질 metric 중심

#### 시험 수행 내용(오류 발견 목적)
- 명세 되었으나 구현되지 않거나 명세와 다르게 구현되어 있는 것을 오류라고 판단

### 주요 시험 용어
- Error(오류), Defect(결함), Failure(장애)
- SW가 최종사용자의 의도된대로 만들어졌는지 확인 : Validation
- SW가 명세된대로(요구사항대로) 만들었는지 확인  : Verification

- 시험 기준(Test Basis), 시험 수준(Test Level)
  - 시험 기준 : 요구사항 명세서 -> 구조 설계서 -> 상세설계서
  - 시험 수준 : 시스템 시험 -> 통합 시험 -> 단위 시험

- 테스트케이스(Test Case)  
특정 요구사항의 준수여부를 테스트 하기 위해 개발된 <b/>입력값, 실행 조건, 예상된 결과값</b>의 집합


## 시험 기법
### SW 시험 기법 분류(시험출제)
- 시험 대상 소프트웨어를 수행시키며 시험하는 지의 여부에 따른 분류
  - 정적 시험(Static Testing)  : 소프트웨어 수행하지 않음
  - 동적 시험(Dynamic Testing) : 소프트웨어 수행
- 시험 설계에 사용되는 정보의 출처에 따른 분류
  - 기능적 시험 : Black Box Testing, 명세 기반 설계
  - 구조적 시험 : White Box Testing, 코드 기반 설계

- Static + Black Box = 문서 Review
- Static + White Box = 코드 Review, Tool 기반 code Analysis
- Dynamic + Black Box = 서브시스템 실험, 시스템 통합 시험, 시스템 시험
- Dynamic + White Box = Tool 기반 White Box 시험

## 시험 방법
### 테스트케이스 설계 기법 분류
- 화이트 박스 같은 경우는 커버리지 라는 용어를 사용함
  - ex) 문장 커버리지, 결정 커버리지, 조건 커버리지... 등
- 블랙 박스
  - ex) Positive & Negative testing, 동등 분할, 경계값 분석

### Positive & Negative Tesging
- 타당하거나, 타당하지 않은 입력 데이터에 대해 시험

### 동등 분할(Equivalence class partitioning)
- 여러 시험 케이스 중에 실제로 수행할 대표적인 시험 케이스를 선택
- 동등 클래스 : 시험 될 때 동일하게 취급되는 입력집합

### 경계값 분석(Bounday Value Testing)
- 많은 결함이 입력 경계값에 근접한 값에 집중되는 경향이 있다는데 착안
- Class 내 경계 값을 시험함
- 동등 분할을 통해 데이터를 찾아낸 후 경계 부분 데이터를 선택하는 것이 효과적

## 동적 시험
### 커버리지(coverage), 시험 충분성(Test Adequacy)
- 완벽한 시험을 하는 것은 불가능
- 얼마 만큼 시험을 해야 하는가?
- 커버리지
  - 시스템이 시험된 정보를 나타내는 metric
  - 일반적으로 시험의 목표를 설정하는 방법 중의 하나

### 화이트박스 테스트
- 경로기반 테스트
  - 어떠한 순서로 테스트를 하는가?
- 문장 커버리지 : 라인 하나하나씩

### 경로 테스트(path Testing)
- 상호 독립적인 경로를 모두 수행, 잠재적 오류 발견
- 경로 테스트 절차
  - 흐름 그래프(flow graph) 생성
  - 선형적으로 독립적인 경로의 기본 집합 결정
  - 기본 집합에서 각 경로를 실행시킬 수 있는 테스트 케이스 준비

- 독립적인 경로 개수 계산
  - McCabe의 cyclomatic number 이용

- Cyclomatic number
  - 주어진 논리 흐름 그래프에서 선형적으로 독립적인 프로그램 경로의 개수
  - Cyclomatic Number = E - N + 2
    - E : Edge 개수
    - N : Node 개수

### 문장 커버리지
- 테스트에 의해 실행된 구문이 몇 퍼센트 인지 측정
- 테스트하려는 프로그램 내의 모든 문장들을 적어도 한번 이상 실행하도록 테스트 케이스 설계  
  가장 간단한 TEST 기법이고, 적어도 문장 커버리지가 100% 이상 되도록 테스트케이스 설계

### 결정 커버리지
- 분기 중 참, 거짓을 적어도 한 번 이상 실행시키도록 테스트 케이스 설계
- 프로그램 내의 모든 분기 조건들이 적어도 한번은 테스트 되어야 함
- 일반적으로 결정 커버리지는 문장 커버리지의 기준 만족

### 조건 커버리지
- 결정의 각 조건에 대해 최소한 한번씩은 모든 가능한 결과를 실행하도록 테스트 케이스 설계
- 전체 조건식의 결과와 관계없이 && 나 || 전후의 각 개별 조건식이 True, False 한번을 갖도록 TC를 만드는 방법

### 조건/결정 커버리지
- 조건, 결정 커버리지를 모두 가지도록 함

### 다중 조건 커버리지
- 모든 조건을 다 고려

### 변경 조건/결정 커버리지(MC/DC)
- Modified Condition/Decision Coverage
- 전체 조합을 테스트 하는 것은 현실적으로 불가능하므로, 가능한 한 의미있게 조합의 수를 줄여 테스트하기 위함

## 시험 도구
### CI(Continuous Integration) Server : 시험 자동화 도구
- 정적/동적 시험도구와 이슈관리 및 소스관리 도구를 연동
- 빌드 및 시험을 주기적으로 자동 수행하도록 스케쥴링 
- 웹 기반으로 시험 결과와 이력을 모니터링 가능한 시스템
- ex) jenkins