# dataBNF-sparql-query

Répertoire de requêtes permettant de trouver les notices d'autorités relatives à la discipline historique depuis le site  http://data.bnf.fr/sparql/

## Liens vers les données de la BNF

* [Années principales de l'histoire de France](http://data.bnf.fr/sparql?default-graph-uri=&query=PREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fsujet+%3Flabel%0D%0AWHERE+%7B%0D%0A++%3Fsujet+dcterms%3AisPartOf+%3Chttp%3A%2F%2Fdata.bnf.fr%2Fvocabulary%2Fscheme%2Fr166%3E+%3B%0D%0A++skos%3AprefLabel+%3Flabel.%0D%0A%0D%0A%0D%0A++FILTER+%28regex%28str%28%3Flabel%29%2C%22%5EFrance+--+.*%5B0-9%5D%5B0-9%5D%5B0-9%5D%22%29%29%0D%0A%7D%0D%0AORDER+BY+%3Flabel&format=text%2Fhtml&timeout=0&should-sponge=&debug=on)

* [Événements majeurs de la ville de Paris](http://data.bnf.fr/sparql?default-graph-uri=&query=%0D%0APREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fsujet+%3Flabel%0D%0AWHERE+%7B%0D%0A++%3Fsujet+skos%3AprefLabel+%3Flabel.%0D%0A%0D%0A%0D%0A++FILTER+%28regex%28str%28%3Flabel%29%2C%22%5EParis+.*+--+.*%5B0-9%5D%5B0-9%5D%22%29%29%0D%0A%7D%0D%0AORDER+BY+%3Flabel&format=text%2Fhtml&timeout=0&should-sponge=&debug=on)

* [Guerres, batailles, soulèvements](http://data.bnf.fr/sparql?default-graph-uri=&query=PREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fsujet+%3Flabel+%3Flabel2+%3Flabel3%0D%0AWHERE+%7B%0D%0A++%3Fsujet+dcterms%3AisPartOf+%3Chttp%3A%2F%2Fdata.bnf.fr%2Fvocabulary%2Fscheme%2Fr166%3E+%3B%0D%0A++skos%3AprefLabel+%3Flabel.%0D%0A%0D%0A++OPTIONAL+%7B%0D%0A%0D%0A++++%3Fsujet+skos%3Anarrower+%3Furi2.%0D%0A++++%3Furi2+skos%3AprefLabel+%3Flabel2%0D%0A%0D%0A++++++OPTIONAL+%7B%0D%0A%0D%0A++++%3Furi2+skos%3Anarrower+%3Furi3.%0D%0A++++%3Furi3+skos%3AprefLabel+%3Flabel3%0D%0A%0D%0A++++%7D%0D%0A%0D%0A%7D%0D%0A%0D%0A++FILTER+%28%28regex%28str%28%3Flabel%29%2C%22%5B0-9%5D.*bataille%22%29%29+%7C%7C+%28regex%28str%28%3Flabel%29%2C%22%5B0-9%5D.*guerre%22%29%29+%7C%7C+%28regex%28str%28%3Flabel%29%2C%22%5B0-9%5D.*si%C3%A8ge%22%29%29+%29%0D%0A%7D%0D%0AORDER+BY+%3Flabel&format=text%2Fhtml&timeout=0&should-sponge=&debug=on)

* [Principaux courants historiographiques](http://data.bnf.fr/sparql?default-graph-uri=&query=PREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0ASELECT+DISTINCT+%3Fsujet+%3Flabel+%3Flabel2+%3Flabel3%0D%0AWHERE+%7B%0D%0A++%3Fsujet+dcterms%3AisPartOf+%3Chttp%3A%2F%2Fdata.bnf.fr%2Fvocabulary%2Fscheme%2Fr166%3E+%3B++%23Recherche+parmis+l%27ensemble+des+noms+communs+du+Rameau%0D%0A++skos%3AprefLabel+%3Flabel.+%23Cherche+la+forme+retenue+de+ce+mot+sujet+et+l%27affiche+dans+la+colonne+%3Flabel%0D%0A++%0D%0A++%0D%0A%0D%0A++OPTIONAL%7B%0D%0A++%3Fsujet+skos%3Anarrower+%3Furi2.+%23Pour+chaque+mot+sujet+%3A+recherche+l%27ensemble+des+%C2%AB+sous-mots+sujets+%C2%BB%0D%0A++%3Furi2+skos%3AprefLabel+%3Flabel2+%23Cherche+la+forme+retenue+des+sous-mots+sujet+et+l%27affiche+dans+la+colonne+%3Flabel2%0D%0A%0D%0A+++++OPTIONAL%7B%0D%0A++++++++%3Furi2+skos%3Anarrower+%3Furi3.++%23Pour+chaque+sous-sujet+%3A+recherche+l%27ensemble+des+%C2%AB+sous-sous-mot+sujet+%C2%BB%0D%0A++++++++%3Furi3+skos%3AprefLabel+%3Flabel3+%23Cherche+la+forme+retenue+pour+l%27ensemble+des+sous-sous-mot+sujet+et+l%27affiche+dans+la+colonne+%3Flabel3%0D%0A%0D%0A++++%7D%0D%0A%0D%0A++%7D%0D%0A++%0D%0A++FILTER+regex%28str%28%3Flabel%29%2C%27istoriographie%27%29+%23Recherche+parmis+les+mots+sujet+comprenant+le+terme+%27istoriographie%27%0D%0A++%0D%0A%7D%0D%0AORDER+BY+%3Flabel&format=text%2Fhtml&timeout=0&should-sponge=&debug=on)

* [Mots sujets relatifs à l'histoire militaire](http://data.bnf.fr/sparql?default-graph-uri=&query=PREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fsujet+%3Flabel+%3Flabel2+%3Flabel3%0D%0AWHERE+%7B%0D%0A++%3Fsujet+dcterms%3AisPartOf+%3Chttp%3A%2F%2Fdata.bnf.fr%2Fvocabulary%2Fscheme%2Fr166%3E+%3B%0D%0A++skos%3AprefLabel+%3Flabel.%0D%0A%0D%0A++OPTIONAL+%7B%0D%0A%0D%0A++++%3Fsujet+skos%3Anarrower+%3Furi2.%0D%0A++++%3Furi2+skos%3AprefLabel+%3Flabel2%0D%0A%0D%0A++++++OPTIONAL+%7B%0D%0A%0D%0A++++%3Furi2+skos%3Anarrower+%3Furi3.%0D%0A++++%3Furi3+skos%3AprefLabel+%3Flabel3%0D%0A%0D%0A++++%7D%0D%0A%0D%0A%7D%0D%0A%0D%0A++FILTER+regex%28str%28%3Flabel%29%2C%22%5EHistoire+militaire%22%29%0D%0A%7D%0D%0AORDER+BY+%3Flabel&format=text%2Fhtml&timeout=0&should-sponge=&debug=on)

* [Mots sujets relatifs à l'histoire sociale](http://data.bnf.fr/sparql?default-graph-uri=&query=PREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fsujet+%3Flabel+%3Flabel2+%3Flabel3%0D%0AWHERE+%7B%0D%0A++%3Fsujet+dcterms%3AisPartOf+%3Chttp%3A%2F%2Fdata.bnf.fr%2Fvocabulary%2Fscheme%2Fr166%3E+%3B%0D%0A++skos%3AprefLabel+%3Flabel.%0D%0A%0D%0A++OPTIONAL+%7B%0D%0A%0D%0A++++%3Fsujet+skos%3Anarrower+%3Furi2.%0D%0A++++%3Furi2+skos%3AprefLabel+%3Flabel2%0D%0A%0D%0A++++++OPTIONAL+%7B%0D%0A%0D%0A++++%3Furi2+skos%3Anarrower+%3Furi3.%0D%0A++++%3Furi3+skos%3AprefLabel+%3Flabel3%0D%0A%0D%0A++++%7D%0D%0A%0D%0A%7D%0D%0A%0D%0A%0D%0A++FILTER+regex%28str%28%3Flabel%29%2C%22%5EHistoire+sociale%22%29%0D%0A%7D%0D%0AORDER+BY+%3Flabel&format=text%2Fhtml&timeout=0&should-sponge=&debug=[on)

* [Mots sujets relatifs à l'histoire économique](http://data.bnf.fr/sparql?default-graph-uri=&query=PREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fsujet+%3Flabel+%3Flabel2+%3Flabel3%0D%0AWHERE+%7B%0D%0A++%3Fsujet+dcterms%3AisPartOf+%3Chttp%3A%2F%2Fdata.bnf.fr%2Fvocabulary%2Fscheme%2Fr166%3E+%3B%0D%0A++skos%3AprefLabel+%3Flabel.%0D%0A%0D%0A++OPTIONAL+%7B%0D%0A%0D%0A++++%3Fsujet+skos%3Anarrower+%3Furi2.%0D%0A++++%3Furi2+skos%3AprefLabel+%3Flabel2%0D%0A%0D%0A++++++OPTIONAL+%7B%0D%0A%0D%0A++++%3Furi2+skos%3Anarrower+%3Furi3.%0D%0A++++%3Furi3+skos%3AprefLabel+%3Flabel3%0D%0A%0D%0A++++%7D%0D%0A%0D%0A%7D%0D%0A%0D%0A++FILTER+regex%28str%28%3Flabel%29%2C%22%5EHistoire+%C3%A9conomique%22%29%0D%0A%7D%0D%0AORDER+BY+%3Flabel&format=text%2Fhtml&timeout=0&should-sponge=&debug=on)

* [Principales thématiques historiques](http://data.bnf.fr/sparql?default-graph-uri=&query=PREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0D%0ASELECT+DISTINCT+%3Fsujet+%3Flabel+%231%C3%A8re+colonne+%3D+l%27URL+de+la+notice+%28%3Fsujet%29+%C2%A6+2e+colonne+%3D+mot+sujet+%28%3Flabel%29%0D%0AWHERE+%7B%0D%0A++%3Fsujet+dcterms%3AisPartOf+%3Chttp%3A%2F%2Fdata.bnf.fr%2Fvocabulary%2Fscheme%2Fr166%3E+%3B++%23Recherche+parmis+l%27ensemble+des+noms+communs+du+Rameau%0D%0A%0D%0A++skos%3AprefLabel+%3Flabel.++%23+Selectionne+la+forme+retenue+du+mot+sujet+qui+sera+affich%C3%A9+dans+colonne+%3Flabel%0D%0A%0D%0A++FILTER+%28regex%28str%28%3Flabel%29%2C%22%5EHistoire%22%29+%26%26+%21regex%28str%28%3Flabel%29%2C%22dr%C3%B4le%22%29%29++%23Recherche+les+mots+sujets+%28%3Flabel%29+comprenant+le+terme+Histoire+et+n%27ayant+pas+le+mot+sujet+de+litt%C3%A9rature+%3A+%22Histoire+dr%C3%B4le%22%0D%0A%7D%0D%0AORDER+BY+%3Flabel+%23+trier+les+resultats+par+mots+sujets+et+par+ordre+alphab%C3%A9tique&format=text%2Fhtml&timeout=0&should-sponge=&debug=on)

* [Régimes politiques, règnes, ministères français](http://data.bnf.fr/sparql?default-graph-uri=&query=SELECT+DISTINCT+%3Fsujet+%3Flabel%0D%0AWHERE+%7B%0D%0A++%3Fsujet+skos%3AprefLabel+%3Flabel.%0D%0A++%0D%0A++FILTER+%28regex%28str%28%3Flabel%29%2C+%22%5EFrance+--+%5B0-9%5D%22%29%29%0D%0A%7D&format=text%2Fhtml&timeout=0&should-sponge=&debug=on)

