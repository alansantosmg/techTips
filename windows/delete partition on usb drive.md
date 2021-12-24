# Delete partition on USB drive using Diskpart

1. Open command prompt then type:

```cmd
diskpart

list disk
select disk  <disknumber>

list partition
select partition <partitionNumber>

delete partition

```