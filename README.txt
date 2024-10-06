###############################################################################
#   Datasets and source codes for TMC (Handling Failures in Secondary Radio Access Failure Handling in Operational 5G Networks)
#
###############################################################################

This README is used to introduce our datasets and source codes used by our TMC (IEEE Transactions on Mobile Computing) work: “Handling Failures in Secondary Radio Access Failure Handling in Operational 5G Networks”.

If you use our datasets and/or codes in your publication, please cite our TMC paper, 
@inproceedings{liu2025handling,
  title={Handling Failures in Secondary Radio Access Failure Handling in Operational 5G Networks},
  author={Liu, Yanbing, and Peng, Chunyi},
  booktitle={IEEE Transactions on Mobile Computing},
  year={2025}
}


1) Dataset overview 

We have conducted this study of secondary radio access failures on three datasets D1, D2 and D3: 
 
(D1) is a public dataset from our prior 5G measurement work in INFOCOM'23 (A Close Look at 5G in the Wild: Unrealized Potentials and Implications). It was collected from April 2021 to January 2022 with 13 regions R1-R13 in two cities, Indianapolis and Chicago with three top-tier US carriers: AT&T, Verizon and T-Mobile. In D1, we run two types of experiments: (1) Heavy traffic: Repeatedly download bulky files (500MB each) from Google Cloud to measure downlink data speed. (2) Light traffic: Ping Google every second to make radio connection active throughout the experiment. 

In D1, we run bulky file downloading, which repeatedly download bulky files (500MB each) from Google Cloud, to measure downlink data speed.

(D2) is collected from September 2023 to October 2023 in West Lafayette, focusing on problematic failure handling. It also covers three top-tier US carriers: AT&T, Verizon and T-Mobile. In D2, we focus on heavy traffic experiment with repeated bulky file downloading.

(D3) is collected from December 2023 to June 2024 on T-Mobile's 5G network in West Lafayette, which also focuses on problematic failure handling. In D3, we run two types of applications, file downloading and file uploading.

All experiments in D1, D2 and D3 are performed via MI-LAB testbed (http://milab.cs.purdue.edu/). 


2) Structure of files

├── dataset
│   ├── raw
│   │   ├── cellset_thput
│   │   │   ├── D1
│   │   │   │   └── {region}_gps_cellset_thput_0.1_taskround_list_{mccmcn}_{phone model}_{date range}.csv.csv
│   │   │   ├── D2
│   │   │   │   └── gps_cellset_thput_0.1_{date range}_taskround_list_{mccmcn}_{phone model}.csv.csv
│   │   │   └── D3
│   │   │       └── gps_cellset_thput_rss_snr_rb_1_{date range}_all_all_taskround_list_{mccmcn}_{phone model}_new.csv.csv
│   │   ├── rss
│   │   │   ├── D1
│   │   │   │   └── {region}_raw_rss_taskround_list_{mccmcn}_{phone model}_{date range}.csv.csv
│   │   │   ├── D2
│   │   │   │   └── raw_rss_{date range}_taskround_list_{mccmcn}_{phone model}.csv.csv
│   │   │   └── D3
│   │   │       └── raw_rss_{date range}_all_all_taskround_list_{mccmcn}_{phone model}_new.csv.csv
│   │   └── scgfailure_instance
│   │       ├── D1
│   │       │   └── failure_fd_sample_{operator}_type_indy_1008.csv
│   │       ├── D2
│   │       │   └── failure_fd_sample_{operator}_type_wl_1008.csv
│   │       └── D3
│   │           └── failure_fd_sample_{operator}_type_dronemeas.csv
│   └── grid
│       ├── D1
│       │   ├── {region}_grid_cell_set_{phone model}_{date range}_{mccmcn}_{grid size}_0_0.csv
│       │   ├── {region}_rss_cell_{date range}_{mccmcn}_{grid size}_0_0.csv
│       │   └── {region}_thput_grid_{date range}_{mccmcn}_{grid size}_0_0_{phone model}.csv
│       ├── D2
│       │   ├── cellset_thput_grid_{operator}_wl_{grid size}.csv
│       │   ├── cell_rss_grid_{operator}_wl_{grid size}.csv
│       │   └── thput_grid_{operator}_wl_{grid size}.csv
│       └── D3
│           ├── all_grid_cellset_thput_{date range}_{grid size}_{mccmcn}_fd.csv
│           ├── all_grid_cell_rss_{date range}_{grid size}_{mccmcn}_fd.csv
│           └── all_grid_thput_{date range}_{grid size}_{mccmcn}_fd.csv
│
└── figure
    └── ...

Due to the space limit by Github, we compress and move dataset/raw folder to 
https://mssn3.cs.purdue.edu/owncloud/index.php/s/sT5j3PD2u8opilM


2) Dataset release and its description

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
figure:
Includes plotting scripts (Pgfplots) and used input data of each figure in the paper.
-------------------------------------------------------------------------------
