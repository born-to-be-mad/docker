FROM python:3.8-slim

RUN mkdir -p /usr/src/app/
WORKDIR /usr/src/app

# copy all in root
#COPY . /usr/src/app

COPY requirements.txt /usr/src/app
COPY app.py /usr/src/app

RUN pip install --no-cache-dir -r requirements.txt

# RUN pip install --upgrade pip \
#     &&  pip install --trusted-host pypi.python.org --requirement requirements.txt

#declare that we ezpose this port
EXPOSE 8080

ENV TZ Europe/Minsk
# or we can do the same via parameter while running the container `-e TZ=Europe/Minsk`

# run command which gets executed when running the image
CMD ["python", "app.py"]
#ENTRYPOINT ["python", "app.py"]
