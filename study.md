## Study

### Spark Cluster creation
#### scenario 1 - manual creation by Azure HDInsight
- result: :x:

- issue 1: **access denied**

it seems due to the lack of access right for Gen 2 storage,
by granting the right access role, the error is fixed.
You need to follow these steps to avoid this issue:
https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2?toc=%2Fen-us%2Fazure%2Fhdinsight%2Fspark%2FTOC.json&bc=%2Fen-us%2Fazure%2Fbread%2Ftoc.json

- issue 2: **ClassNotFoundException**

The WebHDFS could not be accessed by Jupyter
