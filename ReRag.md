**Dynamic Document Retrieval in Retrieval Augmented Generation (RAG) Models**

1. **Introduction**
   
   Retrieval Augmented Generation (RAG) models have become prominent due to their capability to harness non-parametric knowledge and demonstrate adaptability in few-shot learning. Such models work by fetching pertinent information based on a query and then employing the extracted documents to produce a response. One challenge with this approach is the potential for the document matches to become obsolete by the conclusion of the response.

2. **The Proposed Solution**
   
   The core proposition is to implement a dynamic retrieval system wherein the document queries are refreshed once the relevance of the current query encoding descends beneath a designated threshold in relation to the document encoding matches. This ensures that the response generation is informed by up-to-date and pertinent documents throughout its entire course.
   
   - **Illustrative Example**: Consider a multi-step query like:
     - Who painted the "Mona Lisa"?
     - In which city was this artist born?
     - This city is situated along which river?
     - This river flows into which larger body of water?
     - Name another major European city that sits along this body of water.

     Response: (Leonardo da Vinci painted the "Mona Lisa")[1]. He was (born in the city of Vinci)[2]. Vinci is (situated along the Arno River)[3]. (The Arno drains into the Tyrrhenian Sea)[4]. (Genoa is another major European city along this sea)[5].

     Here, after addressing each component of the query, the document retrieval system refreshes to fetch relevant data for the subsequent query component.

3. **Training Mechanism**
   
   - The fine-tuning approach is reminiscent of the Atlas methodology, as described in [Atlas](https://arxiv.org/pdf/2208.03299.pdf). The key distinction lies in sourcing distinct documents during different stages of response formation, which is particularly advantageous for queries demanding discrete pieces of information.
   
   - Training can be optimized by sectioning the target response and pre-calculating requisite query-document pairings. Such a method not only guarantees accuracy but also permits massive parallelization, which is indispensable when working with transformer models.

---

In summary, the proposed dynamic document retrieval mechanism within RAG models seeks to address the concern of outdated or irrelevant document matches during response generation. By refreshing the document matches based on query relevance thresholds and optimizing the training process, it offers a more adaptive and efficient solution for complex, knowledge-rich queries.