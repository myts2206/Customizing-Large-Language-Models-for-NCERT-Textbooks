# Customizing-Large-Language-Models-for-NCERT-Textbooks and Development of Interface which works Offline
## __Overview__
Offline Language Models (LLMs) as a solution designed for pupils with restricted internet access. Our approach combines the National Council of Educational Research and Training (NCERT) dataset for foundational knowledge and straightforward answers with the Question Answering Dataset to encourage critical thinking. The model training prioritizes simplicity for NCERT-based content, delivering concise responses to straightforward queries. Simultaneously, question answer dataset integration prompts the model to provide nuanced responses; fostering out-of-the-box thinking. This paper details the methodology, encompassing pre-processing, model architecture, and evaluation metrics. Preliminary results indicate the model's effectiveness in delivering both fundamental and advanced conceptual understanding. The proposed Offline LLMs strive for inclusivity, ensuring all students benefit from tailored language models, irrespective of internet connectivity. This research lays the foundation for a more equitable education system by making sophisticated learning tools accessible to all.


<img src="Images/FrontPage.jpeg" alt="Alt text" width="200" /> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="Images/OfflineLLM.jpeg" alt="Alt text" width="200" />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="Images/Flashcards.jpeg" alt="Alt text" width="200" />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="Images/Games.jpeg" alt="Alt text" width="200" />

__Images of Front Page__ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__Chatbot which works offline__&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__Flashcards__&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__Game page__








For many students, poor internet connectivity is a major barrier in the world of digital education. In order to close this gap, our research supports the creation of offline language models, or LLMs, designed especially for people without internet connection. Our strategy serves a range of learning demands by utilizing essential dataset: the National Council of Educational Research and Training (NCERT) for foundational knowledge. With user-friendliness as their first priority, the   models employ data from the NCERT dataset to provide accurate and understandable information for basic education—a vital resource in situations where internet availability is erratic.. With this method, advanced language models can now be accessed by everyone, regardless of internet connectivity limitations, potentially transforming education.

## 1. __Data Extraction__
   The first step in our research was data extraction, a crucial process that laid the foundation for our model's learning. We focused on NCERT textbooks, a rich source of structured and reliable educational content.

Our extraction process involved scanning each chapter from the textbooks. This was not simply replicating content, but rather a meticulous curation of pertinent information to form the foundation of our question-answer pairs. The extraction process involved a blend of manual examination and automated tools to achieve a harmony between swiftness and precision. The outcome yielded a thorough dataset, prepared for use in training our model. This procedure encountered its share of difficulties. The textbooks varied in format and complexity, requiring us to adapt our extraction methods accordingly. However, with each challenge overcome, our dataset grew richer and more diverse, paving the way for a robust and versatile learning language model.
Data preprocessing serves as the foundation for building robust machine learning models. In our project, we employ several preprocessing techniques to clean and prepare the raw data. This involves tokenization, stemming, and elimination of stop words for textual data, alongside scaling and normalization for numerical characteristics. One of the primary equations employed in text preprocessing is the TF-IDF formula:

 TF-IDF(t,d)=tf(t,d)×idf(t)TF-IDF(t,d)=tf(t,d)×idf(t)
 
where tf(t,d) represents the term frequency of term in document d, and idf(t) represents the inverse  document frequency of term t across the entire corpus.


## 2. __GPT-Generated Question-Answer Pair__
   In our pursuit to establish an extensive knowledge foundation for our model, we leveraged the capabilities of Generative Pretrained Transformer (GPT) models. The GPT models were provided with data sourced from NCERT textbooks, which they utilized to produce question-answer pairs. This approach was instrumental in creating a diverse and expansive set of potential questions and answers. It allowed us to simulate a wide array of possible queries that a student might have while studying the textbook content. The GPT models demonstrated the capacity to formulate inquiries that explored diverse facets of the content, spanning from straightforward factual inquiries to intricate analytical questions. Moreover, the answers generated by the GPT models were not just restricted to the explicit content of the textbooks. Additionally, they encompassed deductions and associations derived from the models thorough training across a broad spectrum of texts. This enriched the learning base of our model, making it capable of handling a broader range of student queries.

