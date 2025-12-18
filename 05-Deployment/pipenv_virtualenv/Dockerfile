FROM python:3.8.12-slim

RUN pip install \
    flask \
    numpy==1.23.5 \
    scikit-learn==1.2.2

WORKDIR /app
COPY Pipfile Pipfile.lock ./
COPY predict.py model_C=1.0.bin ./

EXPOSE 9696

ENTRYPOINT ["gunicorn", "--bind=0.0.0.0:9696", "predict:app"]

# build this Dockerfile with command: docker build -t predict-test .
# then we can run container with command: docker run -it --rm --entrypoint=bash predict-test / docker run -it --rm -p 9696:9696 predict-test
