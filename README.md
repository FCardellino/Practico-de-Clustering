# Practico de Clustering

Para la realización del siguiente práctico se utilizo el corpus de La Voz del Interior.
Los pasos seguidos fueron los siguientes:

Paso 1:
Se procedió a realizar el preprocesamiento del corpus mediante SpaCy:

+En primer término se dividió el corpus entre "Título" y "Cuerpo" de los documentos (cada noticia), mediante la función "corpus_iterator":
def corpus_iterator(corpus_file):
    document = {
        "title": None,
        "body": None
    }

    with open(corpus_file, "r") as fh:
        for line in fh:
            if line.strip() == "-":
                new_document = True
                document = {
                    "title": None,
                    "body": None
                }
            elif new_document:
                document["title"] = line.strip()
                new_document = False
            else:
                document["body"] = line.strip()
                yield document
                
+Luego se tomó el "Cuerpo" del documento y mediante SpaCy se procedió a "limpiarlo, para lo cual:
-
-se eliminaron stopwords y demás caracteres vaciós
-se
se realizo la respectiva tokenización
-se eliminaron las stopwords y demás caracteres vaciós
-se aplicó lowercase a todas las palabras
-se obtuvo el lemma, pos, dep y head de los tokens

Paso 2:
  Se procedió al diseño de la matriz mediante la función build_cooccurrence_matrix, que devuelve una matriz de co-ocurrencia de palabras:
    -Para ello se utilizaron unicamente los tokens obtenidos previamentes, que fueron almacenados en una variable denominada "contexto" mediante la función conell_iterator
    -Se tuvo en cuenta una ventana de 5
    -La ponderación fue escalada
    -Y se consideró un máximo de 5000 palabras
    
    
Paso 3:
  Se aplicó un método de reducción de dimensionalidades:
  
  
  
Paso 4:
  Se procedió a armar los clusters:
    -Para ello se utilizó el algoritmo de kmeans de sklearn para crear clusters. Se iteró a 3 valores.
    
