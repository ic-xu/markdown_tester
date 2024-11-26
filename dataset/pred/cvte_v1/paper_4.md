## A Scaling laws  
We use 7 models to fit the sealing laws of Baichuan2.The parameler details are shown in Tuble 10.  
<table border = "2" width="50%" height="50%"><tr><td>Nasn</td><td>AnN</td><td>Naa</td><td>Niaal</td><td>Vrarers(Millions)</td></tr><tr><td>384 704 812 1.216 1.792 171 2.8801</td><td>1.152 2.112 2.496 3.648 5.376 6.72 8.640</td><td>5 8 12 l6 210 2 28</td><td>6 8 8 9 14 20</td><td>11.51 51.56 108.0 307.60 835.00 1.565.60 3.019.33</td></tr></table>  
Table 10. The model se choose for fitting scaling laws.  
The losses of the T diffcrent models are shown  
in Figure 8.  
![image](http://ai.cvte.com/openminio/doc-recovery-prd/2024/11/25/f3e161838ad094eb8033f1ac65487ad0/504ece37-2870-4d64-b649-02d4d93c7bcc.jpg)

Figure 8:The various training lass of small models torscaling law  
## B NormHead  
By conclucting a word embecding KNN retrievaltask, where given a qucry word the nearest Kwords are retrieved. We found that the semanticinformation is mainly encoded by the cnsinesimilarity of embedding rather than La distance.ie,The KNN results of cosine similarity are wordswith semantic sirmilarity while the KNN results ofL distance are meaningless in some way. Sincethe current linear classifier computes logits by datproduct, which is a mixture of La distance andcosinc similarity. To alleviate the distraction of L2distance. We propose to compute the logits by theanglc only.We normalized the ourput Embedding8o Lhat the dot product is not affected by the norrmofembedding.To validale this operation, we conduct an  
ablation experiment where we add or remove thenormalization before softmax and train a 7B madelfor 12k steps. All the hyper-parameters and data arethe same with Baichuan 2-7B.The training loss is  
shurwn in Figure9.We can see that when rermovingthe NorreHead the training became very unstable atthe heginning. on the contrary, after we normalizedthe reaul the training became very stable, whichresulted in hetter performance.  
![image](http://ai.cvte.com/openminio/doc-recovery-prd/2024/11/25/f3e161838ad094eb8033f1ac65487ad0/9ad1297f-ecc6-488c-97ab-fdbadeebc9e6.jpg)

Figure 9:The training loss with and withour Norm Headoperation.The experiments are conducred on 7 hillionparameters with the same hyper parameters (lorchrandom seeds, data flow, batch size,learning rate, etc.)  
## C Training Dynamics  
In this scction,we analyze the training dynamics ofour model. We save the checkpoints of Baichuan 2TB and Baichuan 2-13B every 1000 steps. Andevaluate those intermediale results on C-Evaldevelopment set (Huang et al.,2023),MML,U(Hendrycks ct al., 2021a),CMMLU(Li ct al,2023),JEC-QA(Zhong et al.,2020),GSM8K(Shict al.2022) and HumanEval(Chen ct al.2021)  
The result is shown in Figure 10.As shown, both the 7B and 13B modclsclermonstrate substantial gains as trainingprogresses. However, on general henchmarkssuch as MMLU (Hendrycks et al..2021a) andC. Eval (Huang et al.,2023), improvements appearto plateau after 2 trilliun tokens. In contrast.consistent gains are achieved on the GSM8Kmath tasks even beyond 2 trillion tokens. Thissuggests training FLOPs may strongly correlatewith improverments in math problem solving.which may be further studied.  
## D Baichuan Harmless Evaluation Dataset  
## WARNTNG: this section confains ansafe offensive  
or upsetting examples of texz.We proposed the Baichuan Harmless EvaluationDataset (BHED) to evaluate the chut models, as  

