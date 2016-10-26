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
T## Request ParametersParameter        | Description     | Parameter        | Required | Data Type
----------|----------|--------|----------|------------
**S1**        |String to compare   |Query |Yes  |String
**S2**        |String to compare  | Query |Yes  |String
<br>
Strings should be limited to less than 5000 characters.
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
**Timed out**     | request timed out.  | Error state
<br>

**Text String Example:**
```
https://api.projectoxford.ai/academic/v1.0/similarity?s1=Machine learning is the subfield of computer science that gives computers the ability to learn without being explicitly programmed&s2=Machine learning evolved from the study of pattern recognition and computational learning theory in artificial intelligence

```
In this example, we show that you can input 2 text strings including punctuation marks. The output would be:
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
In this example, we show that you can compare 2 abstract text strings to determine if a certain paper is similar enough to warrant further analysis. Using word embedding and word vectors, the similarity API will assess the similarity of not only words but concepts of the related texts. The output would be:
<br>
**0.650**

