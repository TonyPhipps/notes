Quick run of Docker-based Jupyter notebook sharing the local path D:\Tony\Docker-in\notebook so it appears in the /work folder displayed in Jupyter at launch

```
docker run -p 8888:8888 -v d:/tony/Docker-in/notebook:/home/jovyan/work/notebook jupyter/all-spark-notebook
```

