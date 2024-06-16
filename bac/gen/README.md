```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np


# Chemin vers votre fichier Excel
chemin_fichier_excel = r"\BAC.xlsx"

# Charger les données à partir du fichier Excel
df = pd.read_excel(chemin_fichier_excel)

df_filtered = df

# Liste des notions
notions = [
    'art', 'bonheur', 'devoir', 'état', 'conscience',
    'justice', 'inconscient', 'langage', 'nature', 'liberté',
    'raison', 'science', 'religion', 'technique', 'travail',
    'temps', 'vérité'
]

# Fonction pour calculer le pourcentage de chance que la notion tombe la prochaine fois
def calculer_pourcentage_chance(notion):
    # Compter les occurrences de la notion cible dans les colonnes Notion 1 et Notion 2
    occurrences_notion = df[['Notion 1', 'Notion 2']].stack().value_counts().get(notion, 0)

    # Compter le nombre total d'occurrences de toutes les notions
    total_occurrences = df[['Notion 1', 'Notion 2']].stack().count()

    # Calculer le pourcentage de chance que la notion tombe la prochaine fois
    if total_occurrences > 0:
        pourcentage_chance = (occurrences_notion / total_occurrences) * 100
    else:
        pourcentage_chance = 0

    return pourcentage_chance

# Calculer le pourcentage de chance pour chaque notion
pourcentages_chances = {notion: calculer_pourcentage_chance(notion) for notion in notions}

# Afficher les résultats
for notion, pourcentage in pourcentages_chances.items():
    print(f"Pourcentage de chance que '{notion}' tombe la prochaine fois : {pourcentage:.2f}%")
```

Pourcentage de chance que 'art' tombe la prochaine fois : 5.58%
Pourcentage de chance que 'bonheur' tombe la prochaine fois : 6.23%
Pourcentage de chance que 'devoir' tombe la prochaine fois : 4.28%
Pourcentage de chance que 'état' tombe la prochaine fois : 5.68%
Pourcentage de chance que 'conscience' tombe la prochaine fois : 15.24%
Pourcentage de chance que 'justice' tombe la prochaine fois : 7.16%
Pourcentage de chance que 'inconscient' tombe la prochaine fois : 2.29%
Pourcentage de chance que 'langage' tombe la prochaine fois : 0.96%
Pourcentage de chance que 'nature' tombe la prochaine fois : 4.83%
Pourcentage de chance que 'liberté' tombe la prochaine fois : 11.85%
Pourcentage de chance que 'raison' tombe la prochaine fois : 8.18%
Pourcentage de chance que 'science' tombe la prochaine fois : 5.38%
Pourcentage de chance que 'religion' tombe la prochaine fois : 1.47%
Pourcentage de chance que 'technique' tombe la prochaine fois : 3.77%
Pourcentage de chance que 'travail' tombe la prochaine fois : 2.09%
Pourcentage de chance que 'temps' tombe la prochaine fois : 1.92%
Pourcentage de chance que 'vérité' tombe la prochaine fois : 11.40%