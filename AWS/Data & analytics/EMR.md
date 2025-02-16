Elastic MapReduce - its for HADOOP, APACHE SPARK

EMR is for creating **Hadoop clusters** which can have 100s of EC2 to analyze and process big data.
EMR comes with Apache spark, HBase, Presto...
Auto scales and can use **spot-instances** to save cost.
Use case:
- Machine learning
- Big data processing

**Node types**
EMR clusters consist of nodes.
- Master node - manages the cluster - long running
- Core node - Run tasks/store data - long running
- Task node - Just to run small tasks - ususally spot instances

Purchase options:
- On-demand (standard EC2)
- Reserved (like reserved instance EC2)
- Spot instances - cheapest

You can create long running or transient clusters.