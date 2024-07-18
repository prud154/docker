FROM python:3.11
LABEL app="BOTO3 with FastAPI"
MAINTAINER author="sreeharshav@gmail.com"
ENV AWS_ACCESS_KEY_ID=SAMPLEKEYID
ENV AWS_SECRET_ACCESS_KEY=SAMEPLSECRETKEY
WORKDIR /code
COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir --upgrade -r requirements.txt \
    && python --version && apt update && apt install -y unzip 
COPY main.py main.py
ADD Instructions.info Instructions.txt
ARG T_VERSION=1.7.4
ADD https://releases.hashicorp.com/terraform/${T_VERSION}/terraform_${T_VERSION}_linux_amd64.zip terraform.zip
RUN unzip terraform.zip -d /usr/local/bin && terraform version
EXPOSE 80
#CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "80"]
ENTRYPOINT ["uvicorn", "main:app", "--host", "0.0.0.0"]
CMD ["--port", "80"]


#If you get a bookwork security issue pefrom the following steps
#docker system prune -a
