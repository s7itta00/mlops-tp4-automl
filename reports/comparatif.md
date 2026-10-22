# Comparatif des approches - projet fraude (TP04)

Date de consultation de la documentation : 22 octobre 2026

| Approche | F1 test | Temps humain | Temps machine | Cout estime (source, date) | Explicabilite | Export / reversibilite |
|---|---|---|---|---|---|---|
| Logistique (ref.) | 0.7407 | ~2 min | 0.33 s | 0 (poste local) | Maximale | Total |
| Manuel (TP2) | 0.8669 | ~30 min (essais TP2) | 2.3 s | 0 (poste local) | Moyenne/Bonne | Total |
| FLAML 60 s | 0.8582 | ~5 min | 60 s | 0 (poste local) | Moyenne/Basse | Total |
| Vertex AI AutoML | non mesure | ... | ... | Entrainement tabulaire : 21,252 USD par heure de noeud (cloud.google.com/vertex-ai/pricing, 22/10/2026) | Bonne (Shapley echantillonne) | Partiel : export des artefacts possible pour certains types (docs.cloud.google.com/vertex-ai/docs/explainable-ai) ; a verifier pour le tabulaire |
| SageMaker Autopilot | non mesure | ... | ... | A verifier (aws.amazon.com/sagemaker/pricing) | Bonne (SHAP via Clarify) | A verifier |
| Azure Automated ML | non mesure | ... | ... | Pas de surcout AutoML : on paie le calcul + stockage et services associes (azure.microsoft.com/pricing/details/machine-learning, 22/10/2026) | A verifier | A verifier |

## Commentaire (5 lignes)

1. Regression logistique : a garder comme reference et quand l'explicabilite et la rapidite priment (secteur regule, petit projet).
2. Reglage manuel : justifie quand l'equipe connait les donnees et veut controler chaque choix ; le cout est surtout du temps humain.
3. FLAML local : bon compromis quand on veut tester plusieurs familles vite, sans cout cloud ni envoi de donnees a l'exterieur.
4. Plateformes managees : utiles pour une entreprise deja chez le fournisseur, avec besoin de deploiement, monitoring et conformite integres ; attention au verrouillage et a la facture a l'heure.
5. Dans tous les cas, l'AutoML ne remplace pas le jugement : la fuite du bloc D passe inapercue, donc il faut valider les variables soi-meme.