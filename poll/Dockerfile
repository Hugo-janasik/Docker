FROM python

RUN mkdir app/

ADD . /app/

WORKDIR /app/

RUN pip install -r requirements.txt

ENV DB=redis

CMD [ "flask", "run", "--host=0.0.0.0", "--port=80" ]