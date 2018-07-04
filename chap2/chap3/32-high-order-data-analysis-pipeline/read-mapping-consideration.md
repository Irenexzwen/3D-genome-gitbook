# Reads mapping consideration
In the context of Hi-C methods which are not based on restriction enzyme digestion, no filtering of restriction fragments is applied. The uniquely mapped read pairs are directly used to build the contact maps. However, one way to filter out artifacts such as self-ligation is to discard intra-chromosomal pairs below a given distance threshold [4]. HiC-Pro therefore allows these short range contacts to be filtered out.

![](/assets/Overall.jpg)



{% gdrive %} https://drive.google.com/file/d/1w6BVy5KlK9aCv9AoekpsljM7ADqNg041/view?usp=sharing {% gdrive %}