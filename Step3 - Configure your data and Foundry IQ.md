## 데이터 Foundry IQ 구성

이제 Foundry IQ를 사용해 지식 베이스를 검색하는 에이전트를 설정하면 됩니다.

1. 먼저, 에이전트에게 다음과 같은 지침을 주세요:

    ```
    당신은 아웃도어 캠핑 및 하이킹 제품 전문 기업인 콘토소(Contoso)의 친절한 AI 도우미입니다.
    제품 또는 제품 카탈로그에 대한 질문에 답변할 때는 항상 지식 기반을 검색해야 합니다.
    자세하고 정확한 정보를 제공하고 출처를 반드시 명시하세요.
    에이전트에 연결된 지식 및 도구에서만 정보를 참조하고, 관련 정보를 찾지 못한 경우에는 명확하게 알려주세요.
    ```

1. 현재 에이전트 구성을 저장하려면 **저장** 을 클릭하세요.
   
   <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/9f2ca54b-38a8-40a2-8bb9-301d237f4e5b" />

1. 그 다음 **지식** 섹션에서 **추가** 드롭다운을 펼친 후 **Foundry IQ 에 연결** 을 선택하세요.

   <img width="520" height="213" alt="image" src="https://github.com/user-attachments/assets/be59d77d-4d14-4854-bacb-d8a801273ca2" />

1. Foundry IQ 에 연결 창에서 **AI Search 리소스에 연결** 을 선택하세요.
1. 지식(Foundry IQ) 창에서 **새 리소스 만들기** 를 선택하면 자원을 생성하는 대화상자가 열립니다.
1. Create a search resource with the default settings:
    - **리소스 이름**: *전 세계적으로 고유한 이름입니다 (예: OO-contosodemo-srch)*
    - **구독**: *당신의 Azure 구독*
    - **리소스 그룹**: *프로젝트와 동일한 자원 그룹을 사용하세요.*
    - **지역**: *프로젝트와 같은 위치(East US)를 선택합니다. 단, 해당 지경의 용량이 가득 찬 경우 Korea Central 을 선택해도 무방합니다.*
    - **가격 등급**: *가능하면 무료이며, 그렇지 않으면 기본 요금을 선택하세요.*
    - *무료 월별 허용량을 초과하는 에이전트 검색 사용량에는 추가비용이 발생하고 Azure AI Search를 통해 청구됨을 확인합니다.* 를 **체크** 합니다.
    - **만들기** *버튼을 클릭하세요*

    > \* 일부 Azure AI 자원은 지역 모델 할당량에 의해 제약을 받습니다. 작업 후반에 할당량 한도를 초과할 경우, 다른 지역에 자원을 추가해야 할 수도 있습니다.
    > 

Foundry IQ와 연결할 샘플 제품 정보 문서를 업로드합니다.

1. 새 브라우저 탭을 열고 다음 채널로 이동하여 샘플 제품 정보 파일을 다운로드하세요. `https://github.com/MicrosoftLearning/mslearn-ai-agents/raw/main/Labfiles/04-integrate-agent-with-foundry-iq/data/contoso-products.zip`
1. 압축 파일을 추출하세요. 압축 파일은 Contoso의 제품에 대해 상세히 설명한 3개의 PDF 파일이어야 합니다.
     - contoso-backpacks-guide.pdf
     - contoso-camping-accessories.pdf
     - contoso-tents-catalog.pdf
1. 새 탭을 열고 Azure portal `https://portal.azure.com` 로 이동하세요. 상단 검색창에서 **Storage accounts** 를 검색한 후 **스토리지 계정** 을 선택하세요. 
   
   <img width="1543" height="598" alt="image" src="https://github.com/user-attachments/assets/3d0f971a-13ae-4a63-b35d-f8d21ad2201f" />
      
1. 다음 설정으로 스토리지 계정을 만드세요:
    - **구독**: *당신의 Azure 구독*
    - **리소스 그룹**: *프로젝트와 동일한 자원 그룹을 사용하세요.*
    - **스토리지 계정 이름**: *고유한 스토리지 계정 이름입니다. (예: sacontosodemoOO)*
    - **지역**: *프로젝트와 같은 위치(East US)를 선택합니다.*
    - **기본 서비스**: *Azure Blob Storage 또는 Azure Data Lake Storage*
    - **성능**: *표준*
    - **중복도**: *LRS(로컬 중복 스토리지)*
    - **검토 + 만들기** & **만들기** *버튼을 클릭합니다.*

      <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/4732c4a1-0c41-48fc-b19a-a557bf8f4f60" />
      
1. 스토리지 계정 배포가 완료되면 **리소스로 이동** 버튼을 클릭하세요.
1. 스토리지 계정 상단에 **업로드** 를 선택하세요.

   <img width="1283" height="291" alt="image" src="https://github.com/user-attachments/assets/277ea91b-482b-479e-8274-00132bbc0e1d" />

1. **Blob 업로드** 에서 컨테이너 **새로만들기** 링크를 클릭하세요.

   <img width="610" height="599" alt="image" src="https://github.com/user-attachments/assets/495d0fa1-9de9-4972-8abe-e50a504485d0" />

1. 새 컨테이너의 고유한 **이름**(예: **OO-contosoproducts**)을 입력하세요.
1. zip 파일에서 추출한 파일을 찾아서 3개의 PDF 파일을 모두 선택한 후 **업로드** 하세요.

   <img width="610" height="574" alt="image" src="https://github.com/user-attachments/assets/2da05aa5-d8d8-4628-8849-d8b8d0f2a314" />

