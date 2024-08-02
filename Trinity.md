# TRINITY: A Fast Compressed Multi-attribute Data Store

## Paper

TRINITY: A Fast Compressed Multi-attribute Data Store \
Ziming Mao, Kiran Srinivasan, Anurag Khandelwal \
2024 \ 
https://www.anuragkhandelwal.com/papers/trinity.pdf

## Abstract
*With the proliferation of attribute-rich machine-generated data, emerging real-time monitoring, diagnosis, and visual- ization tools ingest and analyze such data across multiple attributes simultaneously. Due to the sheer volume of the data, applications need storage-efficient and performant data representations to analyze them efficiently.*
*We present TRINITY, a system that simultaneously facil- itates query and storage efficiency across large volumes of multi-attribute records. TRINITY accomplishes this through a new dynamic, succinct, multi-dimensional data structure, MDTRIE. MDTRIE employs a combination of novel Mor- ton code generalization, a multi-attribute query algorithm, and a self-indexed trie structure to achieve the above goals. Our evaluation of TRINITY for real-world use-cases shows that compared to state-of-the-art systems, it supports (1) 7.2–59.6× faster multi-attribute searches, (2) storage foot- print comparable to OLAP columnar stores and 4.8–15.1× lower than NoSQL stores and OLTP databases, and (3) point query throughput comparable to NoSQL stores and 1.7–52.5× higher than OLTP databases and OLAP columnar stores.*

## Results

We evaluate TRINITY for three real- world use-cases; compared to state-of-the-art systems, TRIN- ITY supports \
(1) 7.2–59.6× faster multi-attribute searches, \
(2) storage footprint comparable to columnar stores, and 4.8– 15.1× lower than NoSQL and OLTP databases, and \
(3) point query throughput comparable to NoSQL stores and 1.7–52.5× higher than OLTP databases and columnar stores. \

## Notes

Large scale data generation, quick storage, quick querying and analysis. Ie imagine uber ride data gen and rapid analysis.
