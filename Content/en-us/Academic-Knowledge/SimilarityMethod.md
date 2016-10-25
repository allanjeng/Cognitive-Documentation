<!-- 
NavPath: Academic Knowledge API
LinkLabel: Similarity Method
Url:Academic-Knowledge-API/documentation/SimilarityMethod
Weight: 75
-->

# Similarity Method

The **similarity** REST API is used to
calculate a floating point value based on 2 text inputs. 

**REST endpoint:**

```
https://api.projectoxford.ai/academic/v1.0/similarity?

``` 
<br>

**GET http://academic-api-similarity.cloudapp.net/api/similarity**
<br>

## Request Parameters
Parameter        | Description     | Parameter        | Required? | Data Type
-----------|----------|--------|----------|------------
**S1**        |String to compare   |Query |yes  |String
**S2**        |String to compare  | Query |yes  |String
<br>

## Response (Floating Point Value)
Name | Description
--------|---------
**SimilarityValue**        |The floating point value representing the cosine similarity of the text inputs of S1 and S2. The output will be a floating point between -1.0 and +1.0. Example is 0.936232342343 representing a high degree of similarity or -0.7893935 representing a low degree of similarity. 
<br>

## Success/Error Conditions
HTTP Status | Reason | Response
-----------|----------|--------
**200**         |Success | floating point number
**400**         | Bad request or request invalid | Error Message      
**500**         |Internal server error | Error Message
**aborted**     | true if request timed out.  | Error state
<br>

**Text String Example:**
```
https://api.projectoxford.ai/academic/v1.0/similarity?s1=this text similarity api is really, really cool&s2=this
text similarity api is really, really awesome

```
In this example, we show that you can input 2 text strings including punctuation marks. 
<br>
Here is the output:
<br>
**Similarity probability: 0.92379162279743876**
<br>

**Abstract Comparison Example:**

```

https://api.projectoxford.ai/academic/v1.0/similarity?s1=Using complementary priors, we derive a fast greedy
algorithm that can learn deep directed belief networks one layer at a time
provided the top two layers form an undirected associative memory&s2=Deep
neural nets with a large number of parameters are very powerful machine
learning systems. However, overfitting is a serious problem in such networks

```
In this example, we show that you can compare 2 abstract text strings to determine if a certain paper is similar enough to warrant further analysis. Using word embedding and word vectors, the similarity API will assess the similarity of not only words but concepts of the related texts.
<br>
Here is the output:
<br>
**Similarity Probability: 0.65028525870666865**

<br>

**Full Paper Example:**

```

https://api.projectoxford.ai/academic/v1.0/similarity?s1=Information networks, containing a large number of individual agents or components interacting with each other, are ubiquitous in many applications, e.g., the Internet that consists of a gigantic network of webpages, co-author networks and citation networks extracted from bibliographic data, user networks extracted from email systems, and friendship network extracted from web sites like Facebook1 and Myspace2. Clustering on an information network based on links between objects may give us a grand view of the huge network. For example, communities can be detected by clustering on co-author network [11]. Most current studies [20, 17, 19, 21] on information network are on homogeneous networks, i.e., networks consisting of single type of objects, as shown above. However, in reality, objects could be of multiple types, forming a heterogeneous network. A recent algorithm RankClus [16] deals with bi-typed heterogeneous networks. Unfortunately, in reality there often exists more than two types of interacting objects in a network. Among them, networks with star network schema (called star network) such as bibliographic network centered with papers and tagging network (e.g., http://delicious.com) centered with a tagging event are popular and important. In fact, any n-nary relation set such as records in a relational database can be mapped into a star network, with each relation as the center object and all attribute entities linking to it. Example 1.1 (Bibliographic Information Network) A bibliographic network consists of rich information about research papers, each written by a group of authors, using a set of terms, and published in a venue (a conference
or a journal). Such a bibliographic network is composed of four types of objects: authors, venues, terms, and papers. Links exist between papers and authors by the relation of “write” and “written by”, between papers and terms by the relation of “contain” and “contained in”, between papers and venues by the relation of “publish” and “published by”. The topological structure of a bibliographic network is shown in the left part of Figure 1, which forms a star network schema&S2=Networks are a natural way to represent social [20], biological [23], technological [16], and information [8] systems.  Nodes in such networks organize into densely linked groups that are commonly referred to as network communities, clusters or modules [11]. There are many reasons why nodes in networks organize into densely linked clusters. For example, society is organized into social groups, families, villages and associations [7], [12]. On the World Wide Web, topically related pages link more densely among themselves [8]. And, in metabolic networks, densely
linked clusters of nodes are related to functional units, such as pathways and cycles [23].  To extract communities from a given undirected network, one typically chooses a scoring function (e.g., modularity) that quantifies the intuition that communities correspond to densely linked sets of nodes. Then one applies a procedure to  This paper has been published in the Proceedings of 2012 IEEE International Conference on Data Mining (ICDM), 2012. find sets of nodes with a high value of the scoring function. Identifying such communities in networks [14], [6], [26], [9] has proven to be a challenging task [10], [18], [17] due to three reasons: There exist multiple structural definitions of network communities [5], [24]; Even if we would agree on a single common structural
definition (i.e., a single scoring function), the formalizations of community detection lead to NP-hard problems [26]; And, the lack of reliable groundtruth makes evaluation extremely difficult.  Currently the performance of community detection methods is evaluated by
manual inspection. For each detected community an effort is made to interpret it as a “real” community by identifying a common property or external attribute shared by all the members of the community. For example, when examining communities in a scientific collaboration network, we might by manual inspection discover that many of detected communities correspond to groups of scientists working in common areas of science [22]. Such anecdotal evaluation procedures require extensive manual effort, are non-comprehensive and limited to small networks

``` 

<br>

**Sample Output**
<br>
{
<br>
"TextInput1": "deep learning",
<br>
"TextInput2": "machine learning",
<br>
"SimilarityVale": 
<br>
  [
<br>
      {
<br>
      "logprob": 0.65427660684878586,
<br>
      },
<br>
  ]
<br>
}
<br>
...
