# Misc (Level 1): Leaf of the Forest
## Description: 
>We found an even bigger directory tree hiding a flag starting at /problems/ba3662836dafb25fdcb412b505b7b677. It would be impossible to find the file named flag manually...
## Solution:
This one is actually pretty simple thanks to the Linux 'find' command.
***
    $ find . | grep flag
    ./forest/tree2763a4/trunk764d/trunke6d5/trunk7905/trunk0008/
trunk95d7/trunkcbe5/trunk2319/branchc790/flag
    $ cd forest/tree2763a4/trunk764d/trunke6d5/trunk7905/trunk0008/
trunk95d7/trunkcbe5/trunk2319/branchc790/flag
    $ cat flag
    395ba83a5a494eb04f43e15020577a75
***
Therefore, flag is: 395ba83a5a494eb04f43e15020577a75
