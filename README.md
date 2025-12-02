# Smart_Interview_Coach_LangChain
# AI 면접관 Agent

<div align="center">
  <img width="601" height="400" alt="image" src="https://github.com/user-attachments/assets/6eb98d63-b0c8-4528-86e8-f8e33ff48859" />
</div>

---

# **CONTENST**

### 1. 개발 배경 및 문제 정의

* **채용/면접 프로세스의 현황** 
* **AI 면접과 Agent가 풀고자 하는 핵심 문제 및 필요성**
* **요구사항 정의**

### 2. 시스템 개요 및 서비스 흐름
* **전체 시스템 아키텍처**
* **서비스 프로세스**
* **주요 기능 요약**

### 3. 데이터셋 구축 및 전처리
* **데이터 수집**
* **평가 루브릭 정의**
* **데이터 전처리**

### 4. Agent 설계 및 구현
* **LLM & Prompt Engineering**
* **System Prompt 설계**
* **대화 관리**
* **자동 평가 모듈 설계**

### 5. 실험 및 성능 평가
* **실험 환경 및 설정**
* **결과 분석**

### 6. 기대 효과 및 활용 방안
* **활용에 대한 기대효과**
* **B2G & B2B 시나리오**
* **사회적/경제적 기대 효과**

---

# 1️⃣ 개발 배경 및 문제 정의 
<div align="center">
<img width="700" height="600" alt="Gemini_Generated_Image_r5frjlr5frjlr5fr" src="https://github.com/user-attachments/assets/f695b4c4-d69a-43c8-a22d-41e5c793c44f" />
</div>

### 🍎 1.1 채용/면접 프로세스의 현황

> **서류 전형 → 필기/AI역량검사 → 1·2차 면접 → 최종 합격 통보**

<table>
  <thead>
    <tr>
      <th width="100">단계</th>
      <th width="150">세부 절차</th>
      <th width="650">상세 내용</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><b>사전 준비</b></td>
      <td align="center"><b>서류 검토</b></td>
      <td>
        • 지원자의 기본 사항(학력, 경력, 자격증 등) 파악<br>
        • 이력서·자기소개서를 읽고 주요 경험과 키워드(프로젝트, 역할, 성과 등) 정리
      </td>
    </tr>
    <tr>
      <td align="center"></td>
      <td align="center"><b>면접 전략 수립</b></td>
      <td>
        • 직무·조직에 따라 핵심 확인 포인트(직무 적합도, 성장 가능성 등) 선정<br>
        • 각 면접관에게 담당 영역과 질문 방향을 분배하고, 예상 질문 리스트를 준비
      </td>
    </tr>
    <tr>
      <td align="center"><b>면접 진행</b></td>
      <td align="center"><b>질문 및 답변</b></td>
      <td>
        • 준비 질문 중심 질의응답을 진행, 답변 내용을 간단히 메모하거나 평가표에 기록<br>
        • 답변 검증 필요 시, 심화/추가 질문을 통해 정보 보완
      </td>
    </tr>
    <tr>
      <td align="center"></td>
      <td align="center"><b>면접 평가</b></td>
      <td>
        • 면접 종료 후 면접관들이 모여 지원자에 대한 의견 공유·조율<br>
        • 전문성·태도 등 항목별 수동 평가 및 결과 취합 후 최종 결정
      </td>
    </tr>
  </tbody>
</table>

---

### 🍎 1.2 AI 면접관 Agent가 풀고자 하는 핵심 문제

> **일관된 평가 기준 적용 및 대화형 면접 경험, 구체적 피드백을 동시에 제공하는 시스템의 부재**

<div align="center">
<img width="600" height="350" alt="image" src="https://github.com/user-attachments/assets/93502512-3782-4996-a5dd-89505cd5cc1d" />
</div>


| 구분 | 주요 목표 및 내용 |
| :--- | :--- |
| 💡 **평가 기준의 최적화** | 직무 및 조직 특성에 맞춘 질문·평가 기준 커스터마이징 수행 |
| 💡 **프로세스의 투명화** | 면접 전 과정 및 결과의 텍스트 기반 투명한 기록 및 관리 |
| 💡 **상세 피드백 제공** | 단순 합불 통보를 넘어선 지원자 강점·보완점 중심의 피드백 제공 |
| 💡 **HR 운영 효율화** | HR 담당자의 반복적 평가 업무 자동화 및 소요 시간·노동력 절감 |

---

### 🍎 1.3 AI 면접관 Agent 요구사항 정의

