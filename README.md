(Inspired by the infamous "How To Write Unmaintainable Code": http://www2.imm.dtu.dk/courses/02161/2019/files/how_to_write_unmaintainable_code.pdf)

# Introduction

_Never ascribe to malice, that which can be explained by incompetence._

In the interests of creating employment opportunities in the mechanical design field, I am passing on these tips from the masters on how to create CAD that is so difficult to maintain, that the people who come after you will take years to make even the simplest changes. Further, if you follow all these rules religiously, you will even guarantee *yourself* a lifetime of employment, since no one but you has a hope in hell of maintainin the CAD. Then again, if you followed all these rules religiously, even you wouldn't be able to maintain the CAD!

You don't want to overdo this. Your code should not *look* hopelessly unmaintainable, just *be* that way. Otherwise it stands the risk of being deleted and replaced, or exported to STEP and re-imported.

# General Principles

_Quidquid latine dictum sit, altum sonatur._
- Whatever is said in Latin sounds profound.

To foil your fellow designer, you have to understand how he thinks. He has your giant assembly file. He has no time to thumb through it all, much less understand it. He wants to rapidly find the place to make the change, make it, get out, and have no unexpected side effects.

He views your CAD through a toilet paper tube. He can only see a tiny piece of the Feature Tree at a time. You want to make sure he can never get at the big picture by doing that. You want to make it as hard as possible for him to find the code he is looking for. But even more important, you want to make it as awkward as possible for him to safely *ignore* anything.

Designers are lulled into complacency by convention. But every once in a while, by subtly violating convention, you force him to inspect every constraint of your sketches with a magnifying glass.

You might get the idea that every CAD program makes models unmaintainable -- not so, only if properly misused.

# Naming

_"When I use a word," Humpty Dumpty said, in a rather scornful tone, "it means justwhat I choose it to mean - neither more nor less."_
- Lewis Carroll -- Through the Looking Glass, Chapter 6

Some skill in writing unmaintainable CAD is mis-naming things in the tree. They don't matter at all to the CAD program, they exist only as comments for the designer. That gives you latitude to use them to befuddle the CAD Lackey.

## When in Doubt, Default it Out

Use the default names for features. Sketch1, Sketch2, Revolve-7, Boss-Extrude23. All of these are wonderful names, require no typing, and in a many-feature-dense part, convey nothing about what they do unless individually inspected. If the "Top" plane of your part is actually better described as the "bottom", leave it. Do not rename it. If the "Right" would be better described as "Right Midplane" or "Midplane", don't touch it!

## Keep it flat

Don't put things in folders. Keep them laid out in the open for all to see, at all times. If anyone questions your choices to do this, remind them that you need to open and close folders, and that it's inconvenient to re-arrange features into folders if, for instance, a feature needs to be added inbetween others.

## Pick up a second language

Rename things in different languages. Japanese is especially wonderful as some older versions of SOLIDWORKS at least would not permit you to have assemblies with parts having both japanese and english characters.

## Invent an alien language

Just start typing. Go nuts. `asdf` is a perfectly valid name to the compiler.

## Misdirection

Rename things to what they aren't. Rename a boss-extrude to Revolved-77. This is even better when the part is only a couple features long, so that the 77 conveys an air of struggle that finally came to a head in the triumphant 10 lines of features.

# Structural Design

_"The cardinal rule of writing unmaintainable [CAD] is to specifiy each fact in as many places as possible and in as many ways as possible."_
- Roedy Green

## Never lay things out.
Layout AKA Skeleton sketches are the ultimate prevention tool from unmaintainable CAD. If a part begins with a sketch unattached to a feature as its first component, the chances of absurdly used features, redundant features, and sketches without intent drops very low, very quickly. As such never, ever make a layout sketch. They are clearly just a waste of kilobytes of disk space, which is only serving to make load times for the assemblies larger.

## If you do lay things out...
Don't obey the layout sketch. It was a suggestion. Just a scratchpad to think about things. Now with that ideation out of the way you can get on with guessing at dimensions and making it all work out.

## Use more verbose dimensions, which can be used to define the location of things, and drive the position of entities
If you want five holes, equally spaced at a 1" interval, dimension one 1" from an edge, another 2" from the edge, the third 3", and so forth. Do NOT, under ANY circumstance, make construction geometry between the holes and specify them equally spaced. This would make changing the regular spacing too easy. Also, make sure each hole is independently dimensioned. You don't want one convenient place to change the size of hole needed.

## A few big things
Make your part in as few features as possible, with absolutely massive sketches as a result. If you need to make a 2D gearbox plate with pockets, make it all in one sketch - it's just a 2D part anyways! Do NOT break the pockets into their own extrude. Do NOT make bosses for the mount points their own feature. Do it in one shot.

## A ton of tiny things
Make your part in as many features as possible. If you need to make a stepped shaft, don't do it as one revolved feature, do it as a series of extrusions. Noting above, make sure each is named either defaultly, or arbitrarially.

# Housekeeping

## Always on, all the time
Make sure you always have every sketch, axis, plane, point, origin VISIBLE at all times. This way selecting something is quite simple and you do not need to move your cursor over to the Feature Tree to find things.
