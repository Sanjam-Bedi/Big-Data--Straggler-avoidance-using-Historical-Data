# Big-Data--Straggler-avoidance-using-Historical-Data

## Introduction
This project implements a historical data based straggler avoidance technique in a Hadoop cluster with 3 nodes, which include 1 master node and 2 slave nodes. It has been implemented on virtual machine using Virtual Box. The aim of the project is to optimize the performance of the Hadoop cluster by identifying and mitigating stragglers.

## Installation
To use this project, you will need to have the following software installed on your machine:
- Hadoop 3.0 or later
- Python 3.x
- Java-8 or later
## Configuration
1. Before running the project, you will need to configure the Hadoop multinode cluster with 3 nodes to work with the project.
- Modify the hdfs-site.xml and core-site.xml files in the etc/hadoop directory to include the following properties:


- Modify the mapred-site.xml file in the etc/hadoop directory to include the following properties:


- 