* **답변에 대한 다각도 평가 체계 구축**
* **질문 및 평가 기준 커스터마이징 기능**
* **면접 질문-답변-평가 전 과정 로그화 및 텍스트 기록**
* **자동 평가 및 점수 산출 로직 설계**
* **평가 결과 리포트 자동 생성**
* **지원자 강점,보완점 중심 피드백 제공 기능**
* **HR 담당자의 평가 업무 부담 경감을 목표로 한 프로세스 자동화**

---

# 2️⃣ 시스템 개요 및 서비스 흐름

### 🍉 2.1 서비스 프로세스 (질문 생성 → 답변 수집 → 평가 → 피드백)

<div align="center">
<img width="700" height="480" alt="2025-11-28 13 22 06" src="https://github.com/user-attachments/assets/1a2865e0-52fa-43a5-88e2-4283d8a994da" />
</div>

> **전체적인 AI 면접관 시스템 구조도**

---

### 🍉 2.2 전체 시스템 아키텍처

| Initial model | feature engineering |
|---------|---------|
| <img width="550" height="420" alt="image" src="https://github.com/user-attachments/assets/4486b7b2-e6ed-4a4c-8fc3-5cc585b2860d" /> | <img width="550" height="420" alt="image" src="https://github.com/user-attachments/assets/b8de08ac-b15d-437b-a94c-398de419f428" /> |

> **초기모델 -> 고도화를 통한 요구사항 추가**

<div align="center">
<img width="550" height="420" alt="image" src="https://github.com/user-attachments/assets/7429f337-be18-4dc1-ae3b-6c963546d074" />
</div>

> **Gradio 사용 구조**

---

### 🍉 2.3 주요 기능 요약

> **전체 AI Agent 기능 정리**

<table>
  <thead>
    <tr>
      <th width="200">기능명</th>
      <th width="600">상세 내용 및 핵심 로직</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>💡 <b>질문 생성 및 선정</b></td>
      <td>
        • 이력서 기반 질문 풀(Pool) 생성 후, 키워드 중요도에 따른 재정렬·선별 수행<br>
        • 직무·경험 키워드 중심의 핵심 역량 검증용 구조화된 질문 노출
      </td>
    </tr>
    <tr>
      <td>💡 <b>자동 평가</b></td>
      <td>
        • 5개 항목(관련성·구체성·논리성·실무성·소통) 기준 5단계 세분화 평가<br>
        • 평가 결과의 JSON 구조화(점수·등급·코멘트) 및 피드백 모듈 연동
      </td>
    </tr>
    <tr>
      <td>💡<b>인터뷰 Flow Control</b></td>
      <td>
        • 답변 평가 점수에 따른 다음 질문 유형(꼬리 질문 vs 새 질문) 동적 결정<br>
        • 일정 개수/시간 및 점수 조건 충족 시 면접 자동 종료 처리
      </td>
    </tr>
    <tr>
      <td>💡 <b>맞춤형 피드백 생성</b></td>
      <td>
        • 질문별 평가 결과 기반 강점 요약·보완점 및 향후 연습 방향 자동 생성<br>
        • 웹 대시보드를 통한 전체 피드백 일괄 확인 및 시각화 제공
      </td>
    </tr>
    <tr>
      <td>💡 <b>종합 리포트 생성</b></td>
      <td>
        • 지원자별 종합 점수·등급 및 인터뷰어 코멘트가 포함된 보고서 자동 생성<br>
        • 레이더 차트 등 시각화 도구를 활용한 지원자 간 상대 평가 지원
      </td>
    </tr>
    <tr>
      <td>💡 <b>관리자 기능</b></td>
      <td>
        • 평가 루브릭, 질문 템플릿, 점수 매핑 로직 등의 커스텀 수정·관리<br>
        • 면접 세션별 State(진행 상황, 로그) 조회 및 LLM 모델/프롬프트 설정 변경
      </td>
    </tr>
  </tbody>
</table>

--- 

# 3️⃣ 데이터셋 구축 및 전처리

### 🍊 3.1 데이터 생성 전략 (Data Generation)

> **정적 질문 리스트 대신, 지원자의 이력서 내용을 바탕으로 개인화된 면접 질문을 동적으로 생성**

* **Source Data: 사용자 업로드 이력서 (PDF, DOCX)**
* **생성 모델: GPT-4o-mini (속도 및 비용 효율성 고려) - GPT-4o 등 모델 교체 가능**
* **질문 생성 프로세스 요약**
  
