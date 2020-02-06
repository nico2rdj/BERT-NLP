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

- Nous avons essayé deux modèles différents en Fine Tuned la dernière couche:
  - L'un avec une couche Dense classique
  - L'autre avec une couche LSTM


## Résultats sur le dataset SQuAD 2.0



## License

- [MIT](LICENSE)

## Contributors
- Fares Embouazza
- Nicolas Martin
