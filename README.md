Challenge 48h : Analyse des Tweets Clients d'Engie et Paramétrage d'Agents IA

Introduction

Notre Projet à été réalisé dans le cadre du Challenge 48h. Dans ce projet nous avons analyser plus de 500 tweets envoyés par des utilisateurs à engine. Notre premier objectif à été d'extraire de nettoyer les données, pour récupérer seulement les plus importantes. Ensuite, nous avons rajoutés des colonnes grâce à l'ia qui a classifié les tweets selon les sentiments, le niveau d'inconfort et les catégories de chaque tweets. Nous avons aussi conçu un tableau de bord pour permettre la visualisation des données.

Méthodologie

Traitement des données : 

Dans cette partie, nous avons fait le choix de changer le format de la date. Le format passe en J/M/A avec l'heure.
Ensuite pour ce qui est du nettoyage nous avons fait le choix d'enlever les colonnes : 

id : Elle ne nous était pas utile pour l'analyse des tweets et le rendu.

screen_name : Elle ne nous était pas utile pour l'analyse des tweets et le rendu.

name : Elle ne nous était pas utile pour l'analyse des tweets et le rendu.

Les KPI : 

Pour notre Projet, nous avons choisie d'utiliser 5 kpis les voicis : 

- Total des tweets, nous l'avons choisi pour permettre d'avoir une vision d'ensemble.
- Satisfaction moyenne, par rapport à la colonne inconfort. Nous choisissons ce kpi pour permettre d'avoir une vue d'ensemble de la satisfaction des utilisateurs.
- Taux de tweet positif, negatif et neutre. Ce kpi permettra aussi d'avoir une vue plus global sur le nombre d'avis positif ou négatif.
- Nombre de tweets par jour/semaine/mois. Nous avons choisi ce kpi pour pouvoir visualiser l'ensemble des tweets envoyés chaque jour, chaque semaine et chaque mois.
- Fréquence des mentions des comptes Engie. Ce kpi permettra d'avoir une classification de quels comptes engine est le plus et le moins mentionné par les utilisateurs.

L'analyse des sentiments : 

Pour réaliser l'analyse des sentiments nous avons rajouté une colonne pour avoir une classification des tweets selon qu'ils étaient Positif, Neutre et Négatif.

Pour réaliser cette classification voici comment nous avons fait : 

Nous avons utilisé un agent IA basé sur Mistral pour effectuer une classification automatique des tweets. Il ajoute une colonne sentiment et l'agent Ia choisi en fonction du Tweet si il est Positif, neutre ou négatif.

Processus de création des agents IA :

    1. Logique utilisée pour détecter les types de réclamations

L’agent IA repose sur un modèle NLP qui analyse le contenu des tweets et extrait les informations suivantes :

        "category": "Facturation / Gaz / Électricité / Contrat / Autre", permet de connaitre la catégorie dans laquelle se situe le problème de l'utilisateur.
        "sentiment": "Positif / Neutre / Négatif", analyse le sentiment de l'utilisateur en fonction de son tweet.
        "resolu": "Oui / Non", Cette information permet de savoir grâce à des phrases comme "merci", ou "problème réglé", si le problème est résolu ou non.
        "inconfort": Un score de 0 à 100, il permet de savoir à quel point le problème de l'utilisateur lui créer des problèmes.
        "urgence": true / false, permet de savoir si c'est une urgence grâce à des mots clés.

Les prompts ou fine-tuning réalisés :

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

Des exemples d’interactions générées par l’agent : 


Technologies : 

Pour ce projet, pour la visualisation des résultats nous avons décidés d'utiliser Power Bi. Nous l'avons choisi car n'étant pas familiariser avec ces outils, il était plus facile d'accès pour nous, il est plus intéractif.

Notre projet : 

Pour éxécuter notre projet, vous allez devoir suivre ces étapes : 

Etape 1 : 
Sur votre ordinateur, cloner notre répot github https://github.com/Gaper8/Challenge48h.git.

Etape 2 :
installer power Bi.

Etape 3: 
