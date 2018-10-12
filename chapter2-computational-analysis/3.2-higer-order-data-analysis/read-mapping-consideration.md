# 3.2.1 Read mapping consideration

## Reads mapping consideration

In the context of Hi-C methods which are not based on restriction enzyme digestion, no filtering of restriction fragments is applied. The uniquely mapped read pairs are directly used to build the contact maps. However, during the process of ligation \(with blunt ends\) and sonication one may get many kinds of artifacts are can be uniquely mapped to the genome, but doesn't make any sense. So we would like to dive deep into how these unwanted fragments come from. 

![ Figure1: Summary of hic reads mapping scheme.](../../.gitbook/assets/overall.png)

{% embed url="https://www.youtube.com/embed/6XNdbuALqOs" %}

