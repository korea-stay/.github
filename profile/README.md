<div align="center">

# 🇰🇷 K-Stay
**AI 기반 한국 비자 서류 자동 작성 플랫폼**
<br/>
<em>"외국인의 복잡한 한국 체류 행정 절차, AI로 가장 쉽고 빠르게."</em>

<br/>

<img src="https://img.shields.io/badge/Python-3.9+-3776AB?style=flat-square&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/OpenAI-GPT--5-412991?style=flat-square&logo=openai&logoColor=white"/>
<img src="https://img.shields.io/badge/LangChain-RAG-000000?style=flat-square"/>
<img src="https://img.shields.io/badge/License-MIT-green?style=flat-square"/>

<br/>
<br/>

[🌐 Official Website ](https://k-stay.streamlit.app/) 

</div>

<br/>

## 📝 프로젝트 소개 (Introduction)

**K-Stay**는 유학생(D-2/D-4), 구직자(D-10), 결혼이민자(F-6) 등 한국에 체류하는 외국인들이 겪는 서류 작성의 어려움을 해결하는 **AI 자동화 솔루션**입니다.

복잡한 비자 서류를 일일이 작성할 필요 없이, 기본 정보만 입력하면 **RAG(Retrieval-Augmented Generation) 기반의 AI**가 법적 기준에 맞는 서류를 자동으로 생성하고 검토합니다.

### 🎯 핵심 기능
* **Universal Fact System**: 한 번 입력한 인적사항(여권, 주소 등)을 모든 서류에 자동 반영
* **AI Narrative Writer**: 구직활동계획서, 초청 사유서 등 서술형 문항 자동 작성 및 교정
* **Smart Validation**: 출입국 관리 사무소 기준에 맞춘 문법, 필수 키워드, 논리적 일관성 검토
* **AI Consultant**: 최신 법령/고시 데이터를 기반으로 한 실시간 비자 Q&A

<br/>

## 🏗 서비스 아키텍처 (Architecture)

K-Stay는 사용자 입력을 3단계 레이어로 구분하여 데이터 재사용성을 극대화하고, LLM을 통해 완성된 문서를 출력합니다.

```mermaid
graph LR
    User[사용자 입력] --> A[Data Layer]
    A --> B{AI Engine}
    B --> C[Document Layer]

    subgraph "Data Structuring"
        A1(Universal Fact<br/>기본 인적사항)
        A2(Variable Fact<br/>체류/재정 정보)
    end
    
    subgraph "AI Processing"
        B1(Narrative Generation<br/>서술형 작성)
        B2(RAG Validator<br/>법령 검토)
    end

    subgraph "Output"
        C1[통합신청서]
        C2[계획서/사유서]
        C3[신원보증서]
    end

    A --> A1 & A2
    A1 & A2 --> B1
    B1 --> B2
    B2 --> C1 & C2 & C3

