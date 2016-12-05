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

**Abstract Comparison Example:**

To use the **similarity** API through an HTTP interface, requests are constructed as URL strings that contains 2 parameters s1 and s2.

The following example requests the similarity between 2 papers:
```
https://api.projectoxford.ai/academic/v1.0/similarity?s1=Using complementary priors, we derive a fast greedy
algorithm that can learn deep directed belief networks one layer at a time
provided the top two layers form an undirected associative memory&s2=Deep
neural nets with a large number of parameters are very powerful machine
learning systems. However, overfitting is a serious problem in such networks
```
<br>

In this example, abstract of 2 different papers, string 1 (s1) and string 2 (s2), are passed in as parameters to the **similarity** API. Using word embedding and word vectors, the **similarity** API assesses the abstracts. By comparing not only the texts, but the concepts of the related texts, the **similarity** API returns a result of:
```
0.650
```
<br>

Microsoft receives the text you provide and may use these submissions to improve the Similarity API and related services. By submitting a text, you confirm that you have followed our Developer Code of Conduct at https://research.microsoft.com/en-us/UM/legal/DeveloperCodeofConductforCognitiveServices.htm.
