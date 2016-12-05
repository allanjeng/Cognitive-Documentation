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
<br>
**GET**
```
https://api.projectoxford.ai/academic/v1.0/similarity?
```
**POST**
```
https://api.projectoxford.ai/academic/v1.0/similarity?
```
\*GET request's input length is bounded by the limitation of the length of URL. When the strings are too long to be processed using GET, use POST instead.
<br>
\*To use POST, one option is to create a HTML page with POST request in a form, then open it with a browser. Another option is to use a plug-in that sends POST requests, and set content-type to x-www-form-urlencoded, with key-value-pairs s1 and s2.
<br>

## Request Parameters
Parameter        |Data Type      |Required | Description
----------|----------|----------|------------
**s1**        |String   |Yes  |String to be compared
**s2**        |String   |Yes  |String to be compared
\*POST request has a limitation of 1MB.
<br>
## Response (Floating Point Value)
Name | Description
--------|---------
**SimilarityValue**        |The floating point value representing the cosine similarity of the text inputs of S1 and S2. The output is represented by a floating point between -1.0 and +1.0. The **similarity** API evaluates the strings base on their academic concepts, with +1.0 being the most similar and -1.0 being the most different.
<br>

## Success/Error Conditions
HTTP Status | Reason | Response
-----------|----------|--------
**200**         |Success | floating point number
**400**         | Bad request or request invalid | Error Message      
**500**         |Internal server error | Error Message
**Timed out**     | request timed out.  | Error state
<br>

**Example:**
```
https://api.projectoxford.ai/academic/v1.0/similarity?s1=Using complementary priors, we derive a fast greedyalgorithm that can learn deep directed belief networks one layer at a timeprovided the top two layers form an undirected associative memory&s2=Deepneural nets with a large number of parameters are very powerful machinelearning systems. However, overfitting is a serious problem in such networks
```
In this example, abstracts of 2 different papers are passed in as parameters s1 and s2 to the **similarity** API. The **similarity** API returns a result of:
```
0.520
```
By using word embedding and word vectors, the **similarity** API assesses the abstracts based on not only the texts, but the academic concepts of the related texts. 
<br>
<br>
<br>
<br>

*Microsoft receives the text you provide and may use these submissions to improve the Similarity API and related services. By submitting a text, you confirm that you have followed our Developer Code of Conduct at https://research.microsoft.com/en-us/UM/legal/DeveloperCodeofConductforCognitiveServices.htm.
