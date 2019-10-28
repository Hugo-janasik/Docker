FROM python

RUN mkdir app/

ADD . /app/

WORKDIR /app/

RUN pip install -r requirements.txt

#ENV DB=redis
EXPOSE 80

CMD [ "flask", "run", "--host=0.0.0.0", "--port=80" ]