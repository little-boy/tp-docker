# TP Docker

## Objectifs 
- Être capable de containeriser un script Python,
    - Construire une image,
    - Exécuter des scripts à travers Docker

## Instructions

- Créer un repository sur Github 
    - son nom doit être poec-tp-docker
- Créer un script python src/calc.py
    - Il doit contenir une fonction apply_vat(price, percent)
    - Cette fonction doit, comme son nom l'indique, appliquer un pourcentage de TVA
    ex: apply_vat(100, 20) == 120
    - le pourcentage de TVA doit être compris entre 0 et 100,
        - Si le % de TVA n'est pas compris entre ces bornes, 
        - Ou si le % de TVA n'est pas un nombre,
        - la fonction doit lancer une exception ([doc](https://docs.python.org/3/tutorial/errors.html))
    - price doit être un nombre positif,
        - si ce n'est pas le cas, la fonction doit lancer une exception
    scaffolding de la fonction : 
```python 
def apply_percent(price: float, percent: float):
    if not isinstance(price, float):
        raise ValueError(f'Price (${price}) is not a number')

    if price < 0:
        raise ValueError(f'Price (${price}) is negative')
    
    # code logic
```    
- Créer des tests unitaires pour la fonction
    - vous devez tester à minima que la fonction renvoie la bonne valeur pour :
        - price = 100, percent = 20,
        - price = 55.25, percent = 5.5,
        - price = 0, percent = 10,
        - price = -10.99, percent = 10,
        - price = 'wrong value', percent = 10
        - price = 100, percent = -10
        - price = 100, percent = 110

- Votre fonction et vos tests doivent être exécutables via une commande Docker,
  - Aide : 
    - (avec l'image tp-docker préalablement buildée) `docker run -it tp-docker python src/main.py 100 20`
    - permet d'exécuter le script main.py, avec les arguments 100 et 20

- Une documentation doit contenir un readme.md explicite (permettant de comprendre l'objet du projet, comment le faire tourner)
