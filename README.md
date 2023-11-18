what's the point of a hyper-dimensional string (phext)?

you first have to experience phext for yourself. let's say that you have a list of numbers, like below.

3, 10, 17, 8, 9, 4, 11, 6

you want to compute some things about those numbers, so you stash a table

sum: 68
size: 8
average: 8.5
min: 3
max: 17

you can now audit those results easily - because the source data and the results always go together.

you can add a cryptographic signature block, to show that you ran those numbers - anyone can independently verify them (and your work).

5306bf323d3d539d4e8dee134ac310024254ab31699eec91652791a818d07732

so what do we have now? reproducible science!

data1.phext
-----------
3, 10, 17, 8, 9, 4, 11, 6
sum: 68
size: 8
average: 8.5
min: 3
max: 17
hash: 5306bf323d3d539d4e8dee134ac310024254ab31699eec91652791a818d07732

OK, but what happens when someone changes the list? that's fine, but your prior signature is now invalid.

data2.phext
-----------
3, 10, 17, 11, 8, 9, 4, 11, 6
sum: 79
size: 9
average: 8.8
min: 3
max: 17
hash: d9267f4eaaa0b47464d8ff8e3e41f69eeb0745fb8455ee9a5a5b62e92990e39c

anyone looking at just the first and last numbers, or the min and max, won't detect your change.
but anyone looking at the details, will!

here's where phext really comes into play - we can now bundle those two results into a new table.

data3.phext
-----------
[data1.phext]
[data2.phext]
[reviewer comments]

this third file contains all of the detail of the first two, along with annotated notes about the results.

data1.phext is the original test data.
it included 8 elements, with an average of 8.5, and a hash of 5306bf.

data2.phext is the corrupted data.
it includes 9 elements, with an average of 8.8, and a hash of d9267f.

in my expert opinion, we should leverage data1.phext
hash: 0f51bdd705071f7973cfccb1ca05df30cb093a22987df185f7f746884d336c35

we can now audit all of those results and make adjustments as needed.