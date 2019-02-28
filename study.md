## Study

### Spark Cluster creation
#### scenario 1 - manual creation by Azure HDInsight
- result: KO
- issue 1: access denied 
it seems due to the lack of access right for Gen 2 storage,
by granting the right access role, the error is fixed
- issue 2: ClassNotFoundException
The WebHDFS could not be accessed by Jupyter
