## Study

### Spark Cluster creation
#### scenario 1 - manual creation by Azure HDInsight
- result: :x:

- issue 1: **access denied**

it seems due to the lack of access right for Gen 2 storage,
by granting the right access role, the error is fixed.

FIX:    You need to follow these [steps](https://docs.microsoft.com/en-us/azure/hdinsight/hdinsight-hadoop-use-data-lake-storage-gen2?toc=%2Fen-us%2Fazure%2Fhdinsight%2Fspark%2FTOC.json&bc=%2Fen-us%2Fazure%2Fbread%2Ftoc.json) to avoid this issue.

- issue 2: **ClassNotFoundException**
Got http 500 error, here is jupyter's log:

```
[E 2019-03-03 06:04:02.305 NotebookApp] Uncaught exception GET /tree (10.0.0.21)
    HTTPServerRequest(protocol='http', host='hn0-testku.ljpo3xpqnm2ezpqj1spvc1brye.ax.internal.cloudapp.net:8001', method='GET', uri='/tree', version='HTTP/1.1', remote_ip='10.0.0.21', headers={'Accept-Language': 'fr,en;q=0.9,zh-CN;q=0.8,zh;q=0.7,zh-TW;q=0.6', 'Cookie': 'AMBARISESSIONID=9e8jy8758anf1u1jctizobb6h', 'X-Hdi-Rm-Host': 'hn1-testku.ljpo3xpqnm2ezpqj1spvc1brye.ax.internal.cloudapp.net', 'Authorization': 'Basic YWRtaW46TXlhMjAxMjEwMjEs', 'X-Hdi-Hs2-Endpoint': 'hn0-testku.ljpo3xpqnm2ezpqj1spvc1brye.ax.internal.cloudapp.net', 'X-Secure-Hdi-Host': '', 'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_0) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.109 Safari/537.36', 'Host': 'hn0-testku.ljpo3xpqnm2ezpqj1spvc1brye.ax.internal.cloudapp.net:8001', 'X-Hdi-Edge-Host': '', 'Referer': 'https://portal.azure.com/', 'X-Original-Url': '/jupyter/tree', 'X-Hdi-Fc-Host': 'hn0-testku.ljpo3xpqnm2ezpqj1spvc1brye.ax.internal.cloudapp.net', 'X-Hdi-Hs2-Enabled': 'false', 'Connection': 'Keep-Alive', 'X-Original-Host': 'testkun.azurehdinsight.net', 'Max-Forwards': '10', 'Sec-Websocket-Extensions': '', 'X-Forwarded-For': '90.9.247.42:62738', 'X-Arr-Log-Id': 'd0e32483-e3a6-4ea4-8ece-efec07be4b77', 'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8', 'Upgrade-Insecure-Requests': '1', 'X-Arr-Ssl': '2048|256|C=US, S=Washington, L=Redmond, O=Microsoft Corporation, OU=Microsoft IT, CN=Microsoft IT TLS CA 2|CN=*.azurehdinsight.net', 'X-Original-Https-Scheme': 'on', 'X-Hdi-Host': 'hn0-testku.ljpo3xpqnm2ezpqj1spvc1brye.ax.internal.cloudapp.net'})
    Traceback (most recent call last):
      File "/usr/bin/anaconda/lib/python2.7/site-packages/tornado/web.py", line 1467, in _execute
        result = method(*self.path_args, **self.path_kwargs)
      File "/usr/bin/anaconda/lib/python2.7/site-packages/tornado/web.py", line 2829, in wrapper
        return method(self, *args, **kwargs)
      File "/usr/bin/anaconda/lib/python2.7/site-packages/notebook/tree/handlers.py", line 40, in get
        if cm.dir_exists(path=path):
      File "/var/lib/.jupyter/jupyterazure/jupyterazure/httpfscontentsmanager.py", line 42, in dir_exists
        return self._webhdfs_exists(path, 'DIRECTORY')
      File "/var/lib/.jupyter/jupyterazure/jupyterazure/httpfscontentsmanager.py", line 115, in _webhdfs_exists
        file_status = self.httpFSClient.get_file_dir_status(self._make_webhdfs_path(path))
      File "/usr/bin/anaconda/lib/python2.7/site-packages/pywebhdfs/webhdfs.py", line 361, in get_file_dir_status
        _raise_pywebhdfs_exception(response.status_code, response.content)
      File "/usr/bin/anaconda/lib/python2.7/site-packages/pywebhdfs/webhdfs.py", line 722, in _raise_pywebhdfs_exception
        raise errors.PyWebHdfsException(msg=message)
    PyWebHdfsException: {"RemoteException":{"message":"java.lang.ClassNotFoundException: Class org.apache.hadoop.fs.azurebfs.AzureBlobFileSystem not found","exception":"RuntimeException","javaClassName":"java.lang.RuntimeException"}}
```
FIX:    better to wait at least 25 mins for creation of cluster. 



