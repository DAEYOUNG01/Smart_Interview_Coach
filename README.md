# Smart_Interview_Coach 
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

# 1. 개발 배경 및 문제 정의 
<div align="center">
<img width="700" height="600" alt="Gemini_Generated_Image_r5frjlr5frjlr5fr" src="https://github.com/user-attachments/assets/f695b4c4-d69a-43c8-a22d-41e5c793c44f" />
</div>

#### 📊 1.1 채용/면접 프로세스의 현황

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

> **일관된 평가 기준 적용 및 대화형 면접 경험, 구체적 피드백을 동시에 제공하는 시스템의 부재**

<div align="center">
<img width="700" height="350" alt="image" src="https://github.com/user-attachments/assets/93502512-3782-4996-a5dd-89505cd5cc1d" />
</div>


* **평가 기준의 최적화**
    * 직무 및 조직 특성에 맞춘 질문·평가 기준 커스터마이징 수행
* **프로세스의 투명화**
    * 면접 전 과정 및 결과의 텍스트 기반 투명한 기록 및 관리
* **상세 피드백 제공**
    * 단순 합불 통보를 넘어선 지원자 강점·보완점 중심의 피드백 제공
* **HR 운영 효율화**
    * HR 담당자의 반복적 평가 업무 자동화 및 소요 시간·노동력 절감
















