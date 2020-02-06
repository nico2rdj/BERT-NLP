# BERT sur SQuAD 2.0

<p align="center" >

  ![bert](https://user-images.githubusercontent.com/22484369/73925375-3f426480-48ce-11ea-8f5d-bf92ab1ebe87.png)


</p>

<h3 align="center">
  📄 Différents Fine-Tuning de BERT sur le dataset SQuAD 2.0
</h3>
<p align="center">
  Projet NLP <br/>
  <small></small>
</p>

## Manuel d'utilisation

- Se placer à la fin du jupyter notebook dans la cellule ci-dessous et mettre le paragraphe dans la variable doc et la question dans la variable q : 

![example](https://user-images.githubusercontent.com/22484369/73929430-11145300-48d5-11ea-8e14-a29becca0ff4.png)
 
    
   
    
    
    

## Détails de l'implémentation de BERT


- Pour le preprocessing, nous avons utilisé la libraire **transformers** avec la fonction **SquadV2Processor** pour récupérer les questions et réponses puis **squad_convert_examples_to_features** pour convertir les celles-ci en features que l'on donne en entrée de BERT. <br/>

Le format des entrées est le suivant : <br/>
![input](https://user-images.githubusercontent.com/22484369/73931543-c8f72f80-48d8-11ea-96e1-76f477e344f0.png)

 - Ces entrées représente : 
    - attention mask
    - entrée contenant la question et la réponse sous forme id de token
    - position du début de la réponse
    - position de la fin de la réponse

- Pour BERT, nous avons utilisé l'architecture Fine-Tuned **BertForQuestionAnswering** de base avec des poids préentraînés 


![bert-ft](https://user-images.githubusercontent.com/22484369/73930902-a3b5f180-48d7-11ea-8145-b8a79f439229.png)



## Dataset: SQuAD 2.0
- Nous utilisons le dataset Squad 2.0 comportant un jeu de données de questions et de réponses associées. La grande particularité de ce dataset, et ce qui le différencie la première version de SQuAD, concerne la possibilité d'avoir une question sans réponse. Il nous faut donc à la fois trouver la position d'une réponse dans un texte lorsqu'elle existe, mais aussi ne pas donner de réponse lorsque la question n'en a pas. 

- Par conséquent, de simples modèles (ex: Bert) qui performent avec plus de 85% sur SQuAD doivent être finetunés pour dépasser les 66% sur SQuADv2

- Nous avons essayé deux modèles différents en Fine Tuned la dernière couche:
  - L'un avec une couche Dense classique
  - L'autre avec une couche LSTM

## Résultats sur le dataset SQuAD 2.0
Pour les résultats, nous avons comparé plusieurs modèles sur plusieurs métriques, mais nous avons gardé le F1 score afin de comparer au mieux nos résultats. 

- Couche Dense classique: <br/>

Pour la couche Dense classique, comme nous l'avons dit précédemment, les résultats sont plus faibles sur SQuAD v2 avec un score de 66%. Cette couche n'est donc pas suffisante, nous avons donc décidé de tester d'autres modèles.

- LSTM: <br/>

Une idée, assez peu utilisé mais qui peut s'averer pertinente est celle des LSTM. On obtient avec cette méthode un score de ...%. 

- CNN: <br/>

On a voulu utiliser un CNN en sortie de Bert, plus précisément un CNN 1d, qui va prendre en entrée la concaténation des 4 dernières couches de Bert. Nous avons obtenu un score de ...% (en cours d'entrainement).

## License

- [MIT](LICENSE)

## Contributors
- Fares Embouazza
- Nicolas Martin
