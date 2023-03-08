FROM python:3
COPY  requirements.txt ./
WORKDIR  /Applications/desktop/docker/test 
RUN pip install -r requirements.txt
CMD ["java", "Main"]
EXPOSE 8001