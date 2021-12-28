# Spark Study

## Environments

- 환경 설정하기

```sh
# pyenv
pyenv virtualenv spark-env
pyenv activate spark-env
pip install -r requirements.txt
```

- Spark 다운로드 후 아래 커맨드로 전역 설치

```sh
tar -xzf spark-3.1.2-bin-hadoop3.2.tgz
sudo mv spark-3.1.2-bin-hadoop3.2 /opt/spark-3.1.2
sudo ln -s /opt/spark-3.1.2 /opt/spark
```

### Notebook에서 PySpark 실행하기

- `vi ~/.zshrc` 로 연 다음 아래 내용 기입, `source ~/.zshrc`로 적용

```sh
# Spark
export SPARK_HOME="/opt/spark"
export PATH=$SPARK_HOME/bin:$PATH
export SPARK_LOCAL_IP='127.0.0.1'

# Pyspark
export PYSPARK_DRIVER_PYTHON=jupyter # How to rollback: $unset PYSPARK_DRIVER_PYTHON
export PYSPARK_DRIVER_PYTHON_OPTS='notebook'
export PYSPARK_PYTHON=python3
```

### Spark Submit

- `unset PYSPARK_DRIVER_PYTHON` 으로 jupyter 연결 끊기

```sh
spark-submit --master local ./spark-3.1.2-bin-hadoop3.2/examples/src/main/python/pi.py 10
```

### 교재 파일 받기 (submodule)

```sh
git submodule update --init --recursive
```