# Reads mapping consideration
In the context of Hi-C methods which are not based on restriction enzyme digestion, no filtering of restriction fragments is applied. The uniquely mapped read pairs are directly used to build the contact maps. However, during the process of ligation (with blunt ends) and sonication one may get many kinds of artifacts are can be uniquely mapped to the genome, but doesn't make any sense. So we would like to dive deep about how these unwantted fragments come from. <br>
![](/assets/Overall.jpg)
Figure: Summary of hic reads mapping scheme.


We also made a video for this part:(which haven't been able to show on gutbook)
https://drive.google.com/file/d/1w6BVy5KlK9aCv9AoekpsljM7ADqNg041/view?usp=sharing 