---
title: "Mvp 프로젝트 초기 셋업 과정"
datePublished: Fri Feb 07 2025 14:59:37 GMT+0000 (Coordinated Universal Time)
cuid: cm6uw7adr000209l7f66obn6m
slug: mvp

---

## 프로젝트 개요

환자 중심으로 소통과 정보 공유할 수 있는 커뮤니티 플랫폼의 MVP 작업

### 포함 기능

* 로그인 : 소셜 로그인 기능 (네이버, 카카오)
    
* 최초 설문 : 회원가입시 Survey 기능을 통한 유저 기초 정보 수집 기능
    
* 모임 : 유저 간 SNS 소통 기능 (텍스트와 이미지가 포함된 글 본문, 텍스트 댓글, 텍스트 답글)
    
* 아티클 : 서비스 관리자가 개시하는 관련 기사 페이지
    
* 마이페이지 : 프로필 수정 및 내가 쓴 글 모아보기 기능
    

## 프로젝트의 구성 요소

### Infrastructure

AWS 인프라 구성을 다음과 같이 해보았습니다. 우선 AWS IT 클라우드 시장 점유율이 압도적이라는 점에서 Route53, Cloudfront, S3, EC2, RDS 정도의 구성으로 시작할 생각입니다. MVP 까지가 제가 맡은 업무이고, 이후에 고도화 작업을 하게된다면 개발을 누가 맡게 될지 모른다는 측면에서 가장 점유율이 많은 AWS를 사용하는 것이 낫겠다는 판단이었습니다.

![MVP 인프라 구성](https://cdn.hashnode.com/res/hashnode/image/upload/v1738932787942/61cda632-856b-4649-831c-e30ffea6932e.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>MVP 제품으로 만들기 위해 최소한의 인프라를 사용하여 최소 비용으로 시장의 반응을 보기 위해 구성하였습니다. EC2 인스턴스를 중하급 인스턴스(t2.medium 시리즈)로 사용하여 적절한 성능과 메모리를 가지도록 하고, 해당 인스턴스 내에서 Docker를 사용하여 Frontend 앱과 Backend 서버를 운영할 예정입니다. (인프라 구성도 - 사진 👆)</strong></div>
</div>

![중장기적 인프라 구성 예상](https://cdn.hashnode.com/res/hashnode/image/upload/v1738933106270/a9b23819-eaeb-4b81-9b02-002fa3326298.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>중장기적으로는 많은 트래픽과 통신이 발생할 때에 좀더 다양한 인프라를 구성해서 운영하는게 좋을거라 생각해서 그려봤습니다. (중장기 인프라 구성도 - 사진 👆)</strong></div>
</div>

## 프로젝트 기술 스텍

### Frontend

* **Next.js** : SSR/SSG 지원으로 초기 로딩 속도와 SEO 최적화, 파일 시스템 기반의 직관적인 라우팅
    
* **TailwindCSS** : 신속한 개발과 일관된 디자인 시스템 구축, 유지보수 용이성 / 낮은 번들 사이즈
    
* **Zustand :** 간단한 API로 빠른 개발, 서버 사이드 렌더링 지원, 가벼운 번들 사이즈
    
    * Recoil 사용 경험이 있으면 빠르게 학습 후 사용 가능하다고 들음
        
* **Jest :** 직관적인 API와 최소한 설정, 풍부한 생태계와 프레임워크 지원, 병렬 테스트 실행으로 성능 최적화
    

### Backend (업데이트 중)