###############################################################################
#   Datasets and source codes for HotMobile'24 (Demystifying Secondary Radio Access Failures in 5G)
#
###############################################################################

This README is used to introduce our datasets and source codes used by our HotMobile'24 work: 
“Demystifying Secondary Radio Access Failures in 5G”.

If you use our datasets and/or codes in your publication, please cite our HotMobile'24 paper, 
@inproceedings{liu2024demystifying,
  title={Demystifying Secondary Radio Access Failures in 5G},
  author={Liu, Yanbing and Guo, Junpeng, and Peng, Chunyi},
  booktitle={HotMobile'24},
  year={2024}
}


1) Dataset overview 

We have conducted this study of secondary radio access failures on two datasets D1 and D2: 
 
(D1) is a public dataset from our prior 5G measurement work in INFOCOM'23 (A Close Look at 5G in the Wild: Unrealized Potentials and Implications). It was collected from April 2021 to January 2022 with 13 regions R1-R13 in two cities, Indianapolis and Chicago with three top-tier US carriers: AT&T, Verizon and T-Mobile. 

(D2) is a recently collected dataset from September 2023 to October 2023, focusing on problematic failure handling. 

In D1 and D2, we mainly run two types of experiments: (1) Heavy traffic: Repeatedly download bulky files (500MB each) from Google Cloud to measure downlink data speed. (2) Light traffic: Ping Google every second to make radio connection active throughout the experiment. Both heavy and light traffic experiments are performed via MI-LAB testbed (http://milab.cs.purdue.edu/). We conducted both heavy traffic and light traffic experiments in D1 while focusing on heavy traffic experiments in D2. 



2) Structure of files

├── dataset
│   ├── raw
│   │   ├── cellset_thput
│   │   │   ├── D1
│   │   │   │   └── {region}_gps_cellset_thput_0.1_taskround_list_{mccmcn}_{phone model}_{date range}.csv.csv
│   │   │   └── D2
│   │   │       └── gps_cellset_thput_0.1_{date range}_taskround_list_{mccmcn}_{phone model}.csv.csv
│   │   ├── rss
│   │   │   ├── D1
│   │   │   │   └── {region}_raw_rss_taskround_list_{mccmcn}_{phone model}_{date range}.csv.csv
│   │   │   └── D2
│   │   │       └── raw_rss_{date range}_taskround_list_{mccmcn}_{phone model}.csv.csv
│   │   └── scgfailure_instance
│   │       ├── D1
│   │       │   └── failure_fd_sample_{operator}_type_indy_1008.csv
│   │       └── D2
│   │           └── failure_fd_sample_{operator}_type_wl_1008.csv
│   ├── grid
│   │   ├── D1
│   │   │   ├── {region}_grid_cell_set_{phone model}_{date range}_{mccmcn}_{grid size}_0_0.csv
│   │   │   ├── {region}_rss_cell_{date range}_{mccmcn}_{grid size}_0_0.csv
│   │   │   └── {region}_thput_grid_{date range}_{mccmcn}_{grid size}_0_0_{phone model}.csv
│   │   └── D2
│   │   │   ├── cellset_thput_grid_{operator}_wl_{grid size}.csv
│   │   │   ├── cell_rss_grid_{operator}_wl_{grid size}.csv
│   │   │   └── thput_grid_{operator}_wl_{grid size}.csv
│   └── dataset_stat
│       └── dataset-stats.csv
│
└── figure
    └── ...

Due to the space limit by Github, we compress and move dataset/raw folder to 
https://mssn3.cs.purdue.edu/owncloud/index.php/s/zIJ3MA5YQTj0qUE


3) Dataset release and its description

-------------------------------------------------------------------------------
dataset/raw/cellset_thput: 
Records the serving cellset, GPS, instant downlink throughput per 0.1 second.
-------------------------------------------------------------------------------
dataset/raw/rss:
Records RSRP/RSRQ measurement samples of serving cells or neighboring cells.
-------------------------------------------------------------------------------
dataset/raw/scgfailure_instance:
Records SCGFailure instances and their information including timestamp, location, operator, type, failure cause, source/destination cellset, recovery result and throughput before and after SCGFailure.
-------------------------------------------------------------------------------
dataset/grid:
Records coverage, cellset, and performance per grid. The size of each grid is 0.0005 × 0.0005 in latitude and longitude, approximately, 55m × 45m.
-------------------------------------------------------------------------------
dataset/dataset_stat:
Records dataset stats (duration, distance, channel/cell/cellset number, etc.) in each region.
-------------------------------------------------------------------------------
figure:
Includes plotting scripts (Pgfplots) and used input data of each figure in the paper.
-------------------------------------------------------------------------------
