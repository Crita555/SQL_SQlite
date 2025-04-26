# **Rédaction des requêtes SQL**

Dans ce projet, j'ai réalisé des requêtes SQL sur les données d'une société d'assurance afin de mieux comprendre ses clients en analysant le marché de l'assurance habitation et d'aider à la prise de décision stratégique. La base de donnée que j'ai utilisé c'est SQLite.

### Requête 1 : Lister les numéros de contrats (contrat_ID) avec leur surface ?
**SELECT** Contrat_ID, Surface  
**FROM** Contrat AS C  
**INNER** **JOIN** Region AS R ON C. Code_dep_code_commune = R. 
Code_dep_code_commune    
**WHERE** com_nom_maj_court = ‘CAEN’ ; 


![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_1.png)

### Requête 2 : Lister les numéros de contrats avec le type de contrat et leur formule pour les maisons du département 71 ?
**SELECT** Contrat_ID, Type_contrat, Formule,type_local,dep_code  
**FROM** Contrat  
**INNER** **JOIN** Region ON contrat.Code_dep_code_commune = 
Region.Code_dep_code_commune  
**WHERE** Type_local = 'Maison’ AND dep_code = 71 ; 

![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_2.png)

### Requête 3 :  Lister le nom des régions de France ?
**SELECT** **DISTINCT** reg_nom 
**FROM** Region ; 

![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_3.png)

### Requête 4 : Quels sont les 5 contrats qui ont les surfaces les plus élevées ? 
**SELECT** contrat_ID,Surface   
**FROM**  Contrat  
**ORDER BY** surface Desc LIMIT 5 ; 

![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_4.png)

### Requête 5 : Quel est le prix moyen de la cotisation mensuelle ? 
**SELECT** **AVG** (Prix_cotisation_mensuel) AS  
prix_moyen_de_la_cotisation_mensuelle   
**FROM** Contrat ;

![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_5.png)

### Requête 6 : Quel est le nombre de contrats pour chaque catégorie de prix de la valeur déclarée des biens ?
**SELECT** Valeur_declaree_biens, **COUNT**(Contrat_ID) **AS** nombre_de_contrats    
**FROM** contrat   
**GROUP BY** valeur_declaree_biens; 

![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_6.png)

### Requête 7 : Quel est le nombre de formules “integral” sur la région Pays de la Loire ? 
**SELECT COUNT** (Formule) **AS** nombre_de_formule,reg_nom  
**FROM** contrat   
**INNER JOIN** Region **ON** contrat.Code_dep_code_commune = 
region.Code_dep_code_commune 
**WHERE** reg_nom = 'Pays de la Loire' **And** Formule = 'Integral' ; 

![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_7.png)

### Requête 8 : Lister les numéros de contrats avec le type de contrat et leur formule pour les maisons du département 71 ?
**SELECT** contrat_ID, Type_contrat,formule, Type_local, dep_code **AS** 
departement   
**FROM**contrat   
**RIGHT OUTER JOIN** Region **ON** contrat.Code_dep_code_commune = 
region.Code_dep_code_commune   
**WHERE** dep_code = 71   
**AND** type_local ='Maison'; 

![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_8.png)

### Requête 9 :Quelle est la surface moyenne des contrats à Paris ?
**SELECT** **AVG** (Surface) AS Surface_moyenne  
**FROM** contrat 
**INNER JOIN** Region **ON** contrat.Code_dep_code_commune = 
region.Code_dep_code_commune   
**WHERE** aca_nom = 'Paris'; 

![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_9.png)

### Requête 10 :Classement des 10 départements où le prix moyen de la cotisation est le plus élevé ?
**SELECT** dep_nom **AS** Départements ,AVG(prix_cotisation_mensuel) **AS** 
prix_moyen_de_la_cotisation   
**FROM** region   
**INNER JOIN** contrat **ON**region.Code_dep_code_commune = 
contrat.Code_dep_code_commune   
**GROUP BY** Départements   
**ORDER BY** prix_moyen_de_la_cotisation **desc limit** 10; 

![Résultat](1C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_10.png)

### Requête 11 :Liste des communes ayant eu au moins 150 contrats ?  
**SELECT** com_nom_maj_court,**COUNT** (contrat_ID) **AS** nombre_contrat   
**FROM** region   
**INNER JOIN** contrat **ON** contrat.Code_dep_code_commune = 
region.Code_dep_code_commune   
**GROUP BY** com_nom_maj_court   
**HAVING COUNT** (contrat_ID) >=150; 

![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_11.png)

### Requête 12 :Quel est le nombre de contrats pour chaque région ?  
**SELECT DISTINCT** reg_nom ,**COUNT** (contrat_ID) **as** nombre_contrat   
**FROM** region   
**LEFT JOIN** contrat **ON** (contrat.Code_dep_code_commune = 
region.Code_dep_code_commune)   
**ORDER BY**reg_nom; 
 
![Résultat](C:\Users\Administrateur\Documents\Data analyst\GitHub_Projet\Sqlite_sql\SQL\Image requete_12.png)
