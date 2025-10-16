## 🧭 Use Docker Compose (multi-service cluster)

If you want a **pseudo-distributed cluster**, you can use the prebuilt setup:

```bash
git clone https://github.com/justudin/docker-hadoop/docker-hadoop
cd docker-hadoop
docker-compose up -d
```
Then follow the steps:

```bash
docker exec -it namenode bash
```

## 📁 4. Prepare Input Data

Create a local text file, e.g. `input.txt`:

```bash
echo "Hadoop is fast Hadoop is scalable Hadoop is reliable" > input.txt
```

Now upload it to HDFS:

```bash
hdfs dfs -mkdir -p /input
hdfs dfs -put input.txt /input/
```

Verify:

```bash
hdfs dfs -ls /input
```

---

## 🧠 5. Run the WordCount Example

Run the example JAR provided by Hadoop:

```bash
hadoop jar /opt/hadoop-3.2.1/share/hadoop/mapreduce/hadoop-mapreduce-examples-3.2.1.jar wordcount /input /output
```

---

## 📤 6. Check the Output

Once the job finishes:

```bash
hdfs dfs -ls /output
hdfs dfs -cat /output/part-r-00000
```

Expected output:

```
Hadoop 3
fast    1
is      3
reliable 1
scalable 1
```

---