| 질문 생성 프로세스 | 상세 내용 |
| :--- | :--- |
| 💡 **Resume Parsing** | 파일(PDF, DOCX)에서 텍스트 데이터 추출 |
| 💡 **Summary & Keyword Extraction** | LLM이 이력서 내용을 요약하고 핵심 키워드(5~10개)를 추출 |
| 💡 **Strategy Generation** | 3대 평가 영역(경력, 동기, 논리)별 맞춤형 질문 전략 수립 |
| 💡 **Deepen Question** | 지원자의 이전 답변을 바탕으로 심층 꼬리 질문(Follow-up) 생성 |

--- 

### 🍊 3.2 평가 루브릭 (Evaluation Rubric)

> **면접관 Agent가 일관성 있는 평가를 수행하기 위해 5가지 핵심 평가 지표와 5점 척도를 정의하여 시스템 프롬프트(System Prompt)에 적용**

* **평가 모델: GPT-4o (정확하고 깊이 있는 평가를 위해 고성능 모델 사용)**
* **평가 척도: 1점(하) ~ 5점(상) 정량 평가 + Weak Points(보완점) 정성 평가**

| 평가 항목 (Metric) | 평가 기준 (Criteria) |
| :--- | :--- |
| 💡 **1. 질문과의 관련성** | 질문의 핵심 의도를 파악하고 동문서답하지 않았는가? |
| 💡 **2. 답변의 구체성** | STAR 기법 등 구체적인 수치, 사례, 근거를 제시했는가? |
| 💡 **3. 논리적 일관성** | 주장의 앞뒤가 맞고 기승전결이 뚜렷한가? |
| 💡 **4. 커뮤니케이션 명확성** | 용어 사용이 적절하고 문장이 간결하며 이해하기 쉬운가? |
| 💡 **5. 실무 임팩트/성과** | 조직의 KPI나 기술적 성과에 기여한 바가 명확한가? |

--- 

### 🍊 3.3 데이터 전처리 및 구조화 (Preprocessing & Structuring)

> **비정형 텍스트(이력서, 구어체 답변)를 Agent가 처리 가능한 구조화된 데이터(State)로 변환하는 과정 수행**

| 텍스트 추출 (Parsing) | 설명 |
| :--- | :--- |
| 💡 **PDF** | PyMuPDF 라이브러리를 사용하여 페이지별 텍스트 추출 및 병함 |
| 💡 **DOCX** | python-docx를 사용하여 문단 단위 텍스트 추출 |
| 💡 **Cleaning** | 불필요한 공백 제거 및 줄바꿈 문자 정규화 |

| 데이터 구조화 (Structuring) | 설명 |
| :--- | :--- |
| 💡 **LangGraph State 관리** | 인터뷰 전체 맥락을 유지하기 위해 InterviewState (TypedDict) 정의 |
| 💡 **JSON Parsing** | LLM의 출력을 Python 객체로 변환하기 위해 PydanticOutputParser 적용 |
* **예: Resume Summary -> summary_n_keywords 객체로 변환**
* **예: Evaluation Result -> eval_answer 객체로 변환**
<p></p>

* 💡 **토큰 관리 전략**
* **이력서 전체를 매번 프롬프트에 넣는 대신, 요약문과 키워드를 추출**
* **Context로 활용함으로써 토큰 비용 절감 및 처리 속도 향상**

--- 

# 4️⃣ Agent 설계 및 구현 (Architecture & Implementation) 🌠

> **본 시스템은 LangGraph 프레임워크를 기반으로 State를 관리, 역할에 따라 최적화된 LLM 모델 하이브리드 운용**

### 🌠 4.1  LLM & Prompt Engineering

> **효율적인 비용 관리와 응답 속도, 그리고 평가의 정확도를 모두 확보하기 위해 두 가지 모델을 목적에 따라 분리 후 사용**

<table>
  <thead>
    <tr>
      <th width="150">모델</th>
      <th width="200">사용 모듈</th>
      <th width="700">선정 이유</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>💡 <b>GPT-4o</b></td>
      <td align="center"><b>답변 평가<br></td>
      <td><b>복합적인 맥락 이해와 논리적 추론 능력 ⬆️, 답변의 미세한 뉘앙스와 점수 산정의 정확성을 보장</b></td>
    </tr>
    <tr>
      <td>💡 <b>GPT-4o-mini</b></td>
      <td align="center"><b>질문 생성, 이력서 분석</b></td>
      <td><b>빠른 응답 속도와 낮은 비용으로 실시간 인터뷰의 효율성 향상</b></td>
    </tr>
  </tbody>
</table>

---

### 🌠 4.2  System Prompt 설계 (Persona Definition)

> **면접관 Agent가 일관된 태도를 유지하도록 페르소나와 제약 조건을 명확히 설정**

