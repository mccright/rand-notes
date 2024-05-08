# Random Artificial Intelligence & Machine Learning Notes  

There is an AI *theme* applied to virtually anything at work.  My experience says that signals simple *hype* (or *executive echo chamber*) but my reading also suggests that this hum of *AI-everything* is ignored at our peril.  Maybe you have analogous sensations?  If not, maybe think some more...  

This is alpha interest work.  After percolating in this format for a while, I'll figure out how to better prioritize this reading and content.  


## Where do we encounter AI/ML?  
* Games  
* Investing  
* Logistics systems  
* Medical diagnosis  
* Search 
* Autonomous driving  
* Language translation  
* Chatbots (general) 
* Interactive personal assistance  
* *Consumer*/*customer*/consumption suggestions, advice, and *support* (and product/service reviews)  
* *Customer* support  
* Application development  

## Required Workflow(s):  
Starter list outline below:  
* Data Governance (Trust-Building and Transparency)  
* Data Collection (Acquire New Data as Needed; resist hostile inputs)  
* Understanding the Target Business (including model performance metrics and business KPIs)  
* Understanding the Data  
* [Feature Engineering](https://en.wikipedia.org/wiki/Feature_engineering) & Data Preparation (Analysis, Cleaning, Repair; resist hostile inputs)  
* Model Training (resist hostile inputs)  
* Model Evaluation  
* Model Deployment (resist hostile inputs)  
* Monitor Deployed AI Model Quality (Trust-Building)  
* Monitor Deployed AI Model Fairness (Trust-Building)  
* Monitor Deployed AI Model Explainability (Trust-Building and Transparency)  

List above began with a model [IBM AI lifecycle](https://www.ibm.com/blog/ai-model-lifecycle-management-build-phase/)  

## Maybe Leave This Page Now and Read "This" for Context!
Yes.  Go read this now...  
**"AI Is a Lot of Work."**  
As the technology becomes ubiquitous, a vast tasker underclass is emerging — and not going anywhere.  
By **[Josh Dzieza](https://www.theverge.com/authors/josh-dzieza)**, June 20, 2023.  New York Magazine.  
https://nymag.com/intelligencer/article/ai-artificial-intelligence-humans-technology-business-factory.html  


## Resources:  
* "Executive Order on the Safe, Secure, and Trustworthy Development and Use of Artificial Intelligence." October 30, 2023 [https://www.whitehouse.gov/...and-use-of-artificial-intelligence/](https://www.whitehouse.gov/briefing-room/presidential-actions/2023/10/30/executive-order-on-the-safe-secure-and-trustworthy-development-and-use-of-artificial-intelligence/)  
  Then Ezra Klein [recommends](https://www.nytimes.com/2023/11/22/opinion/openai-sam-altman.html) reading A.I. writer Zvi Mowshowitz’s [analysis](https://thezvi.substack.com/p/on-the-executive-order), and [roundup of reactions](https://thezvi.substack.com/p/reactions-to-the-executive-order)  
* Associated Press coverage of AI [https://apnews.com/hub/artificial-intelligence](https://apnews.com/hub/artificial-intelligence) and [https://apnews.com/hub/generative-ai](https://apnews.com/hub/generative-ai)  
* Watch or join the [W3C Generative AI Community Group](https://www.w3.org/community/gai/) created September 2023 and/or the [w3C Human Centric AI Community Group](https://www.w3.org/community/humancentricai/) created April 2023  
* Allen Institute for Artificial Intelligence [https://allenai.org/](https://allenai.org/)  
* AI2 Leader Boards [https://leaderboard.allenai.org/](https://leaderboard.allenai.org/)  
* One view of *current topics* in AI/ML:  [https://arxiv.org/search/truncated](https://arxiv.org/search/advanced?advanced=&terms-0-operator=AND&terms-0-term=cs.AI&terms-0-field=all&classification-physics_archives=all&classification-include_cross_list=include&date-filter_by=all_dates&date-year=&date-from_date=&date-to_date=&date-date_type=submitted_date&abstracts=show&size=200&order=-announced_date_first)  
* NIST on the topic: "[Powerful AI Is Already Here: To Use It Responsibly, We Need to Mitigate Bias](https://www.nist.gov/blogs/taking-measure/powerful-ai-already-here-use-it-responsibly-we-need-mitigate-bias)."  
* NIST AI Risk Management Framework (RMF): [https://www.nist.gov/itl/ai-risk-management-framework](https://www.nist.gov/itl/ai-risk-management-framework)  
* and the accompanying NIST AI RMF Playbook: [https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook](https://airc.nist.gov/AI_RMF_Knowledge_Base/Playbook)  
* "A curious person's guide to artificial intelligence -- Everything you wanted to know about the AI boom but were too afraid to ask." By Pranshu Verma and Rachel Lerman, 2023-05-07  https://www.washingtonpost.com/technology/2023/05/07/ai-beginners-guide/  
* "You probably don't know how to do Prompt Engineering -- Features missing from most LLM front-ends that should exist." https://gist.github.com/Hellisotherpeople/45c619ee22aac6865ca4bb328eb58faf  
* "Humans Feel Too Special for Machines to Score Their Morals." By Zoe A Purcell and Jean-François Bonnefon, 29 May 2023. https://academic.oup.com/pnasnexus/advance-article/doi/10.1093/pnasnexus/pgad179/7185601?searchresult=1  PNAS Nexus, pgad179,  https://doi.org/10.1093/pnasnexus/pgad179  



# Natural Language Processing and Common Sense
### Types of Reasoning:  
* **Human intuition and instinct**: Its processes are unconscious, *effortless*, fast, associative, *automatic-pilot*, slow-learning.  Its content is conceptual, temporal (for example before and after) and can be evoked by language. [D.Kahneman1](https://www.amazon.com/Thinking-Fast-Slow-Daniel-Kahneman/dp/0374533555/)  
* **Rational thinking**: Its processes are require effort, and are slow, *logical*, governed by rules, often serial, sometimes flexible, and indecisive.  Its content is conceptual, temporal and can be evoked by language. [D.Kahneman1](https://www.amazon.com/Thinking-Fast-Slow-Daniel-Kahneman/dp/0374533555/)  


## Timeline Ideas:  
* 2024: Feb 8th Google changed the name of its chatbot from Bard to Gemini and introduced a smartphone app [Gemini](https://blog.google/products/gemini/bard-gemini-advanced-app/) -- like a talking digital assistant and a conversational chatbot.  
* 2023: [Google releases a conversational AI service called "*Bard*"](https://blog.google/technology/ai/bard-google-ai-search-updates/) (*or go directly to [https://bard.google.com/](https://bard.google.com/)*) to compte with ChatGPT. ...There are many *competitors*: [Bing AI](https://www.microsoft.com/en-us/edge/features/the-new-bing?form=MT00D8) (*or go directly to [https://www.bing.com/new](https://www.bing.com/new)*) (research), Claud/Claude 2 (writing), Google Docs AI (Notes), BlueWillow (images), ChatGPT+ (research, writing, search), Notion AI (Notes), Midjourney (images), Canva AI (art/design), Le Chat ([Mistral AI](https://mistral.ai/), free access at [https://chat.mistral.ai](https://chat.mistral.ai))  
* 2022: OpenAI released ChatGPT - an a LLM conversational AI service that accepts inputs in plain language and spits out human-friendly, content relevant results.  
* 2021: [Language Model for Dialogue Applications](https://blog.google/technology/ai/lamda/) (or LaMDA for short)  
* 2020: OpenAI GPT-3 a language model that generates text using pre-trained algorithms.  
* 2019:  
* 2018: 'Human-level performance' on reading comprehension (limited data set & limited definition of *comprehension*) -- Alibaba language processing AI beats top humans at a Stanford University reading and comprehension test, scoring 82.44 against 82.30 on 100,000 questions.  
* 2017:  
  * 'Super-human performance' on speech recognition  
  * [Transformer](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html) neural network architecture  
  * Google's [Alpha Go](https://en.wikipedia.org/wiki/AlphaGo) [defeats Chinese Go champion, Ke Jie](https://www.deepmind.com/research/highlighted-research/alphago)  
* 2016:  
  * 'Google neural' machine translation  
  * Google's [Alpha Go](https://en.wikipedia.org/wiki/AlphaGo) [defeats Go champion Lee Sedol](https://www.deepmind.com/research/highlighted-research/alphago)  
* 2015:  
  * 'Super-human performance' on image captioning  
  * 'Super-human performance' on object recognition  
* 2014:  
* 2013: Robot HRP-2, built by SCHAFT Inc. of Japan, a subsidiary of Google, defeats 15 teams to win DARPA's Robotics Challenge Trials by completing disaster response tasks, including driving a vehicle, walking over debris, climbing a ladder, removing debris, walking through doors, cutting a wall, closing valves, and connecting a hose.  
* 2012:  
* 2011: IBM's Watson wins Jeopardy.  Apple introduces Siri.  
* 2010:  
* 2005: Computer scientist Sebastian Thrun and a Stanford Artificial Intelligence Laboratory team build a driverless car (*Stanley*) that was the first autonomous vehicle to complete a DARPA Grand Challenge 132-mile course in the Mojave Desert.  
* 1980: The "neocognitron", which introduced the two basic types of layers in *Convolutional neural networks* (CNNs) -- convolutional layers and downsampling layers -- was [introduced by Kunihiko Fukushima in 1980](https://en.wikipedia.org/wiki/Convolutional_neural_network#History).  
* 1955: "[A Proposal for the Dartmouth Summer Research Project on Artificial Intelligence. August 31, 1955."](https://ojs.aaai.org/index.php/aimagazine/article/download/1904/1802)  


#### Timeline Notes:  
* Stanford AI 100 [https://ai100.stanford.edu/reflections-and-framing](https://ai100.stanford.edu/reflections-and-framing)  
* "The History of Artificial Intelligence." by Rockwell Anyoha, 2017 [https://sitn.hms.harvard.edu/flash/2017/history-artificial-intelligence/](https://sitn.hms.harvard.edu/flash/2017/history-artificial-intelligence/)  
* "[The History of Artificial Intelligence.](https://courses.cs.washington.edu/courses/csep590/06au/projects/history-ai.pdf)" from 'History of Computing' CSEP 590A, University of Washington, December 2006, By Chris Smith, Brian McGuire, Ting Huang and Gary Yang.  
* [https://www.ai.nl/artificial-intelligence/timeline-of-ai-a-brief-history-of-artificial-intelligence-its-highlights/](https://www.ai.nl/artificial-intelligence/timeline-of-ai-a-brief-history-of-artificial-intelligence-its-highlights/)  
* "LaMDA: our breakthrough conversation technology." [https://blog.google/technology/ai/lamda/](https://blog.google/technology/ai/lamda/) By Eli Collins and Zoubin Ghahramani.  
* "Transformer: A Novel Neural Network Architecture for Language Understanding." [https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html](https://ai.googleblog.com/2017/08/transformer-novel-neural-network.html) Thursday, August 31, 2017, By Jakob Uszkoreit  
* "Why Do A.I. Chatbots Tell Lies and Act Weird? Look in the Mirror." [https://www.nytimes.com/2023/02/26/technology/ai-chatbot-information-truth.html](https://www.nytimes.com/2023/02/26/technology/ai-chatbot-information-truth.html) By Cade Metz  
* [NewsGuard](https://www.newsguardtech.com/special-reports/ai-tracking-center/) -- "Tracking AI-enabled Misinformation" -- identified [475 ‘unreliable AI-generated news’ websites by 2023-09-18](https://www.newsguardtech.com/special-reports/ai-tracking-center/).  These unreliable AI-generated news outlets operatied "with little to no human oversight."  NewsGuard concluded that these outlets "have been a boon to content farms and misinformation purveyors alike."  


## Resource Consumption:  
* "As they race to capitalize on a craze for generative AI, leading tech developers including Microsoft, OpenAI and Google have acknowledged that growing demand for their AI tools carries hefty costs, from expensive semiconductors to an increase in water consumption." ... "In its latest environmental report, Microsoft disclosed that its global water consumption spiked 34% from 2021 to 2022 (to nearly 1.7 billion gallons, or more than 2,500 Olympic-sized swimming pools), a sharp increase compared to previous years that outside researchers tie to its AI research." ...  "Google [reported](https://sustainability.google/reports/google-2023-environmental-report/) a 20% growth in water use in the same period, which Ren also largely attributes to its AI work. Google’s spike wasn’t uniform -- it was steady in [Oregon where its water use has attracted public attention](https://apnews.com/article/technology-business-environment-and-nature-oregon-united-states-2385c62f1a87030d344261ef9c76ccda), while doubling outside Las Vegas. It was also thirsty in Iowa, drawing more potable water to its Council Bluffs data centers than anywhere else." ... "“It’s fair to say the majority of the growth is due to AI,” including “its heavy investment in generative AI and partnership with OpenAI,” said Shaolei Ren, a researcher at the University of California, Riverside who has been trying to calculate the environmental impact of generative AI products such as ChatGPT.  In a paper due to be published later this year, Ren’s team estimates ChatGPT gulps up 500 milliliters of water (close to what’s in a 16-ounce water bottle) every time you ask it a series of between 5 to 50 prompts or questions. The range varies depending on where its servers are located and the season. The estimate includes indirect water usage that the companies don’t measure — such as to cool power plants that supply the data centers with electricity."  ...In late May, 2023 "Microsoft’s president, Brad Smith, disclosed that it had built its “advanced AI supercomputing data center” in Iowa, exclusively to enable OpenAI to train what has become its fourth-generation model, GPT-4. The model now powers premium versions of ChatGPT and some of Microsoft’s own products and has accelerated a debate about containing AI’s societal risks."   ..."describing it as a “single system” with more than 285,000 cores of conventional semiconductors, and 10,000 graphics processors — a kind of chip that’s become crucial to AI workloads.  Experts have said it can make sense to “pretrain” an AI model at a single location because of the large amounts of data that need to be transferred between computing cores."  "In July 2022, the [month before OpenAI says it completed its training of GPT-4](https://arxiv.org/abs/2303.08774), Microsoft pumped in about 11.5 million gallons of water to its cluster of Iowa data centers, according to the West Des Moines Water Works. That amounted to about 6% of all the water used in the district, which also supplies drinking water to the city’s residents."     [https://apnews.com/article/chatgpt-gpt4-iowa-ai-water-consumption-microsoft-f551fde98083d17a7e8d904f8be822c4](https://apnews.com/article/chatgpt-gpt4-iowa-ai-water-consumption-microsoft-f551fde98083d17a7e8d904f8be822c4) and [https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RW15mgm](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RW15mgm)  


## Some Definitions:  

"AI guidance, terms added to [AP Stylebook](https://www.apstylebook.com/)." Aug. 17, 2023, by Nicole Meir.  [https://blog.ap.org/ai-guidance-terms-added-to-ap-stylebook](https://blog.ap.org/ai-guidance-terms-added-to-ap-stylebook)  
>Guidance on how to cover artificial intelligence and 10 key AI terms were added today to the AP Stylebook, to help journalists accurately explain the potential, inherent risks and varying effects of AI and generative AI models.  

* *Algorithmic bias* "A term used to describe the negative impacts of AI tools that draw from large datasets that are skewed by historical or selection bias." (*from the [AP Stylebook](https://www.apstylebook.com/)*)  
* *Common Sense* "It's the unspoken, implicit knowledge that you and I have. It's so obvious that we often don't talk about it." [Interview with Yejin Choi](https://www.nytimes.com/interactive/2022/12/26/magazine/yejin-choi-interview.html)  
* *Common Sense* is the basic level of 'practical' knowledge and reasoning concerning everyday situations and events that are commonly shared among most people.  It is essential for humans to live and interact with each other in a reasonable and safe way. [Yejin Choi](https://homes.cs.washington.edu/~yejin/) [at](https://homes.cs.washington.edu/~msap/acl2020-commonsense/slides/01%20-%20Intro.pdf)  *Common Sense* is a difficult challenge and integration into AI implementations still suffer from:  
  * *Common sense inferences* are about predicting new information that is likely to be true based on partially available information. [Yejin Choi](https://homes.cs.washington.edu/~yejin/) at: [https://homes.cs.washington.edu/~msap/acl2020-commonsense/slides/01%20-%20Intro.pdf](https://homes.cs.washington.edu/~msap/acl2020-commonsense/slides/01%20-%20Intro.pdf)  
  * *Common sense* is essential for humans to live and interact with each other in a reasonable and safe way, and it is essential for AI to understand human needs and actions better. [Yejin Choi](https://homes.cs.washington.edu/~yejin/) at: [https://homes.cs.washington.edu/~msap/acl2020-commonsense/slides/01%20-%20Intro.pdf](https://homes.cs.washington.edu/~msap/acl2020-commonsense/slides/01%20-%20Intro.pdf)  
  * "Insufficient coverage" --> Pre-trained language models contain *some* commonsense knowledge -- but an impractically small subset of what is needed for most use cases.  
  * "Insufficient precision" --> Language models also generate false facts -- which can be an annoyance or a catastrophy, depending on your use case.  
* *Generative artificial intelligence* (generative AI) "Generative AI is the technology to create new content by utilizing existing text, audio files, or images. With generative AI, computers detect the underlying pattern related to the input and produce similar content. This is in contrast to most other AI techniques where the AI model attempts to solve a problem which has a single answer (e.g. a classification or prediction problem)." (*from the [AIMultiple](https://research.aimultiple.com/generative-ai/)*)  Various techniques include (*but are not limited to*):  
    * **Transformers**: "Transformers, such as [GPT-3](https://research.aimultiple.com/gpt/), [LaMDA](https://research.aimultiple.com/lamda/), [Wu-Dao](https://research.aimultiple.com/wu-dao/) and [ChatGPT](https://research.aimultiple.com/chatgpt/) imitate cognitive attention and differentially measure the significance of the input data parts. They are trained to understand the language or image, learn some classification tasks and generate texts or images from massive datasets." (*from the [AIMultiple](https://research.aimultiple.com/generative-ai/)*)  
    * **Generative adversarial networks** (GANs): "[GANs](https://research.aimultiple.com/gan-synthetic-data/) are two neural networks: a generator and a discriminator that pit against each other to find equilibrium between the two networks:  The *generator network* is responsible for generating new data or content resembling the source data.  The *discriminator network* is in charge of differentiating between the source and the generated data in order to recognize what is closer to the original data." (*from the [AIMultiple](https://research.aimultiple.com/generative-ai/)*)  
    * **Variational auto-encoders**:  "The encoder encodes the input into compressed code while the decoder reproduces the initial information from this code.  If chosen and trained correctly, this compressed representation stores the input data distribution in a much smaller dimensional representation." (*from the [AIMultiple](https://research.aimultiple.com/generative-ai/)*)  
	* **Hallucinate**: When a chatbot fabricates information or emits definitive statements on uncertain fact sets [from Cade Metz in the NYT](https://www.nytimes.com/2023/05/01/business/ai-chatbots-hallucination.html).  
Always consider "the models’ tendency to generate inaccurate responses to queries." (*from the [AP Stylebook](https://www.apstylebook.com/)*)  
* *Machine learning* (ML) is often viewed as a subset of *Artificial Intelligence*.  ML employes previously collected data to predict outcomes.  ML *models* may depend upon direct human inputs (*training or supervision*), or not, depending on their algorithms and their level of training maturity.  ML enables software (*and supporting infrastructure*) to build upon training/experience and improvise suggestions or results.  At some point, *modern* implementations involve [AI systems helping humans oversee other AI](https://nymag.com/intelligencer/article/ai-artificial-intelligence-humans-technology-business-factory.html)" to enable *economical* ML/AI at scale.  
* *Natural language processing* (NLP) is a growing field within artificial intelligence. The fundamental goal of NLP is to program computers capable of human-level understanding of natural language. Common NLP applications include personal assistants and chatbots, automatic translation, question answering, sentiment analysis and summarization. Among the main challenges of NLP research is that human language is often ambiguous and underspecified. A person processing language relies heavily on their commonsense knowledge and reasoning abilities to resolve these ambiguities and complete missing information. Machine learning based NLP models, on the other hand, lack this commonsense and often make absurd mistakes. From [Dr. Vered Shwartz](https://www.cs.ubc.ca/~vshwartz/index.html) in her [2022 NLP course description](https://www.cs.ubc.ca/~vshwartz/courses/CPSC532V-22/index.html)  
* *[Convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network)* (CNN)"In deep learning, a convolutional neural network (CNN, or ConvNet) is a class of artificial neural network (ANN), most commonly applied to analyze visual imagery. CNNs are also known as Shift Invariant or Space Invariant Artificial Neural Networks (SIANN), based on the shared-weight architecture of the convolution kernels or filters that slide along input features and provide translation-equivariant responses known as feature maps. Counter-intuitively, most convolutional neural networks are not invariant to translation, due to the downsampling operation they apply to the input. They have applications in image and video recognition, recommender systems, image classification, image segmentation, medical image analysis, natural language processing, brain–computer interfaces, and financial time series."  
* *Generative adversarial networks* (GANs) and *reinforcement learning* endow *deep networks* with the ability to produce artificial content such as fake images that pass for the real thing. "GANs consist of two interlocked components—a generator, responsible for creating realistic content, and a discriminator, tasked with distinguishing the output of the generator from naturally occurring content. The two learn from each other, becoming better and better at their respective tasks over time" [AI100Report_MT_10, page 12](https://ai100.stanford.edu/sites/g/files/sbiybj18871/files/media/file/AI100Report_MT_10.pdf).  
* Retrieval-Augmented Generation (RAG), focusing on high-dimensional embeddings crucial for machine learning...  *What is this?*  
* *[Recurrent neural network](https://en.wikipedia.org/wiki/Recurrent_neural_network)* (RNN) "is a class of artificial neural networks where connections between nodes can create a cycle, allowing output from some nodes to affect subsequent input to the same nodes. This allows it to exhibit temporal dynamic behavior. Derived from feedforward neural networks, RNNs can use their internal state (memory) to process variable length sequences of inputs. This makes them applicable to tasks such as unsegmented, connected handwriting recognition[4] or speech recognition."  
* Large Language Model (LLM)  
* *Reinforcement Learning from Human Feedback* (RLHF) https://en.wikipedia.org/wiki/Reinforcement_learning_from_human_feedback  
* *Sensibleness and Specificity Average* (SSA)  
* *Training data*  "refers to the vast corpus of information used to train large language models. This data can include text, images, audio, or video. Generative models learn patterns from this data, enabling them to generate new content matching the input data’s complexity, style, and structure." (*from [AIMultiple](https://research.aimultiple.com/generative-ai-data/)*)  "Explaining the term, and advising to consider the specific information training data may contain as machine learning models learn to find patterns from these datasets. The types of training data used in different AI tools can vary widely." (*from the [AP Stylebook](https://www.apstylebook.com/)*)  
 

## Some References:  
* A little guide to building Large Language Models in 2024. 2 part series:  
  * [Video 1](https://www.youtube.com/watch?v=2-SPH9hIKT8): covering all the concepts to train a good performance LLM in 2024  
    * [Slides for Video 1](https://docs.google.com/presentation/d/1IkzESdOwdmwvPxIELYJi8--K3EZ98_cL6c5ZcLKSyVg/mobilepresent#slide=id.g2c1fcf5439e_1_11)  
  * [Video 2](): hands-on applying all these concepts with code example  
* "Artificial Intelligence at Google: Our Principles" [https://ai.google/principles/](https://ai.google/principles/)  
* "Gathering Strength, Gathering Storms: The One Hundred Year Study on Artificial Intelligence (AI100) 2021 Study Panel Report." September 2021 [http://ai100.stanford.edu/2021-report](http://ai100.stanford.edu/2021-report)  
* Kahneman, Daniel.  "Thinking, Fast and Slow." [Amazon](https://www.amazon.com/Thinking-Fast-Slow-Daniel-Kahneman/dp/0374533555/)  
* Stanford 100 Year Study on AI [http://erichorvitz.com/100_year_study_on_AI_presentation_12_2016.pdf](http://erichorvitz.com/100_year_study_on_AI_presentation_12_2016.pdf)    
(https://en.wikipedia.org/wiki/Zero-shot_learning)  
* "Section 230 Won't Protect ChatGPT." By Matt Perault, 2023-02-23  [https://www.lawfareblog.com/section-230-wont-protect-chatgpt ](https://www.lawfareblog.com/section-230-wont-protect-chatgpt)  Quote:  
>"The emergence of products fueled by generative artificial intelligence (AI) such as ChatGPT will usher in a new era in the platform liability wars. Previous waves of new communication technologies—from websites and chat rooms to social media apps and video sharing services—have been shielded from legal liability for content posted on their platforms, enabling these digital services to rise to prominence. But with products like ChatGPT, critics of that legal framework are likely to get what they have long wished for: a regulatory model that makes tech platforms responsible for online content."  
* "Event will let hackers test limits of AI -- Goal is to find harmful issues that can be fixed." By Matt O'Brien, ASSOCIATED PRESS https://apnews.com/article/hacking-jailbreaking-chatgpt-bing-defcon-biden-ai-97b963db084800f11b26b8a023b1713f  Quote:  
>Anyone who's tried ChatGPT, Microsoft's Bing chatbot or Google's Bard will have quickly learned that they have [a tendency to fabricate information and confidently present it as fact](https://apnews.com/article/kansas-city-chiefs-philadelphia-eagles-technology-science-82bc20f207e3e4cf81abc6a5d9e6b23a). These systems, built on what's known as large language models, also emulate the cultural biases they've learned from being trained upon huge troves of what people have written online.  
* "Generative AI: 5 essential reads about the new era of creativity, job anxiety, misinformation, bias and plagiarism." By [Eric Smalley](https://theconversation.com/us/team#eric-smalley) 19-05-2023  [https://theconversation.com/generative-ai-5-essential-reads...](https://theconversation.com/generative-ai-5-essential-reads-about-the-new-era-of-creativity-job-anxiety-misinformation-bias-and-plagiarism-203746)  
* "White House unveils artificial intelligence ‘Bill of Rights'" By GARANCE BURKE, October 4, 2022 https://apnews.com/article/technology-business-artificial-intelligence-7a39848340d210592aeea2478225f489  
* "An algorithm that screens for child neglect raises concerns." By Garance Burke and Sally Ho. April 29, 2022 https://apnews.com/article/child-welfare-algorithm-investigation-9497ee937e0053ad4144a86c68241ef1  Quote:  
>From Los Angeles to Colorado and throughout Oregon, as child welfare agencies use or consider tools similar to the one in Allegheny County, Pennsylvania, an Associated Press review has identified a number of concerns about the technology, including questions about its reliability and its potential to harden racial disparities in the child welfare system. Related issues have already torpedoed some jurisdictions' plans to use predictive models, such as the tool notably dropped by the state of Illinois. According to [new research from a Carnegie Mellon University team](https://loganstapleton.com/wp-content/uploads/2022/04/Extended_Analysis__How_Child_Welfare_Workers_Reduced_Racial_Disparities_in_Algorithmic_Decisions.pdf) obtained exclusively by AP, Allegheny's algorithm in its first years of operation showed a pattern of flagging a disproportionate number of Black children for a "mandatory" neglect investigation, when compared with white children. The independent researchers, who received data from the county, also found that social workers disagreed with the risk scores the algorithm produced about one-third of the time.  
* Associated Press "Standards around generative AI." Aug. 16, 2023, by Amanda Barrett [https://blog.ap.org/standards-around-generative-ai}(https://blog.ap.org/standards-around-generative-ai)  
>Any output from a generative AI tool should be treated as unvetted source material. AP staff must apply their editorial judgment and AP’s sourcing standards when considering any information for publication.  
>Generative AI makes it even easier for people to intentionally spread mis- and disinformation through altered words, photos, video or audio, including content that may have no signs of alteration, appearing realistic and authentic. To avoid using such content inadvertently, journalists should exercise the same caution and skepticism they would normally, including trying to identify the source of the original content, doing a reverse image search to help verify an image’s origin, and checking for reports with similar content from trusted media.  
* "How to Tell if Your A.I. Is Conscious -- In a new report, scientists offer a list of measurable qualities that might indicate the presence of some presence in a machine." By Oliver Whang, 2023-09-18. [https://www.nytimes.com/2023/09/18/science/ai-computers-consciousness.html](https://www.nytimes.com/2023/09/18/science/ai-computers-consciousness.html)  

## ToDo: Experiment with the following to build additional context:  
* https://huggingface.co/ A platform where some parts of the machine learning community collaborate on models, datasets, and applications (free option).  
* Language Models: Python building blocks to explore large language models on any computer with 512MB of RAM [https://github.com/jncraton/languagemodels](https://github.com/jncraton/languagemodels) This package is designed to be as simple as possible for learners and educators exploring how large language models intersect with modern software development.  
* SadTalker：Learning Realistic 3D Motion Coefficients for Stylized Audio-Driven Single Image Talking Face Animation 
[https://github.com/OpenTalker/SadTalker](https://github.com/OpenTalker/SadTalker)  
* FableForge: "Generate a picture book from a single prompt using OpenAI's new function calling and Replicate's API for Stable Diffusion." [https://github.com/e-johnstonn/FableForge](https://github.com/e-johnstonn/FableForge)  
*  Machine Learning A-Z -- A step towards Data Science and Machine Learning [https://github.com/srafay/Machine_Learning_A-Z](https://github.com/srafay/Machine_Learning_A-Z)  
READ:  
"What is generative AI?"  (January 19, 2023) https://www.mckinsey.com/featured-insights/mckinsey-explainers/what-is-generative-ai  

"Seven new no-cost generative AI training courses to advance your cloud career." May 18, 2023 https://cloud.google.com/blog/topics/training-certifications/new-google-cloud-generative-ai-training-resources  

"Generative AI Data in 2023: Importance & 7 Methods"  Updated on July 10, 2023 https://research.aimultiple.com/generative-ai-data/  

"Introduction to Generative AI." 2 hr 33 min    Learning Path    3 Modules. https://learn.microsoft.com/en-us/training/paths/introduction-generative-ai/  

"Generative Design & Generative AI: Definition, 10 Use Cases, Challenges." By Cem Dilmegani  https://research.aimultiple.com/generative-design/  

"Generative Adversarial Networks (GAN) & Synthetic Data [2023]." By Cem Dilmegani, Updated on December 22, 2022  https://research.aimultiple.com/gan-synthetic-data/  

"Generative AI: 7 Steps to Enterprise GenAI Growth in 2023." By Cem Dilmegani, Updated on July 20, 2023  https://research.aimultiple.com/generative-ai/  

"Mistral AI releases new model to rival GPT-4 and its own chat assistant." By Romain Dillet, February 26, 2024 
https://techcrunch.com/2024/02/26/mistral-ai-releases-new-model...chat-assistant/](https://techcrunch.com/2024/02/26/mistral-ai-releases-new-model-to-rival-gpt-4-and-its-own-chat-assistant/?utm_source=tldrnewsletter)

https://apnews.com/hub/generative-ai  



-----
### Random  
ImageNet (zero-shot): SOTA, surpassing OpenAI CLIP (https://openai.com/blog/clip/).  
LAMA (factual and commonsense knowledge): Surpassed AutoPrompt (https://arxiv.org/abs/2010.15980).  
LAMBADA (cloze tasks): Surpassed Microsoft Turing NLG (https://www.microsoft.com/en-us/research/blog/turing-nlg-a-17-billion-parameter-language-model-by-microsoft/).  
SuperGLUE (few-shot): SOTA, surpassing OpenAI GPT-3 (https://arxiv.org/abs/2005.14165).  
UC Merced Land Use (zero-shot): SOTA, surpassing OpenAI CLIP (https://openai.com/blog/clip/).  
MS COCO (text generation diagram): Surpassed OpenAI DALL·E (https://openai.com/blog/dall-e/).  
MS COCO (English graphic retrieval): Surpassed OpenAI CLIP and Google ALIGN (https://ai.googleblog.com/2021/05/align-scaling-up-visual-and-vision.html).  
MS COCO (multilingual graphic retrieval): Surpassed UC² (best multilingual and multimodal pre-trained model) (https://arxiv.org/pdf/2104.00332.pdf).  

