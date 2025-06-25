---
title: "아직도 Iceberg 관리하느라 바쁘신가요? S3 Tables로 쉽고 빠르게 해결!"
seoTitle: "AWS Summit 2025 강연"
seoDescription: "Amazon의 S3와 S3 Tables"
datePublished: Sun Jun 22 2025 14:09:27 GMT+0000 (Coordinated Universal Time)
cuid: cmc7qursy000102jme2w12tc9
slug: iceberg-s3-tables
tags: conference, aws, it

---

안녕하세요! 써밋에서 들었던 세션 내용을 기록하려고 합니다

제가 5/15(목) Core Service Day에서 들었던 세션들은 다음과 같습니다

1. 아직도 Iceberg 관리하느라 바쁘신가요? S3 Tables로 쉽고 빠르게 해결!
    
2. 숨고 1,000만 가입자를 이끈 플랫폼의 클라우드 활용 전략 및 혁신 스토리
    
3. 생성형 AI 보안 강화 전략의 첫번째, 심층 방어 아키텍처 설계
    
4. 그저 Chill한 데브옵스 구축 : 생성형 AI를 통한 차세대 데브옵스 구성하기
    

이 글에선 *1\. 아직도 Iceberg 관리하느라 바쁘신가요? S3 Tables로 쉽고 빠르게 해결!* 에 대한 후기를 작성해보려고 합니다

  

---

## 1️⃣ 아직도 Iceberg 관리하느라 바쁘신가요? S3 Tables로 쉽고 빠르게 해결!

해당 세션은 두분이서 Amazon S3와 S3 Tables를 나눠서 진행하셨습니다

* 김용기
    
    * AWS 스토리지 전문 솔루션즈 아키텍트
        
* 김성연
    
    * AWS 분석 전문 솔루션즈 아키텍트
        

  

### ✅ Amazon S3 소개

![](https://velog.velcdn.com/images/rlaehdehd7/post/8a88bd56-6532-4f53-8ca5-3d21f3b702fc/image.png align="left")

Amazon S3는 AWS에서 가장 먼저 출시한 서비스로, 엑사바이트 규모의 Parquet 같은 표 형식(Tabular) 데이터를 저장합니다

![](https://velog.velcdn.com/images/rlaehdehd7/post/84d8431c-1a0f-4213-9814-0c0738214273/image.png align="left")

저는 Iceberg가 뭔지 처음에 몰랐었는데, Apache Iceberg는 대용량 분석 데이터를 위한 오픈소스 테이블 포맷이라고 합니다

[AWS - Apache Iceberg](https://aws.amazon.com/ko/what-is/apache-iceberg/)

다양한 기능이 있어 대용량 분석 데이터에 많이 사용되지만, 메타데이터 파일과 성능 최적화를 직접 관리해야 하는 번거로움이 있다고 합니다

  

### ✅ Amazon S3 Tables

![](https://velog.velcdn.com/images/rlaehdehd7/post/2b4727c4-79cb-4fbd-ac51-86d2382d965b/image.png align="left")

세션에서는 S3 Tables를 완전 관리형 Apache Iceberg Tables이라고 소개합니다

![](https://velog.velcdn.com/images/rlaehdehd7/post/eb9294e9-2d93-4498-9543-c7c5d1a038bb/image.png align="left")

![](https://velog.velcdn.com/images/rlaehdehd7/post/b1b3f727-c744-419e-842c-75b574ce8a43/image.png align="left")

다음과 같은 특징이 있습니다

* 데이터/메타 데이터 모두 S3에 저장함
    
* 삭제와 덮어쓰기 불가
    
* AWS CloudTrail 로그로 접근 이력 확인 가능
    

> 💡 콘솔에서 사용자가 직접 데이터 확인하는 것은 불가!!

![](https://velog.velcdn.com/images/rlaehdehd7/post/4975044f-2f03-4f9b-8a56-0431c8990c91/image.png align="left")

주요 기능은 다음과 같습니다

1. 최적화 성능
    
    * 초당 트랜잭션 성능 10배
        
        * [How Amazon Ads uses Iceberg optimizations to accelerate their Spark workload on Amazon S3](https://aws.amazon.com/ko/blogs/storage/how-amazon-ads-uses-iceberg-optimizations-to-accelerate-their-spark-workload-on-amazon-s3/)
            
    * 더 빠른 쿼리 성능 3배
        
        * [How Amazon S3 Tables use compaction to improve query performance by up to 3 times](https://aws.amazon.com/ko/blogs/storage/how-amazon-s3-tables-use-compaction-to-improve-query-performance-by-up-to-3-times/)
            
2. 보안 제어
    
    * 테이블 버킷&테이블 정책을 각각 설정할 수 있습니다
        
    * 네임스페이스 통해서 논리적 그룹화하기에, 그 기반으로 접근 제어할 수 있습니다
        
3. 비용 최적화
    
    * 주기적인 유지보수 작업을 실행
        
    * 정책을 기반으로 유지보수
        

  

### ✅ S3 Tables로 분석 워크로드 실행

직접 실습 영상을 통해 어떻게 생성하고 적용할 수 있는지를 보여주셨습니다

1. 테이블 버킷 생성
    
2. Amazon EMR에서 테이블 생성
    
    * sql문으로 생성 가능
        
3. Amazon Athena에서 테이블 쿼리
    
    * sql문으로 실행 가능
        
    * Athena에서 추가로 설정할 필요 없음
        
4. Amazon Redshift에서 테이블 쿼리
    
    * sql문으로 실행 가능
        
    * Redshift에서 추가로 설정할 필요 없음
        
5. AWS Lake Formation으로 세밀한 접근 제어
    
    * 특정 사용자를 지정해서 권한 제어
        
        * 테이블, 테이블의 특정 칼럼 단위로 권한 조정
            

> 💡 테이블 단위로 권한 부여 뿐만 아니라, 특정 칼럼 단위로도 권한 조정 가능함

6. 실시간 분석
    
    * 대규모 데이터 스트리밍 및 시각화
        

![](https://velog.velcdn.com/images/rlaehdehd7/post/20f60320-ed47-45dd-9982-4c81ac561b82/image.png align="left")

## 결론

### ✅ Amazon S3 Tables이란?

> S3의 완전 관리형 Apache Iceberg 테이블

* 특징 및 기능
    
    * 최적화된 데이터 레이아웃 기반으로 **쿼리 성능 향상**
        
    * **간소화된 테이블 보안** 제어
        
    * 스냅샷 관리 및 참조되지 않은 파일 제거로 **자동화된 스토리지 비용 최적화**
        

  

---

## 느낀점

S3 Tables의 소개 및 영업에 가까운 세션이었다(따끈따끈한 신상 서비스라고 하네요)

기술적인 측면이 많이 나올줄 알았는데, 사실상 S3 Tables 쓰면 복잡한 과정 줄이고 간편하게 쓸 수 있어 ~~를 세션으로 진행한 느낌이라 그 점은 좀 아쉬웠다