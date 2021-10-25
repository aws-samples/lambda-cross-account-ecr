TAG ?= 01
NAME = cross-account-function

REGION = us-east-1
ACCOUNT_ID ?= 111111111111


build :
	docker build -t ${NAME}:${TAG} .
.PHONY: build

deploy : tag push
	echo ${NAME}:${TAG}
.PHONY: deploy

tag :
	docker tag ${NAME}:${TAG} ${ACCOUNT_ID}.dkr.ecr.${REGION}.amazonaws.com/${NAME}:${TAG}
.PHONY: push

push :
	docker push ${ACCOUNT_ID}.dkr.ecr.${REGION}.amazonaws.com/${NAME}:${TAG}
.PHONY: push

login :
	aws ecr get-login-password --region ${REGION} | docker login --username AWS --password-stdin ${ACCOUNT_ID}.dkr.ecr.${REGION}.amazonaws.com
.PHONY: login
