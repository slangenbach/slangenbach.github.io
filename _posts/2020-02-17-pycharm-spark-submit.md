# Using spark-submit with Spark on YARN via PyCharm

My favourite IDE for Python development is [PyCharm](https://www.jetbrains.com/pycharm/). It offers so many great features that make Python development convenient, efficient and fun, that I do not know which one to list first.  The *professional* version pf PyCharm offers one particular feature I do enjoy when developing [PySpark](http://spark.apache.org/docs/latest/api/python/index.html) applications at work: [Remote interpreters](https://www.jetbrains.com/help/pycharm/configuring-remote-interpreters-via-ssh.html).  

Using remote interpreters, I can use PyCharm on my local development machine, connect to the Hadoop Edge Node via SSH and use its Python interpreter to develop my PySpark application. While developing the application works just fine, I ran into a problem when trying to submit it to Spark using `spark-submit`. The command `spark-submit --master yarn </path/to/my/pyspark_app.py` failed with the following error: `Error: Unrecognized option: -u`.

Searching Google for *"spark-submit pycharm"* I found lots of tutorials on how to set up Spark **locally**, but not an obvious solution to problem. If you are lucky enough to spot [one](https://intellij-support.jetbrains.com/hc/en-us/community/posts/360006925440-How-to-remove-u-when-running-python-script-?page=1#community_comment_360001275260) of [two posts on the JetBrains support forum](https://intellij-support.jetbrains.com/hc/en-us/community/posts/360000044644-PyCharm-remove-python-u-option-with-remote-interpreter) referring to a similar issue, follow a link to [JetBrains issue tracker](https://youtrack.jetbrains.com/issue/PY-28339) and read through the comments, you will eventually find a **suitable workaround**, but **not a solution** (at the time of writing, the ticket had been open for 2 years while still being unresolved). 

In order to spare you going down the Google search rabbit hole, take a shortcut and follow the instructions below:
1. Create the file `custom_spark_submit.sh` with the following content 
```bash
#!/bin/sh

for arg do
    shift
    [[ "$arg" = "-u" ]] && continue
    set -- "$@" "$arg"
done

# replace <path/to/spark-submit> with your actual path
exec <path/to/spark-submit> --master yarn $@
```
2. Copy `custom_spark_submit.sh` to your Edge Node (you may want do so via [deployment server configuration](https://www.jetbrains.com/help/pycharm/creating-a-remote-server-configuration.html) in PyCharm)
3. Make the file executable via `chmod +x custom_spark_submit.sh`
4. Set `custom_spark_submit.sh` as your [remote Python interpreter](https://www.jetbrains.com/help/pycharm/configuring-remote-interpreters-via-ssh.html)
5. Enjoy submitting PySpark applications to Spark on YARN via PyCharm :bowtie:

