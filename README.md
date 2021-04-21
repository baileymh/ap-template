# ap-template
Adventure Path creation tool for Foundry VTT

This is a pre-made module template for the creation of Adventure Paths and Homebrew adventures. It is based on the structure of Pathfinder AP's (3 Parts with Appendices) but can be adopted for other systems. Please read below, as it explains how I set things up, and some suggestions to speed up your adventure creations.

It is set up with compendiums for items, npcs, encounters, journals, and tables.

## How to use this AP Template
This AP template was created to provide some framework for GM's to create and structure their AP games in Foundry VTT. 

Detailed below are tips/how-to for the following:

* Creating a Duplicate folder
* Editing the module.json
* Using Indexs and tips on Linking
* How to easily create a new index with entity links
* How to use Data toolbox to speed up creating journal entries
* Tips on creating Encounters
 

## Creating a Duplicate folder
It is recommended that you create a duplicate of this module folder, and rename the folder and the values within the module.json. This allows you to keep this template for future books, while setting the appropriate name of the module and compendiums ahead of time. 

**For example:** you might copy and rename the **/modules/ap-template/** module folder to **/modules/tg1-thedeadroads/**  - if you were trying to create book 1 of Tyrant's Grasp. 

 

## Editing the module.json
Within the module.json:

You would then rename the name, title, label, path, and module fields.

Rename as appropriate so that the names and labels make sense. Name is how the system refers to it (can't have duplicates), the Label is how it will show up in the Compendium list. Rename .db names.
Foundry will create blank .db of the same name below, if there isn't one found in the folder.


```
"name": "ap-tempalte",
"title": "AP Name 1 - Book Name", 
```

Might change to:

``` 
"name": "tg1-thedeadroads",
"title": "TG 1 - The Dead Roads", 
```

 

While 
``` 
{
 "name": "ap1-items",
 "label": "AP 1 - Items",
 "system": "pf1",
 "path": "packs/ap1-items.db",
 "entity": "Item",
 "module": "ap-template"
}, 
```

Might change to:

```
{
 "name": "tg1-items",
 "label": "TG 1 - Items",
 "system": "pf1",
 "path": "packs/tg1-items.db",
 "entity": "Item",
 "module": "tg1-thedeadroads"

},
```


Make sure that you change the actual .db names within your new module folder to match the above changes, or it will create new blank .db without any information/content.
 

## Indexes, and linking
The items are listed in an organized fashion to help keep things structured. Indexes have been created with a few links, so that the AP book is easily navigated. On most pages I have included a set of links/text at the top to mirror a quick navigation system. 

### Link to Part Index

- Link to Locations
  - Link to Areas within Location
    - Link to Special Text for Areas

The page you are currently on should be in bold, allowing you to easily see where you are relative to the other sections: 

As an example:

- (Index) Part 3: Title
  - H. Location Name
      - H1. Area Name
      - H2. Area Name ( You are on this page) 


## Creating a New AP Index
After you have the entries in the compendium, you may want to create/update the index without dragging and dropping a few dozen links. Included in this module is a macro that let's you specify a compendium and it will general a journal with a list of all the entity links. 

By using this, and a little time organizing/formatting them, it significantly speeds up the creation of a link index. 

### Steps
Open the AP-Template Macro compendium and import Create Entity List. Edit the macro (make sure it is set as script not chat), and replace the key name, to be the name of the compendium. Naming scheme is `moduleName.compendiumName`. 
 

## Linking the entries - Avoiding broken links
It should be easy to expand the links as you add sections. Remember that links are specific to the source.

That is, if you link from an item/journal in your world, it will break if you delete it. 

There are a couple ways you might be able to effeciently navigate this:

* Create and edit everything within the compendium, without importing it to the world. This ensures link are always correct, but each edit may require you to close and reopen the entry.

* Import this journal compendium into the world, replace and rename as needed, add all the text, without links. Export the folder back into the compendium after deleting old/invalid entries. Then edit the newly created entries in the journal, to add links (that will now be correct). 

* Use the Data Toolbox and excel to create the structure for you, and import them. (Recommended - See below for details)
 

## Using Data Toolbox and Excel
Given the sheer volume of entries an AP can have, it might be more prudent to use some automation. Below is a method I've used to help speed things up in creating the journal entries. 

 

Included in the **/modules/ap-template/assets/** folder are three files. One is a .json that can be used with Data Toolbox's Compendium Generation tool, which allows you to create a compendium of entries based on a .csv file. 

Second, there is a outline.txt file that lists the contents of the AP template journal. Using this with notepad++ should let you easily create the outline of the AP by name, using the structure provided (or a new naming scheme if you prefer). 

Using these two together can let you create the outline for your journal as a text document, save that list as a .csv, and then use Data toolbox with the .json and csv to create a journal entries for the book without having to duplicate or manually create each journal. 

It seems complicated, but once you do it, it'll make more sense. Below are the steps in order that I use. 

### Steps
1. Open **Outline.txt** from the module folder.
2. Edit the list to match the outline of the AP.
    - **NOTE:** I usually look at the bookmarks and rename as I go, but there are ways to export a list of Bookmarks from PDFs - use google. 
3. Once the list is finished, copy and paste it into the **Import-Journal.csv,** under the name column.
4. Save the .csv as **APBookName.csv** or whatever is convenient for you. 
5. Use the Show Toolbar macro provided by Data Toolkit (Data Macros Compendium)
6. Set **Entity type** to Journal, **Source file** will be the .csv you just saved, and **Template** will be the **Journal-Template.json** 
7. Set the ccompendium name to whatever you like.
    - **NOTE:** If you set it as the same compendium name for the template journals, it will attempt to overwrite the exisiting journals if you check Merge by Name. Not merging will result in duplicates. 
8. You should now have a compendium full of all the entries you will be making. 
9. From here, you can choose to do either:
   - A. Use the new compendium as the primary filling in the rest.
     - **NOTE:** Be sure to add the indexes, along with the 0.0.X journal entries to the new compendium.
   - B. Drag and Drop the newly created entries into the provided journal compendium, and delete the old entries.
10. Create a new index (see above), and copy-paste those entity links into the appropriate indexes and journals for linking. 
 


## Creating Encounters
The most effective way I've found for organizing and creating encounters is to to Compendium Folders module and create a compendium separated by AP Parts, with Encounters contained within folders for their respective areas. 


### Best Practice Tip
It's recommended to include any npcs and custom magic items (+1 Flaming Greatsword, etc.) in the module, rather than just assume the end-user will have it. 

**Example:**

-TG Encounters
 - Part 1
      - B1. Area Name
        - NPC 1
        - NPC 2
      - B3. Area Name
        - LootNPC with Treasure inside
    - Part 2
        - C1. Area Name
            -Boss 1
            - NPC 3
            - NPC 4
    - Part 3
    - Random Encounters
        - CR X
            - Monster 1
            - Monster 2
        - CR Y
            - Monster 3

Doing it like this allows me to quickly import by area and drag into a scene. Or keep the entire encounter list in the world, and drag the folder over, dropping all entities inside.



If you want to create encounters in this fashion, I've created a folder template for AP use in the **AP 1 - Encounters** compendium.

Alternatively, you can use **AP 1 - NPCs** to toss all your npcs in there if you don't use Compendium Folders. 