In essence, the GPT-generated question-answer pairs served as a robust training set, preparing our model to respond effectively to the diverse and dynamic needs of learners. In the next section, we will discuss how we ensured the precision of our model’s responses through textbook-restricted answer generation.

## 3. __Textbook-Restricted Question-Answer Pairs__
  While the GPT-generated question-answer pairs provided a broad knowledge base, we aimed to ensure the precision of our model’s responses. To achieve this, we implemented a textbook-restricted answer generation approach. In this approach, we fed the questions from the NCERT textbooks into the GPT model Nevertheless; we constrained the model's responses to information strictly drawn from the content of the textbooks. This ensured that the generated answers were not only accurate and relevant but also strictly adhered to the NCERT curriculum.	By confining the generation of answers to the content within the textbooks, we upheld the integrity of the educational material. This approach ensured that the answers provided by our model were reliable and could be cross-verified with the textbook content. Furthermore, this approach enabled us to manage the extent of the model's responses, mitigating the risk of it producing answers that could be accurate in a broader context but not applicable within the confines of the particular textbook.	
The methodology of generating answers confined to the textbook content was pivotal in guaranteeing the accuracy and dependability of our model's responses, rendering it an invaluable resource for students engaging with the NCERT curriculum. In the subsequent section, we will delve into the evolution and training of our model.

## 4. __Model Selection__
   The selection of a suitable model constituted a critical aspect of our investigation. The chosen model needed to be both compact in size and proficient in producing relevant answers aligned with the NCERT syllabus. We conducted an assessment of several models, each presenting distinctive merits and drawbacks. Our main emphasis was on models demonstrating potential in the realm of question-answer generation, such as:

DistilBERT: DistilBERT is a compact version of BERT, comprising 66 million parameters, which is 40% fewer than BERT-base. It is engineered to be smaller, faster, and lighter, while still maintaining a high level of performance. This makes it an optimal choice for our use case, where we require a balance between model size and performance.
ALBERT (lite): ALBERT is a streamlined version of BERT that employs parameter-reduction techniques to decrease memory usage and enhance training speed. The base version of ALBERT has 12 million parameters, and the large version has 18 million parameters. Its smaller size renders it suitable for our task of generating NCERT answers.
Electra-Small: Electra-Small is a more efficient, smaller variant of the ELECTRA model. It employs an innovative pretraining approach that trains two transformer models: the generator and the discriminator.
MiniLM: MiniLM is a compact version of the original Transformer model. It has 33 million parameters for the 12-layer model and 22 million parameters for the 6-layer model. Its smaller size and performance comparable to larger models make it a viable choice for our task.
TinyBERT: TinyBERT is a compact version of BERT specifically designed for efficient deployment. The 4-layer version of TinyBERT has approximately 14.5 million parameters, making it significantly smaller than BERT-base.
GPT-2: GPT-2, a transformer-based language model with 1.5 billion parameters, boasts impressive language generation capabilities. However, its extensive size may present challenges within our specific application.

T5 Small: T5 Small, a variant of the Text-To-Text Transfer Transformer (T5) model, restructures all NLP tasks into a uniform text-to-text format, where both input and output are text strings. With 60 million parameters, T5 Small serves as a versatile checkpoint suitable for various NLP tasks, ranging from machine translation and document summarization to question answering and classification.

## 5. __Model Training__
The training phase stands as a crucial stage in the evolution of our generative AI model, specifically designed for language comprehension tasks such as DistilBERT. This phase entails instructing the model to grasp and generate responses pertinent to the realm of artificial intelligence and machine learning. Utilizing a dataset comprising question-answer pairs sourced from diverse references including textbooks, research papers, and the GPT model itself, the training process can be conceptualized as an optimization challenge. Our objective is to determine the optimal parameters θ* that minimize the loss function L, given a parameter set θ.

* =argmin θ L(θ)

