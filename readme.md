# Devoir d'encodage en XML-TEI

Devoir réalisé dans le cadre de l'évaluation du cours d'XML-TEI de Mme Pinche à l'Ecole nationale des chartes. 

## Présentation
Cette édition partielle d'un [texte](https://gallica.bnf.fr/ark:/12148/bpt6k6365618w/f17.item) d'Eugène Sue a été encodée en suivant les [*guidelines*](https://tei-c.org/release/doc/tei-p5-doc/fr/html/index.html) du TEI Consortium. Ces principes d'encodage ont pour but de garantir la pérennité, l'interopérabilité et les possibilités de transformation des données dans un contexte scientifique. L'encodage proposé est donc *TEI conformant*.
## Principaux éléments contenus
- Texte nettoyé issu d'une [OCR](https://en.wikipedia.org/wiki/Optical_character_recognition#:~:text=Optical%20character%20recognition%20or%20optical,billboards%20in%20a%20landscape%20photo)
- Métadonnées complétées dans le *TEI Header*
- Indexation des noms de lieux et de personne
- [ODD](https://wiki.tei-c.org/index.php/ODD) documentée et schéma Relax-NG (dossiers *ODD* et *ODD/out*) générés via [*ODD by example*](http://teic.github.io/TCW/howtoGenerate-fr.html)
- Consignes pour l'établissement de l'ODD:
    - Une règle contraignant l’usage d’un attribut et sa ou ses valeurs
    - Une règle contraignant l’enchaînement de certains éléments
    - Une règle contraignant la valeur d’un attribut ou l’usage d’un élément ou d’un attribut en fonction de son environnement

## Ce repository comprend :
- sue_tei.xml : l'encodage TEI lui-même
- Le dossier odd/ qui comprend:
    - L'ODD (qui comprend documentation et règles d'encodage avec modifications manuelles)
    - L'exportation HTML de la documentation de l'ODD
    - Le dossier out/ qui comprend :
        - Le schéma RNG exporté depuis l'ODD

## Précisions sur l'ODD

Ci-après les consignes concernant l'ODD dans le cadre du devoir et la manière dont elles ont été appliquées : 

- Une règle contraignant l’usage d’un attribut et sa ou ses valeur
Voir : 
```xml
<standOff type="glossaire"/>
```
- Une règle contraignant l’enchaînement de certains éléments
Voir :
```xml
<elementSpec ident="entry" mode="change">
               <content>
                  <sequence preserveOrder="true">
                     <elementRef key="form" minOccurs="1" maxOccurs="1"/>
                     <elementRef key="gramGrp" minOccurs="1" maxOccurs="1"/>
                     <elementRef key="usg" minOccurs="0" maxOccurs="unbounded"/>
                     <elementRef key="def" minOccurs="1" maxOccurs="unbounded"/>
                  </sequence>
               </content>
            </elementSpec>
```
- Une règle contraignant la valeur d’un attribut ou l’usage d’un élément ou d’un attribut en fonction de son environnement
Voir: 
```xml
 <elementSpec ident="person" mode="change">
               <content>
                  <sequence preserveOrder="true">
                     <elementRef key="persName" minOccurs="1" maxOccurs="1"/>
                     <elementRef key="note" minOccurs="0" maxOccurs="1"/>
                     <elementRef key="date" minOccurs="0" maxOccurs="2"/>
                     <elementRef key="idno" minOccurs="0" maxOccurs="1"/>
                  </sequence>
               </content>
            </elementSpec>
```