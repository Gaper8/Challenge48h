Challenge 48h : Analyse des Tweets Clients d'Engie et Paramétrage d'Agents IA

🌟 Introduction

Ce projet a été réalisé dans le cadre du Challenge 48h. Nous avons analysé plus de 500 tweets envoyés par des utilisateurs à Engie.

Nos objectifs principaux étaient :

- Nettoyer et extraire les données essentielles.

- Classifier les tweets selon leur sentiment, niveau d'inconfort et catégorie grâce à une IA.

- Concevoir un tableau de bord interactif pour la visualisation des données.

📝 Méthodologie

Traitement des données : 

Dans cette partie, nous avons fait le choix de changer le format de la date. Le format passe en JJ/MM/AAAA avec l'heure.

Pour le nettoyage nous avons fait le choix d'enlever les colonnes : 

- id ❌ (inutile pour l'analyse des tweets)

- screen_name ❌ (inutile pour l'analyse des tweets)

- name ❌ (inutile pour l'analyse des tweets)

Les KPI : 

Nous avons défini 7 KPI pour suivre et analyser les tweets :

- Total des tweets. Vision d'ensemble du volume de tweets.
- Satisfaction moyenne, par rapport à la colonne inconfort. Nous choisissons ce kpi pour permettre d'avoir une vue d'ensemble de la satisfaction des utilisateurs.
- Répartition des tweets par type de problème. Combien de tweets concernent la facturation, Gaz, Electricité, Contrat, Autre etc.
- Taux de tweets résolus. Affiche le nombre de tweets ou le problème a été résolu et non résolu.
- Taux de tweet positif, negatif et neutre. Ce kpi permettra aussi d'avoir une vue plus global sur le nombre d'avis positif, négatif ou neutre.
- Nombre de tweets par jour/semaine/mois. Nous avons choisi ce kpi pour avoir une analyse temporelle.
- Fréquence des mentions des comptes Engie. Ce kpi permettra de voir quels comptes Engie sont le plus mentionnés.

🎭 L'analyse des sentiments : 

Pour réaliser l'analyse des sentiments nous avons rajouté une colonne "sentiment" avec trois catégories possible : 

😀 Positif

😐 Neutre

😡 Négatif

Pour réaliser cette classification voici comment nous avons fait : 

Nous avons utilisé un agent IA basé sur Mistral pour effectuer une classification automatique des tweets. Il choisis quel catégorie correspond le mieux au tweet.

🤖 Processus de création des agents IA :

    1. Logique utilisée pour détecter les types de réclamations

L’agent IA repose sur un modèle NLP qui analyse le contenu des tweets et extrait les informations suivantes :

        "category": "Facturation / Gaz / Électricité / Contrat / Autre", permet de connaitre la catégorie dans laquelle se situe le problème de l'utilisateur.
        "sentiment": "Positif / Neutre / Négatif", analyse le sentiment de l'utilisateur en fonction de son tweet.
        "resolu": "Oui / Non", Cette information permet de savoir grâce à des phrases comme "merci", ou "problème réglé", si le problème est résolu ou non.
        "inconfort": Un score de 0 à 100, il permet de savoir à quel point le problème de l'utilisateur lui créer des problèmes.
        "urgence": true / false, permet de savoir si c'est une urgence grâce à des mots clés.

    2. Les prompts ou fine-tuning réalisés :

Voici le prompt que nous utilisons.

        You are an NLP agent for analyzing tweets.
        Return **ONLY a valid JSON** with these attributes:
        
        {{
            "category": "Facturation / Gaz / Électricité / Contrat / Autre",
            "sentiment": "Positif / Neutre / Négatif",
            "resolu": "Oui / Non",
            "inconfort": A score from 0 to 100,
            "urgence": true / false
        }}

Nous affinons progressivement le prompt pour améliorer la précision de la classification. Nous avons testé ce prompt avec différents tweets au début pour voir si l'ia réagissait bien avec des tweets très différents.

    3. Des exemples d’interactions générées par l’agent : 

![image](https://github.com/user-attachments/assets/748513b9-4f04-4a85-934a-d2b39da1e084)
![image](https://github.com/user-attachments/assets/b26b8cf4-fe7b-4774-8ced-58f679c5dbd2)
![image](https://github.com/user-attachments/assets/46461113-b011-4cdc-9e00-07efe24031d0)

💻 Technologies Utilisées :  

Pour ce projet, pour la visualisation des résultats nous avons décidés d'utiliser Power Bi. Nous l'avons choisi car n'étant pas familiariser avec ces outils, il était plus facile d'accès pour nous, il est plus intéractif.

Notre projet : 

Pour éxécuter notre projet, vous allez devoir suivre ces étapes : 

Etape 1 : 💪 Cloner le répertoire GitHub
Sur votre ordinateur, cloner notre répot github https://github.com/Gaper8/Challenge48h.git.

Etape 2 : Installation
🛠 Installer power Bi.

Etape 3 : 📂 Importation
Prendre le fichier .csv et le fichier engietest.pbix et importer les deux fichier dans Power Bi. Grâce à cette importation vous verrez la visualisation du résultat.
