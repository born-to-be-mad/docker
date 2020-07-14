FROM python:3.6

RUN mkdir -p /usr/src/app/
WORKDIR /usr/src/app

COPY . /usr/src/app
RUN pip install --no-cache-dir -r requirements.txt

#declare that we ezpose this port
EXPOSE 8080

ENV TZ Europe/Minsk
# or we can do the same via parameter while running the container `-e TZ=Europe/Minsk`

CMD ["python", "app.py"]
#ENTRYPOINT ["python", "app.py"]
