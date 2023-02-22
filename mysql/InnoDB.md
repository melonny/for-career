### Intro

```InnoDB is a storage engine that stores table data on disk, so even after a shutdown, our data still exists. The actual data processing process occurs in memory, so it is necessary to load the data from the disk into memory. If it is a write or modification request, the contents in memory also need to be flushed back to disk. However, as we know, the speed of reading and writing to disk is very slow, and it is several orders of magnitude slower than reading and writing to memory. So, if we want to retrieve certain records from a table, does the InnoDB storage engine need to read each record from the disk one by one? No, that would be too slow. The approach that InnoDB takes is to divide the data into several pages, with pages as the basic unit for data exchange between disk and memory.```

### Row Format
#### COMPACT
