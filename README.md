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

### 7. 한계점 및 향후 연구 방향
* **보완 계획**
* **AI Agent의 한계점**

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
        • 준비한 질문을 중심으로 질의응답을 진행, 답변 내용을 간단히 메모하거나 평가표에 기록<br>
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