The loss function L evaluates the disparity between the model's forecasts and the genuine answers within the training dataset. To optimize this, stochastic gradient descent (SGD) or its adaptations are employed.
        t+1 =t​-η∇L(t​)

Where η denotes the learning rate, and ∇L(t​)  signifies the gradient of the loss function at t. The training process consists of multiple epochs, with each epoch representing a complete iteration through the entire training dataset. During each epoch, adjustments are made to the model's parameters to minimize the loss function.

Following the completion of the model's training, we fine-tune it for our specific objective of generating responses within the domain of artificial intelligence and machine learning, harnessing the capabilities of models such as DistilBERT. Fine-tuning involves training the model on our particular task using a reduced learning rate. This facilitates the adaptation of the model to the intricacies of our task while retaining the general knowledge acquired during pre-training.

   1N  i=1NCrossEntropy(yi​,f(xi​;))+λR() 
	
In this context, θ signifies the parameters of the model, N represents the count of training samples, xi​  and yi​  denote the input question and corresponding true answer pair, f(xi​;)  represents the output produced by the model for input xi, CrossEntropy denotes the cross-entropy loss function, and R(θ) stands for a regularization term aimed at preventing overfitting.

Throughout the training procedure, the model's parameters undergo iterative updates using optimization algorithms such as stochastic gradient descent (SGD) or its variations like Adam or RMSprop. The formula for updating the parameter θ can be articulated as:
        -CrossEntropyyi​,fxi​;+λR 
where α represents the learning rate, controlling the magnitude of parameter updates, and denotes the gradient with respect to the model parameters. Throughout the training iterations, the model's performance is monitored using evaluation metrics such as perplexity and accuracy. Perplexity quantifies the model's predictive uncertainty, while accuracy measures its proficiency in generating answers consistent with the NCERT syllabus.
In an optimal offline LLM situation, the training process is conducted meticulously over a series of epochs, ensuring thorough adaptation of the model to the task at hand. The optimum number of epochs is determined empirically, balancing between model convergence and computational resources, typically ranging from 5 to 20 epochs for DistilBERT-based models. This iterative optimization process, combined with fine-tuning and evaluation, culminates in a highly proficient AI model capable of delivering contextually accurate responses, thereby revolutionizing language understanding and generation tasks.

## 6. __Quantization__
The focus of this paper is on the most commonly used uniform quantization format whose quantization process can be expressed as:
Xint​=Xfp16​-ZS

S​=max(XFP16​)-min(XFP16​)​  2N-1-1
 
How quantization works
The majority of interactions with generative models take place via APIs, on servers with elastic resources handling the computational heavy lifting. This is a result of the extreme hardware strain these models place on it. Quantization emerges as a valuable technique for enhancing power efficiency and alleviating this computational burden. Although the term "quantization" encompasses a wide range of methods, its essence is the ability to transform continuous infinite input values from a large set into discrete finite output values in a smaller set. You can use the following analogy to understand quantization. You get asked what time it is by someone. You would say "10:21" after looking at your watch, but that wouldn't be entirely accurate. We employ the convention of hours, minutes, and seconds to quantize, or approximate, the continuous variable that is time, reducing it to discrete values

## 7. __RESULTS__
In the research conducted, an offline user interface was developed using Flask, a Python web framework, to emulate the conversational platform, with a focus on real-time interaction. This interface prioritizes fluid conversation and facilitates seamless exchanges through a text-based input field and contextually generated responses using natural language processing. Emphasizing accessibility, the design ensures ease of navigation for users with varying technical proficiency, guided by minimalist layout principles. Functionally, the interface supports diverse conversational interactions across various topics, enabling users to ask questions, seek information, or engage in dialogue. Adaptability enhances engagement, with tailored responses and prompts provided to assist users. Positive responses from usability tests and feedback sessions affirm the interface's simplicity and responsiveness, further supported by a comparative analysis demonstrating its superiority over existing systems. In summary, the offline user interface offers a streamlined platform for natural language interactions, continually refined based on user feedback and emerging technology to maintain effectiveness and relevance.



