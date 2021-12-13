# Exercices sur les transactions

Pour réaliser les exercices de ce laboratoire, il faut utiliser deux sessions connectées sur votre base de données.



## Préambule

Créer une table `Membres` qui contient les colonnes id de type `NUMBER` (clé primaire), `Nom` de type `VARCHAR2(30)`, Prénom de type `VARCHAR2(25)` et Montant de type `NUMBER(6,2)`.
Y insérer les tuples `(100, 'Dupont', 'Jean', 100.6)`, `(200, 'Dubois', 'Marc', 50)`, `(300, 'Martin', 'Jules', 75.5)` et `(400, 'Tartempion', 'Charles', 25.25)`.



```sql

COMMIT;
```



## Transaction 1

Imaginer un ensemble de commandes permettant d'illustrer qu'il n'y a pas de lecture impropre, par défaut, dans Oracle.



| Session A | Session B |
| --------- | --------- |
|           |           |
|           |           |
|           |           |

> 



## Transaction 2

Imaginer un ensemble de commandes permettant d'illustrer qu'il n'y a pas de pertes de mises à jour, par défaut, dans Oracle.

| Session A | Session B |
| --------- | --------- |
|           |           |
|           |           |
|           |           |
|           |           |

> 



## Transaction 3

Imaginer un ensemble de commandes permettant d'illustrer qu'il est possible d'obtenir des lectures non reproductibles dans Oracle.

| Session A | Session B |
| --------- | --------- |
|           |           |
|           |           |
|           |           |
|           |           |
|           |           |

> 



## Transaction 4

Imaginer un ensemble de commandes permettant de provoquer une étreinte fatale (deadlock) dans le cadre de deux transactions concurrentes.

| Session A | Session B |
| --------- | --------- |
|           |           |
|           |           |

> 

Ou 

| Session A | SESSION B |
| --------- | --------- |
|           |           |
|           |           |
|           |           |
|           |           |

> 

## Transaction 5

Imaginer un ensemble de commandes permettant d'illustrer qu'il est possible d'empêcher les lectures non reproductibles.

| Session A | Session B |
| --------- | --------- |
|           |           |
|           |           |
|           |           |
|           |           |
|           |           |

> 4 niveaux d'isolation :
>
> - 
> 
> 

## Transaction 6

Effectuer les tests ci-dessous. Aux endroits indiqués par => expliquez la réaction d'Oracle.

| SESSION A                                             | SESSION B                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------ |
| UPDATE Membres SET Nom ='xxx'<br/>	WHERE id = 200; |                                                              |
| Spécifier le type de verrou :  ...                    |                                                              |
|                                                       | UPDATE Membres SET Nom ='yyy'<br/>							WHERE id = 200;<br> Ceci implique : ... |
| COMMIT; ...                                           |                                                              |
|                                                       | COMMIT; => ....                                              |

Expliquez le résultat de

```sql
SELECT * FROM Membres WHERE id = 200;
```

> 



## Transaction 7

Effectuer les tests ci-dessous. Aux endroits indiqués par => expliquez la réaction d'Oracle.

| **SESSION A**                        | **SESSION B**                     |
| ------------------------------------ | --------------------------------- |
| SELECT * FROM Membres FOR UPDATE;    |                                   |
| => Spécifier le type de verrou : ... |                                   |
|                                      | SELECT * FROM Membres FOR UPDATE; |
|                                      | ....                              |



## Transaction 8

Effectuer les tests ci-dessous. Aux endroits indiqués par => expliquez la réaction d'Oracle.

| SESSION A                                     | SESSION B                                     |
| --------------------------------------------- | --------------------------------------------- |
| SELECT * FROM Membres <br/>FOR UPDATE NOWAIT; |                                               |
| => Spécifier le type de verrou : ...          |                                               |
|                                               | SELECT * FROM Membres <br/>FOR UPDATE NOWAIT; |
|                                               | => ...                                        |

