docker run -d \
  --name localstack \
  -p 4566:4566 \
  -p 4510-4559:4510-4559 \
  localstack/localstack

docker-compose up -d

aws configure


AWS Access Key ID: test
AWS Secret Access Key: test
Default region name: us-east-1
Default output format: json

# Cria
aws --endpoint-url=http://localhost:4566 s3 mb s3://meu-bucket-local

# Lista
aws --endpoint-url=http://localhost:4566 s3 ls

# Envia
aws --endpoint-url=http://localhost:4566 s3 cp arquivo.txt s3://meu-bucket-local/


# init-s3.sh cria quando subir o docker
'''#!/bin/bash
awslocal s3 mb s3://meu-bucket-local'''

Montar volume no docker-compose.yml 
volumes:
  - ./init-s3.sh:/etc/localstack/init/ready.d/init-s3.sh


