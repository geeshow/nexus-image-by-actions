# Sonatype Nexus3

## Description
- 본 프로젝트는 Sonatype Nexus3를 AWS EC2에 배포하는 코드기반 구축 템플릿이다.
- CloudFormation을 통해 AWS EC2, S3가 설치되며, EC2의 사용자 데이터로 Nexus3가 설치된다.
- (작업예정) EC2에서는 Code Deploy Agent가 설치되어 있으며, Github Action을 통해 Nexus config 파일이 업데이트 된다.

## Version
- Sonatype/nexus-3.64.0-04

## Requirements
- EC2 t3.small 이상
- S3 버킷
- Github Action

## Deploy steps
1. CloudFormation 파일을 이용하여 AWS 리소스를 생성한다.
- create-ec2.yaml
- create-s3.yaml
2. nexus config 파일을 환경에 맞도록 수정한다.
3. Github Action을 이용하여 nexus를 배포한다.

