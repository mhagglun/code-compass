# Fork of [code-compass](https://github.com/nokia/code-compass) with focus on the learned embeddings

## Changes
- Added support to search for repositories by topic

The main goal is to extract embeddings for machine learning specific code to investigate the possibility of forming clusters based on the implemented functionality. 

# Import2vec

### What is it?
Import2vec is an unsupervised machine learning model that learns how to cluster similar software packages by their context of use, as determined by how libraries get imported alongside other libraries in large open source codebases.
Software packages are represented as vectors which we call "library vectors" by analogy with [word vectors](https://blog.acolyer.org/2016/04/21/the-amazing-power-of-word-vectors/). Just like [word2vec](https://code.google.com/archive/p/word2vec/) turns words into vectors by analyzing how words co-occur in large text corpora, our "import2vec" turns libraries into vectors by analyzing how import statements co-occur in large codebases.

You can read the details in [here](https://arxiv.org/abs/1904.03990). Supplementary material including trained library embeddings for Java, JavaScript and Python is available on [Zenodo](https://zenodo.org/record/2546488).

### TLDR
As an example, for Java we looked at a large number of open source projects on [GitHub](https://github.com) and libraries on [Maven Central](https://mvnrepository.com/) and studied how libraries are imported across these projects. We identified large clusters of projects related to web frameworks, cloud computing, network services and big data analytics. Well-known projects such as [Apache Hadoop](http://hadoop.apache.org/), [Spark](https://spark.apache.org/) and [Kafka](https://kafka.apache.org/) were all clustered into the same region because they are commonly used together to support big data analytics.

Below is a 3D visualization (a [t-SNE](https://lvdmaaten.github.io/tsne/) plot) of the learned vector space for Java. Each dot represents a Java library and the various colored clusters correspond to different niche areas that were discovered in the data. We highlighted the names of [Apache projects](https://projects-new.apache.org/projects.html).

![3dviz](assets/java_ecosystem_3d_ann.png)

# What's in this repo?

  * `scripts/`: data extraction scripts to generate library import co-occurrences from source code
  * `nbs/`: Jupyter notebooks with TensorFlow models to train library embeddings from import co-occurrence data

# Team

Code Compass is developed by a research team in the [Application Platforms and Software Systems](https://www.bell-labs.com/our-research/areas/applications-and-platforms/) Lab of [Nokia Bell Labs](https://www.bell-labs.com).

# License

BSD3
