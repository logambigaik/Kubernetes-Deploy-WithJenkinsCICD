FROM python:slim
WORKDIR /app
EXPOSE 8000
COPY /Kubernetes-Deploy-WithJenkinsCICD/python/requirements.txt requirements.txt
COPY /Kubernetes-Deploy-WithJenkinsCICD/python/app.py app.py
RUN pip3 install -r requirements.txt
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]
