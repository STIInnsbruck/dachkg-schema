# dachkg-schema

The DACH-KG is trying to find a vocabulary to semantically describe touristic content. As a foundation, **schema.org** is the vocabulary of choice. Yet, the expressivity of schema.org is limited and that is why the DACH-KG extends the vocabulary of schema.org and publishes this vocabulary here.

In this repository we host two types of extensions:

* First, in the **schema** folder, the actual extension to schema.org under the *dachkg* namespace. The DACH-KG with all its members agreed on this extension in their meetings and this is assumed as the *official dach-kg extension*.

* The second type, in the **extension** folder, is where it-service providers or touristic service providers can publish their custom extensions to schema.org or the *dachkg* namespace.

# Folder structure

**schema** contains the *dachkg* schema.org extension in a turtle file. Over time, the different releases will be held there (or with the release feature of GitHub).

**extensions** contains the template folder with show case files to extend the vocabulary, called *template-extension*, and the submodules of custom dachkg-extensions by third parties.

# Examples:

This sections gives examples of how to add own vocabulary to the dachkg namespace or the third-party extensions.

## Extending the *dachkg-schema*

1. clone this repository
2. change the file in the **schema** folder according to your suggestion
3. file a Pull Request and wait for the DACH-KG to come back to you and/or accept your request.

## Adding third-party *extensions*

suppose we have a company called **the super tourism data provider** or short **tstdp**.

1. If you have no GithHub account, create one and create a new repository called, named *****-extension** (e.g.: **tstdp-extension**).
   
   [UMUT: or clone ours???]
2. Copy the extension template file (mycompany.ttl) in template-extension folder in this repository and paste into the root of repository. Rename the file as you wish (keep the .ttl file format), and edit the file. 
3. then you decide on a namespace. This could be **https://thesuperprovider.com/ontology/1.0/** abbreviated with **tstdp:**.
4. start adding your classes and properties and make sure to always use **rdfs:subClassOf** to your class definition to make it part of the dachkg vocabulary.
5. Commit and push your extension to your github repository.

Your extension file, based on the provided template would then look like this:

```
@prefix dachkg: <http://http://dachkg.org/ontology/1.0/> .
@prefix schema: <http://schema.org/> .
@prefix tstdp: <https://thesuperprovider.com/ontology/1.0/> .

##Classes

tstdp:Heurigen a rdfs:Class ;
    rdfs:label "Heurigen" ;
    rdfs:comment "A place where you consume housmade wine." ;
    rdfs:subClassOf schema:LocalBusiness .
    rdfs:subClassOf schema:Winery .

#Properties

tstdp:wineOfTheDay a rdf:Property ;
    rdfs:label "wineOfTheDay" ;
    schema:domainIncludes tstdp:Heurigen ;
    schema:rangeIncludes schema:Text ;
    rdfs:comment "The wine of the day sold in a Heurigen." ;
    rdfs:subPropertyOf dachkg:drinkOfTheDay .
```

5. **[UMUT: is there a way to validate their file???] ELIAS: Syntactically, yes, semantically also yes but may be harder.**
6. If you want to submit your third-party extension to the DACH-KG extensions list, please for this repository, add a row with the requested information to the table in [Third-Party-Extensions.md]() and make a pull request.

For more information please contact the editors of this file and repository or write an email to elias.kaerle [a t] sti2.at or umutcan.simsek [a t] sti2.at.