* **페르소나 (Persona): "전문적인 HR Recruiter" 및 "면접 코치"**
* **어조 (Tone): 객관적이고 중립적인 태도, 정중한 한국어 존댓말 사용**
* **제약 조건 (Constraints)**
  - 질문은 한 번에 하나씩만 제시 (모호성 배제)
  - 답변에 대한 힌트나 예시 제공 금지 (지원자 역량 검증 목적)
  - 모든 출력은 지정된 JSON 스키마를 엄격히 준수
    
---
    
    SYSTEM: "너는 채용 면접 코치다. 아래 정보를 바탕으로 ‘이전 답변’을 검토한 후 
    지원자의 사고력·문제해결 방식·기술적 깊이를 더 확인할 수 있는 
    심화 인터뷰 질문 1개만 생성하라. 반드시 JSON으로만 답하라."
    
    REQUIREMENTS:
    - 이전 답변의 빈약하거나 모호했던 지점을 겨냥해 한 단계 파고드는 질문 생성
    - 유사 질문/중복 질문 금지
    - '왜/어떻게/무엇을 기준으로' 같은 탐색형 질문 활용

---

### 🌠 4.3  대화 관리 (Dialogue Management)

> **LangGraph를 활용하여 인터뷰의 전체 흐름(Context)을 상태(State)로 관리하고, 평가 결과에 따라 다음 행동을 동적으로 결정**

* **💡State관리 (InterviewState)**
    - conversation : 누적된 대화 로그 (History)
    - current_score : 최근 답변의 평가 점수
    - resume_summary, keywords: 이력서 분석 고정 데이터

* **💡컨텍스트 유지 (Context Retention)**
    - 단순 모든 대화 기입 x, 이력서 요약 + 직전 Q&A + 평과 결과를 프롬프트에 주입 후 토큰 효율성 향상 + 맥락 유지

* **💡동적 꼬리 질문 로직(Dynamic Follow-up)**
    - 답변 평가 점수(5점 만점)에 따라 다음 노드로 분기
    - 2.0 < 점수 < 3.5: 답변이 애매하거나 검증이 필요한 경우 → 꼬리 질문(Deepen Question) 생성
    - 그 외 (너무 낮거나 완벽함): 더 파고들 필요가 없다고 판단 → 새로운 주제(New Topic)로 전환

--- 

### 🌠 4.4  자동 평가 모듈 설계 (Auto-Evaluation)
> **주관적인 텍스트 평가를 정량적인 점수로 변환하기 위해 Pydantic Parser를 활용하여 구조화된 데이터를 출력**

<div align="center">
<img width="450" height="349" alt="image" src="https://github.com/user-attachments/assets/e67fff1d-c358-439b-859c-c02823ae4282" />
</div>

* **Input: 질문, 답변, 이력서 요약, 현재 전략**
* **Output: JSON (평가 항목별 점수, 총점, 보완점 리스트)**
  
* **점수 산출 로직 (Scoring Mapping)**
    - 5개 평가 항목(관련성, 구체성, 논리성, 명확성, 성과)에 대해 각각 1~5점 부여
    - 평균 점수를 자동 계산하여 current_score State 업데이트

* **피드백 생성 알고리즘**
    - [질문 의도 파악] -> [답변 분석] -> [부족한 점 도출] 과정 후
    - 지원자가 어떤 부분을 보완해야 합격 확률을 높일 수 있는지 구체적인 가이드 제공

--- 

# 5️⃣ 실험 및 성능 평가 (Architecture & Implementation) 

<div align="center">
<img width="700" height="480" alt="image" src="https://github.com/user-attachments/assets/b0fa62ba-17aa-4279-981d-9596ae8e7b0d" />
</div>

### 🍌 5.1 정량적 평가 (Quantitative Evaluation)
> **시스템 내부적으로 정의된 5가지 평가 지표(Rubric)에 따라 LLM이 산출한 점수의 분포와 경향성을 분석**

* **평가 지표: 관련성, 구체성, 논리성, 명확성, 실무 성과 (각 5점 만점)**
* **점수 산출 결과**
    - 답변의 구체성(수치, 사례)이 부족할 경우 → 평균 3.0점 이하 부여
    - 질문 의도에 부합하고 근거가 명확한 경우 → 평균 4.5점 이상 부여
* **동적 분기 검증**
    - 점수가 2.0점 이하일 때 → decide_next_step 함수가 정상적으로 종료(End) 또는 재질문으로 라우팅 함을 확인
    - 점수가 애매한 구간(2.0~3.5)일 때 → 꼬리 질문(Deepen Question)이 생성됨을 확인
 
---

