<h1 align="center">Text to SQL Bedrock Agent</h1>


## Authors ( by Korean) :
**Yeonkyung Park** @yeonkp

## Introduction
자연어 처리의 힘을 활용한 "Text to SQL Bedrock Agent"는 자연어 질문을 실행 가능한 SQL 쿼리로 자동 변환하는 것을 용이하게 합니다. 
이 도구는 복잡한 데이터베이스 구조와 직관적인 인간 질문 간의 격차를 메우며, 사용자는 간단한 영어 프롬프트를 사용하여 데이터에서 쉽게 통찰력을 추출할 수 있습니다. 
AWS Bedrock의 최첨단 에이전트 기술을 활용하고 AWS의 강력한 인프라와 AWS Bedrock에서 제공하는 고급 대규모 언어 모델 간의 시너지를 보여주며, 정교한 데이터 분석을 더 많은 사람이 이용할 수 있도록 합니다.
이 repository에는 AWS 서비스와 함께 Bedrock Agent를 사용하여 Text to SQL 변환을 설정하고 테스트하는 데 필요한 파일이 포함되어 있습니다.

![sequence-flow-agent](images/text-to-sql-architecture-Athena.png)

## Use case
여기의 코드는 자연어 질문에서 SQL 쿼리를 작성할 수 있는 에이전트를 설정합니다. 
그런 다음 데이터베이스에서 응답을 검색하여 사용자 문의에 정확한 답변을 제공합니다. 
아래 다이어그램은 이 솔루션의 아키텍처를 간략하게 설명합니다.

에이전트는 다음을 위해 설계되었습니다.
- Retrieve database schemas
- Execute SQL queries


## 필수 조건

시작하기 전에 다음이 있는지 확인하세요.
- 다음 권한이 있는 AWS 계정:
- IAM 역할 및 정책을 만들고 관리합니다.
- AWS Lambda 함수를 만들고 호출합니다.
- Amazon S3 버킷을 만들고, 읽고, 씁니다.
- Amazon Bedrock 에이전트 및 모델에 액세스하고 관리합니다.
- Amazon Glue 데이터베이스 및 크롤러를 만들고 관리합니다.
- Amazon Athena에서 쿼리를 실행하고 작업 공간을 관리합니다.
- Amazon Bedrock 기반 모델에 액세스합니다(이 솔루션의 경우 Anthropic의 Claude 3 Sonnet 모델)

- 로컬 설정의 경우, 
- Python 및 Jupyter Notebook 설치
- AWS CLI 설치 및 구성
- AWS SageMaker의 경우 
- 도메인에 위의 권한이 있는지 확인합니다.
- SageMaker Studio에서 Data Science 3.0 커널 사용

## 설치 
로컬 머신이나 AWS 환경에 repository를 복제합니다.
git clone https://github.com/psps97/text-2-sql-agent.git

## Usage

1. `create_and_invoke_sql_agent.ipynb` Jupyter Notebook을 열어 시작합니다.
2. 노트북 셀을 순서대로 실행합니다. 노트북은 다음을 수행합니다.
- `config.py`에서 구성을 가져옵니다.
- 고유한 `AWS_PROFILE'을 설정합니다.
- `build_infrastructure.py`를 사용하여 필요한 인프라를 빌드합니다. 여기에는 다음이 포함됩니다.
- S3 버킷
- Lambda 함수
- Bedrock 에이전트
- Glue 데이터베이스 및 크롤러
- 필요한 IAM 역할 및 정책
3. 인프라가 설정되면 노트북 내에서 샘플 쿼리를 실행하여 에이전트를 테스트할 수 있습니다.
4. 생성된 모든 리소스를 삭제하고 지속적인 요금을 피하려면 노트북에서 clean.py 스크립트를 실행합니다.

