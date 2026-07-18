# minio docker run

docker run -d \
  --name minio \
  -p 9000:9000 \
  -p 9001:9001 \
  -e MINIO_ROOT_USER=minioadmin \
  -e MINIO_ROOT_PASSWORD=minioadmin123 \
  -v ~/minio/data:/data \
  quay.io/minio/minio server /data --console-address ":9001"

  # export minio access keys
  
  export AWS_SECRET_ACCESS_KEY=xxxx
  export AWS_ACCESS_KEY_ID=xxxx
  
  # dvc install
  
  python -m pip install "dvc[s3]"

  # dvc init
  
  dvc init
  
  # dvc config set
  
  dvc remote add -d minio s3://mlops   #(from local minio)
  dvc remote modify minio endpointurl http://localhost:9000

  # dvc congig list 
  
  dvc config --list
# dvc commands like git 
  dvc add data/churn_data.csv
  dvc status
  dvc push -v


  
