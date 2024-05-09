--------------------
Name: Lok Yee Joey CHEUNG
SID:47633542
--------------------

Folders: 

`MLlib`: To be uploaded to GCP VM, contains docker-compose file (docker-compose_hdfs_spark.yml), Hadoop environment file (hadoop.env) and a nbs folder 

`MLlib/nbs`: Two datasets (train.csv, test.csv), jupyter notebook for spark implementation (47633542.ipynb)


---------------------
Commands Submission
---------------------

1. Upload MLlib zip file and unzip it 
unzip MLlib.zip

2. Create and change directory to proj 
mkdir $HOME/proj && cd $HOME/proj

3. Move folder to proj directory
mv $HOME/MLlib/* $HOME/proj/


4. Run the docker-compose file to pull images and run all containers
sudo docker-compose -f docker-compose_hdfs_spark.yml up -d


5. Find the container id of the namenode
sudo docker ps


6. Log into the namenode container 
sudo docker exec -it container_id bash


7. Transfer local files from nbs folder to HDFS
hdfs dfs -put /home/nbs/train.csv /
hdfs dfs -put /home/nbs/test.csv /


8. Display all directories and files to check if transfer is successful 
hdfs dfs -ls /


9. Exit the namenode 
exit


10. (Optional) Set permission 
sudo chmod -R 777 $HOME/proj/nbs

11. Go to EXTERNAL_IP:8888 to access jupyter notebook