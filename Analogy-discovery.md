Need to clearn this

TR1(x1,x2,x3)=e1,e2,e3. I am not sure if TR1 should look at all inputs of an example or one by one, although I think that it is better to look one by one. TR1(x4,x5,x6)=e4,e5,e6 for the other example. TR2(e1,...e6)=[c,p1,p2]. C is the common thing for both examples, while p1 is the particularity for example 1 and similar for p2. TR3(e1,e2,e3,c) = should output “yes”, c is a property of this example, same for example 2: TR3(e4,e5,e6,c) = yes.
TR3(e1,e2,e3,p1) = should output  “yes”, p1 is a property of this example, same for example 2, but using p2 instead of p1.
TR3(e1,e2,e3,p2) = should output “no”, p2 is NOT a  property of this example, same for example 2 but with p1 instead of p2.
TR3(e7,e8,e9, c or p1 or p2) = should output WTF/no since this comes from an unrelated example that most likely there is no analogy that corresponds to c,p1,p2. C is actually the analogy, the thing in common. Maybe I should use “no” instead of  WTF, and have just 2 possible outputs. 

Given an incomplete example, as the ones given to see how the network understands the analogy, we need to go from a set of incomplete embeddings, like [e7, e8] from this query example, to the image that will make that [e7,e8, e9_pred] results in TR2[e7,e8, e9_pred, e1, e2, e3 ] = c, p_new, p1 while c is the important thing. For this purpose I need the following TR4 and D network.

If I masked one embedding in [e1,e2,e3], for example masking out e2, if I give [c, p1] I should be able to recover e2. TR4(e1, m2, e3, c, p1) = e2. For what I want to do later, I prefer to avoid using p1:  TR4(e1, m2, e3, c) = e2, however, in that case I don’t know if it is possible to recover e2 exactly. If it is not possible I would rather have  TR4(e1, m2, e3, c) = e2_hat, so that TR2(e1, e2_hat, e3, e4, e5, e6) produces c.
I also want another network that creates a raw image based on an embedding. If possible I would rather avoid supervising using the actual image since TR1 is probably discarding some details of it. Therefore, something like D(ei) is such that TR1(D(ei)) = ei, cyclic in the embedding space, makes more sense.
Combining TR4 and D, for a pair of examples for which I obtained a c, I can obtain the remaining embedding of another example but incomplete that I want to have the same analogy c, and from that embedding, the desired final image.
