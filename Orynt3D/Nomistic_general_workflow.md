# Nomistic's historical wargaming

_**Editor's note**: the original version of this guide that you can find in the Tips and Tricks Discord channel was written before "attributes" were available. This is an updated version, using Orynt3D version 0.14.2-win32.

After working with Orynt3D for a few months, I've finally put order where chaos was. In the process, I had to come up with a workflow to organise efficiently all the free and bought models I've been collecting.

**DISCLAIMER**: this is the workflow that works for me. It was refined through trials and errors. I wanted to share this with the community in the goal of inspiring others to build their own structure. Each of our collection and our goals are different.

## Folder structure

First thing is my folder structure.

All my models are in a single source (in Orynt3D parlance). In that folder, I have only folders, one for each creator I've collected models from. I treat as creator large studios like Loot, Arch Villain, RN Estudios, but also Thingiverse creators that published only a single model (so far). That means a lot of folders.

Within a creator's folder, I will create a subfolder for each model I want to see in Orynt3D. I will also drag from my browser the url of the creator's home page(s) from Thingiverse, Wargaming3D, Cults, Printables, MyMiniFactory, etc. If I liked a model enough to download it, there might be more from that creator that I will want to grab in the future.

For the model folder, I will flatten the structure, meaning if there is subfolders for supported versions, different sizes, images, etc, I bring them all into a single folder, making sure the names of the files will let me distinguish between the various versions. If there's name collisions, I will use "Power Rename" in the PowerToys suite from Microsoft. It allows you to rename folders and/or files in batch, and can use regular expressions to target only the files you want.
At this stage, if the source of the model had pictures, I will select the image that should be used as thumbnail by pre-pending 0- in front of its name, to make sure it's the one picked up by Orynt3D. If there's no preview, I'll save a screenshot using [Papa's Best STL viewer](https://papas-best.com/stlviewer_en).

<Figure
  src="/img/guide/nomistic/folder-layout.png"
  title="Folder and file layout"
  w={640}
  h={139}
/>

Once I'm happy with the folder/model structure, it's time to switch to Orynt3D to assign attributes to my models.

## Attribute system

Inspired by ThatRobHuman, I've created a set of set of `attributes`. The first `attribute` assigned to every model is the `type`. 

Then most of the model types will be assigned a `genre:` and a `faction:`. And finaly all models tagged `gaming miniatures:` would be further described with tags for `race:`, `gender:`, `class:`, etc. So far, here are the keywords that I use:

- `type:`
- `genre:`
- `faction:`
- `race:`
- `gender:`
- `class:`
- `holding:`
- `wearing:`
- `feature:`

`Feature:` is bit of a catch all where I want to capture stuff like if the model has wings, antlers is dual-wielding or is nswf.

<Figure
  src="/img/guide/nomistic/using-tags.png"
  title="Tags on a model"
  w={640}
  h={333}
/>

To help in tagging, I've come up with a series of saved searches for models not already tagged. For example, when adding a genre, I filter with this query `!#"genre:**" !(#"type: 3d print**" | #"type: hobby tool")`. Then in the tag browser, I will filter on the `genre:` tags and then it's just a matter of drag'n dropping the models on the applicable `genre:` tag. I've numbered these searches in an order that funnels down from the most generic to the more specific tags and collected them under - Model organization.

<Figure
  src="/img/guide/nomistic/tag-search.png"
  title="Full set of tags and search query"
  w={640}
  h={759}
/>

And that's it. Hope you found this helpful.

## Using saved searches to find unprocessed models

In processing my models, I put the folders/files into shape, then run the following saved searches one after the other.

1. No preview `! f:"*.jpg" & ! f:"*.png" & ! f:"*.gif" & ! f:"*.jpeg" & ! f:"*.jfif" & ! f:"*.webp"`
2. No type assigned `! attr:"type"="**"`
3. No genre assigned `!attr:"genre"="**" !(attr:"type"="3d print**" | attr:"type"="hobby tool" | attr:"type"="replacement part" | attr:"type"="game accessory" | attr:"type"="utility")`
4. No gender assigned `!attr:"gender"="**" attr:"type"="gaming miniature"`
5. No faction assigned `(attr:"type"="gaming miniature" | attr:"type"="vehicle**") !attr:"faction"="**`
6. No race assigned `!attr:"race"="**" attr:"type"="gaming miniature"`
7. No class assigned `!attr:"class"="**" attr:"type"="gaming miniature"`
8. No held item `!attr:"holding"="**" attr:"type"="gaming miniature"`
9. No worn item assigned `!attr:"wearing"="**" attr:"type"="gaming miniature"`

So for example, when selecting search 2 - No type assigned, I open on the sidebar the type attribute and then multi-select the models in the search result and drag them on the desired type. Rinse and repeat with every attribute.
Attributes do all the heavy lifting.

<Figure
  src="/img/guide/nomistic/tag-counts.png"
  title="Full set of tags and attributes"
  w={640}
  h={799}
/>

<Figure
  src="/img/guide/nomistic/database-overview.png"
  title="Resultant attributes in the database."
  w={640}
  h={302}
/>

import Figure from "@/c/decoratives/Figure";
import DocLayout from "@/c/layout/DocLayout";
export default ({ children }) => <DocLayout>{children}</DocLayout>;