### 🍌 5.2 정성적 평가 (Qualitative Evaluation)
> **실제 생성된 인터뷰 리포트와 피드백의 구체성을 바탕으로 면접관으로서의 자연스러움을 평가**

<table>
  <thead>
    <tr>
      <th width="200">평가 항목</th>
      <th width="1000">평가 결과 및 관찰 내용</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>💡 <b>피드백 구체성</b></td>
      <td>단순한 "좋음/나쁨"이 아닌, "수치적 성과가 부족하다", "협업 관점의 설명이 필요하다" 등 구체적인 약점을 지적</td>
    </tr>
    <tr>
      <td>💡 <b>질문 자연스러움</b></td>
      <td>이전 답변 맥락을 반영 "~라고 하셨는데, 구체적으로 어떤 기술을 사용했나요?"와 같은 자연스러운 연결형 질문 생성</td>
    </tr>
    <tr>
      <td>💡 <b>리포트 품질</b></td>
      <td>면접 종료 후 생성된 종합 리포트가 지원자의 강점과 보완점을 구조적으로 요약 </td>
    </tr>
  </tbody>
</table>

---

# 6️⃣ 기대 효과 및 활용 방안 (Expected Effects & Application)
> **본 AI 면접관 Agent는 채용 담당자(HR)의 업무 효율성을 극대화하고, 구직자에게는 언제 어디서나 접근 가능한 고품질의 모의 면접 환경을 제공**

### 🥝 6.1 대상별 기대 효과 (Benefits by Target)

<table>
  <thead>
    <tr>
      <th width="200">대상</th>
      <th width="200">핵심 가치</th>
      <th width="600">상세 기대 효과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">🏢 <b>기업 / HR</b></td>
      <td align="center"><b>비용 절감 & 효율화</b></td>
      <td>
        • 1차 서류/면접 단계의 반복적인 평가 업무 자동화<br>
        • 정량화된 평가 기준(Rubric) 적용으로 <b>평가 일관성 확보</b><br>
        • 면접 전 과정의 텍스트 로그화로 <b>기록 자동화</b>
      </td>
    </tr>
    <tr>
      <td align="center">🏫 <b>학교 / 교육기관</b></td>
      <td align="center"><b>진로 지도 고도화</b></td>
      <td>
        • 학생 개개인의 이력서에 맞춘 맞춤형 모의 면접 훈련 제공<br>
        • 교사/상담사가 학생 전체를 케어하기 힘든 상황에서 보조 교사(Assistant) 역할 수행<br>
        • 취업 지원 센터의 상담 효율성 증대
      </td>
    </tr>
    <tr>
      <td align="center">🧑‍💻 <b>취업 준비생</b></td>
      <td align="center"><b>무제한 실전 연습</b></td>
      <td>
        • 시공간 제약 없는 반복 연습으로 면접 불안감 해소<br>
        • 객관적인 피드백 리포트를 통해 자신의 <b>강점과 약점 파악</b><br>
        • 예상치 못한 꼬리 질문(Deepen Question)에 대한 대응 능력 향상
      </td>
    </tr>
  </tbody>
</table>

---

### 🥝 6.2 비즈니스 프로세스 통합 시나리오
> **본 시스템은 B2B 및 B2G 모델로 확장이 가능**

**💼 B2B: 기업 채용 프로세스 연동**

1. 서류 접수: 지원자가 채용 포털에 이력서(PDF) 업로드
2. AI 역량 검사 (Pre-Interview): AI Agent가 지원자와 15~20분간 심층 채팅 면접 진행 (ex_구현된 Gradio 활용)
3. 스크리닝 보조: AI가 생성한 종합 평가 리포트와 점수를 HR 담당자에게 전달
4. 최종 면접: 면접관은 리포트를 참고하여 심층적인 인성/직무 면접에만 집중

<br>

**🏛️ B2G: 공공 일자리 센터 키오스크/웹 서비스**

1. 청년 취업 사관학교 / 고용복지센터: 키오스크/웹 기반 자가 면접과 상담사 코칭을 결합한 하이브리드 모델 구축

<br>

**🌈 6.3 사회적/경제적 파급 효과 (Social & Economic Impact)**

1. 채용 공정성 강화: 블라인드 로직 및 고정 프롬프트 적용을 통한 인간적 편향 배제와 데이터 기반의 객관적 평가 구현
2. 기회의 평등 제공: 시공간 제약 없는 양질의 면접 코칭 제공을 통한 컨설팅 비용 절감 및 취업 역량 격차 해소
3. HR 리소스 최적화: 단순 반복 검증의 AI 자동화를 통한 HR 담당자의 핵심 역량 평가 및 고부가가치 업무 집중 유도