1. **스토리지 브라우저**에서 Blob 컨테이너와 업로드된 파일을 확인하세요.

   <img width="2000" height="787" alt="image" src="https://github.com/user-attachments/assets/707ebde5-560d-4d58-90e1-09ee18f1ea0e" />

1. 스토리지 계정의 **설정 > 구성** 에서 **Blob 익명 엑세스 허용** 을 **사용** 으로 선택하고 **저장**하세요.

   <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/8eb6f548-c20d-4fdf-9be8-842a91a0efea" />


이제 앞에서 만든 AI Search (Foundry IQ) 로 이동 합니다.
1. AI Search(Foundry IQ) 의 왼쪽 창에 **보안 + 네트워킹** > **키** 에서 API 접근 제어를 위해 **모두** 를 선택하고 **기본 관리자 키** 를 클립보드에 복사하여 메모장에 붙여 넣습니다.

   <img width="1484" height="763" alt="image" src="https://github.com/user-attachments/assets/fae797f3-f7f4-4378-bb4b-bb6ee07b44a2" />

1. Azure Portal 을 열어둔 채 **Foundry Portal** 탭으로 돌아갑니다.

Foundry Portal 에서 에이전트와 연결할 지식 기반을 생성합니다.

1. **지식** 페이지에서 **지식 기반 만들기**를 선택하고 아래와 같이 구성합니다 :
    - **이름**: *고유한 이름을 입력합니다. (예: **kb-contosoproducts-OO**)*
    - **채팅 완료 모델**: *배포된 모델을 선택합니다. (예: **gpt-5-mini**)*

1. **지식원본** > **원본추가** 에서 **Azure Blob Storage**를 선택합니다.
1. **지식 원본 만들기** 를 아래와 같이 구성합니다 :
    - **이름**: *고유한 이름을 입력합니다. (예: **ks-contosoproducts-OO**)*
    - **설명**: `Contoso product catalog items`
    - **스토리지 계정**: *앞에서 만든 스토리지 계정 선택* `sacontosodemoOO`
    - **컨테이너 이름**: *앞에서 만든 스토리지 계정 선택* `contosoproducts-OO`
    - **인증 유형**: *API 키*
    - **콘텐츠 추출 모드**: *최소*
    - **포함 모델**: *사용 가능한 배포 모델을 선택하세요, text-embedding-3-small 일 가능성이 큽니다.*
    - **채팅 완료 모델**: *사용 가능한 배포 모델을 선택하세요* `gpt-5-mini`
1. **만들기** 를 선택하세요.

   <img width="590" height="851" alt="image" src="https://github.com/user-attachments/assets/f0503f85-f645-4a37-83d6-7bfa2722ebac" />

1. **지식 기반 저장** 을 선택하세요.
1. 지식 소스 상태가 **활성** 으로 바뀔때 까지 브라우저를 새로고침 하세요.

   <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/f308bdfe-e334-4527-9c4d-ca042cde7217" />

> 지식 소스가 활성화 되면 Azure Portal 의 **AI Search(Foundry IQ)** > **검색 관리** 에서 자동으로 생성된 **인덱서** 와 **인덱스** 를 확인할 수 있습니다.

1. 뒤로가기 버튼을 클릭하여 **지식** 페이지로 돌아간 후, **관리** 링크를 클릭하세요.

   <img width="2000" height="468" alt="image" src="https://github.com/user-attachments/assets/07cf6af0-bee2-4056-af93-f1a77d77bfb8" />

1. 아래의 **연결된 리소스** 탭에서 **CognitiveSearch** 행을 선택하고, 인증 섹션에서 **인증 편집** 을 클릭합니다.

   <img width="2000" height="1125" alt="image" src="https://github.com/user-attachments/assets/c7e7ae24-0a06-4da9-b38d-74033e2821fe" />

1. 인증 유형에서 **API 키** 로 변경하고, 메모장에 복사해 놓은 AI Search (Foundry IQ) 의 키를 **API 키** 항목에 **붙여넣기** 합니다.

   <img width="597" height="273" alt="image" src="https://github.com/user-attachments/assets/6f974b9c-b0dc-45ef-9f0b-6ea809e55ab5" />

1. 인증 편집 화면을 **저장** 합니다.

이제 Foundry IQ 설정이 완료되었습니다.



## 다음 단계

* [Step 04. 다양한 환경에서 Foundry IQ 테스트](Step4%20-%20Test%20the%20Agent%20in%20the%20Playground.md)

## 실습 순서

* [개요. Integrate Agent with Foundry IQ](README.md)
* [Step 01. Microsoft Foundry 프로젝트 생성](Step1%20-%20Create%20a%20Foundry%20Project.md)
* [Step 02. 에이전트 생성](Step2%20-%20Create%20an%20Agent.md)
* [Step 03. 데이터 Foundry IQ 구성](Step3%20-%20Configure%20your%20data%20and%20Foundry%20IQ.md)
* [Step 04. 다양한 환경에서 Foundry IQ 테스트](Step4%20-%20Test%20the%20Agent%20in%20the%20Playground.md)
* [Step 05. Foundry Toolkit 에서 도구 호출에 대한 승인 설정 및 테스](Step5%20-%20Connect%20to%20your%20Agent%20from%20an%20App.md)
* [Step 06. 앱에서 에이전트 통합 테스트](Step6%20-%20Test%20the%20Integration.md)
* [Step 07. 요약 및 리소스 정리(Cleanup)](Step7%20-%20Summary%20%26%20Clean%20up.md)
