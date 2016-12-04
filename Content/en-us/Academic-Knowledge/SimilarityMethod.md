<!-- 
NavPath: Academic Knowledge API
LinkLabel: Similarity Method
Url:Academic-Knowledge-API/documentation/SimilarityMethod
Weight: 75
-->

## Similarity Method

The **similarity** REST API is used to calculate a floating point value based on 2 text inputs. 
<br>
**REST endpoint:**
```
https://api.projectoxford.ai/academic/v1.0/similarity
```
<br>
**GET https://api.projectoxford.ai/academic/v1.0/similarity**
<br>
**POST https://api.projectoxford.ai/academic/v1.0/similarity**
<br>
For get requests, the parameters should be passed as a URL parameter.  For post requests, the parameters should be passed in the body of the request.
<br>
## Request Parameters
Parameter        |Data Type      |Required | Description
----------|----------|----------|------------
**S1**        |String   |Yes  |Input String 1
**S2**        |String   |Yes  |Input String 2
<br>
**Input strings have limits of roughly 1300 (1294) english characters.**
<br>

## Response (Floating Point Value)
Name | Description
--------|---------
**SimilarityValue**        |The floating point value representing the cosine similarity of the text inputs of S1 and S2. The output is represented by a floating point between -1.0 and +1.0. A value like 0.936232342343 represents a high degree of similarity where as a value like -0.7893935 represents a low degree of similarity. 
<br>

## Success/Error Conditions
HTTP Status | Reason | Response
-----------|----------|--------
**200**         |Success | floating point number
**400**         | Bad request or request invalid | Error Message      
**500**         |Internal server error | Error Message
**Timed out**     | request timed out.  | Error state
<br>

**Text String Example:**
```
https://api.projectoxford.ai/academic/v1.0/similarity?s1=Machine learning is the subfield of computer science that gives computers the ability to learn without being explicitly programmed&s2=Machine learning evolved from the study of pattern recognition and computational learning theory in artificial intelligence

```
In this example, 2 parameters are passed into the **similarity** API. The parameters S1 and S2 represent two strings that are being compared respectively.
The response to this request indicates the similarity between S1 and S2 is:
<br>
**0.737**
<br>

**Abstract Comparison Example:**

```

https://api.projectoxford.ai/academic/v1.0/similarity?s1=Using complementary priors, we derive a fast greedy
algorithm that can learn deep directed belief networks one layer at a time
provided the top two layers form an undirected associative memory&s2=Deep
neural nets with a large number of parameters are very powerful machine
learning systems. However, overfitting is a serious problem in such networks

```
In this example, abstract of 2 different papers are passed in as parameters to the **similarity** API. Using word embedding and word vectors, the similarity API assesses the **similarity** of the abstracts. By comparing not only the texts, but the concepts of the related texts, the **similarity** API gives a result of:
<br>
**0.650**

Microsoft receives the text you provide and may use these submissions to improve the Similarity API and related services. By submitting a text, you confirm that you have followed our Developer Code of Conduct at https://research.microsoft.com/en-us/UM/legal/DeveloperCodeofConductforCognitiveServices.htm.
