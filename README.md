# 간단한 블록체인 서비스 구현하기

이 프로젝트는 Hyperledger Fabric를 사용하여 간단한 블록체인 서비스를 구현한 것입니다. 이 문서는 해당 프로젝트의 구현 방법과 사용법에 대해 설명합니다.

## 목차

1. [개요](#개요)
2. [사용 기술](#사용-기술)
3. [사전 설치](#사전-설치)
4. [프로젝트 구조](#프로젝트-구조)
5. [체인코드 설명](#체인코드-설명)
6. [실행 방법](#실행-방법)
7. [기여하기](#기여하기)
8. [라이선스](#라이선스)

## 개요

이 프로젝트는 블록체인 서비스를 구현하기 위한 간단한 예제입니다. 2023.07.03 - 2023.07.28일 인턴 기간 중 7일 동안 혼자 공부하여 구축했습니다.

## 사용 기술

- Hyperledger Fabric
- Java (체인코드 개발)
- Docker-Compose

## 사전 설치

다음 사항들이 설치되어 있어야 합니다.

- Docker
- Docker Compose
- Hyperledger Fabric Binaries
- Java SDK
- Go Language

자세한 사전 설치 방법은 [링크](https://hyperledger-fabric.readthedocs.io/en/latest/prereqs.html)를 참조해주세요.

## 프로젝트 구조

프로젝트는 다음과 같은 구조를 가지고 있습니다.
![스크린샷 2023-07-25 오후 3 42 21](https://github.com/KangminNa/blockchainweb/assets/139530542/36303ba1-9b6a-4bee-82b9-6b5de9256178)


## 체인코드 설명

체인코드는 Java 언어를 사용하여 구현되었습니다. Fabric-Samples에 있는 예제를 활용했습니다. 파일을 확인하면 체인코드의 주요 기능과 트랜잭션 처리 방법이 구현되어 있습니다.

## 개발 순서 및 실행 순서

1. cryoto-config 작성하기.
2. fabric-tools:latest 이미지를 활용하여 인증서 발급
   2.1.docker run --rm -v <본인이 다운받은 혹은 프로젝트 실행 부분 위치>:/opt -w /opt hyperledger/fabric-tools:latest cryptogen generate --config=crypto-config.yaml
   2.2 docker run --rm -v /Users/mac_nkm/docker/blockchainweb:/opt -w /opt hyperledger/fabric-tools:latest cryptogen generate --config crypto-config.yaml
4. 생성된 crypto-config를 활용하여 configtx.yaml을 작성하여 네트워크 및 블럭, 채널 설정
5. crypto-config의 작성된 peer와 orderer에 맞춰서 docker-comopse.yml 작성
6. chaincode 작성 및 채널 생성 및 peer에 배포

## 부족한 점
- 블록체인에 대한 선수지식 부족
- linux에 구축되어 있는 참고자료와 mac docker 환경과 비교했기에 진행속도가 늦음
- 배우고 한게 아닌 하면서 하이퍼레저패브릭에 대한 감과 개념을 잡게 됨
- 간단하게 form 데이터를 원장으로 담아 하려 했지만 시간 부족으로 넘어감.
- 환경변수설정 등 구조 구축에서 사소한 오류들을 해결하는데 오래 걸림.
