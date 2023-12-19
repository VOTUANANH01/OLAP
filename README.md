# OLAP

## Source folder:
[2020 Green Taxi link dataset](https://data.cityofnewyork.us/Transportation/2020-Green-Taxi-Trip-Data/pkmi-4kfn)

[taxi look up = location decode](https://s3.amazonaws.com/nyc-tlc/misc/taxi+_zone_lookup.csv)

[desc_csv = other catergorical column decode](https://www1.nyc.gov/assets/tlc/downloads/pdf/data_dictionary_trip_records_green.pdf)

## [diagram](https://app.diagrams.net/#G1R1o1Ah1DGpqyNO_dr-2v0Tc8gcPXZXVA):
![](https://github.com/VOTUANANH01/OLAP/blob/b710830b6fde5881a51224836c901682311bf9b1/picture/star_schema.png)

## SSIS:

### Preprocessing:
- Detect Null:  ISNULL(VendorID) || ISNULL(RatecodeID) || ISNULL(trip_type) || ISNULL(payment_type) || ISNULL(congestion_surcharge) || ISNULL(store_and_fwd_flag) || ISNULL(passenger_count)
- Detect outlier on mta_tax: mta_tax == 3.55
- detect outlier on passenger_count: passenger == 0
- detect outlier on RateCodeID: RateCodeID==99.0
- detect on Pickup_Dropoff_date: YEAR(lpep_pickup_datetime) > 2021 || YEAR(lpep_dropoff_datetime) > 2021
- detect negative values: : SIGN(trip_distance) == -1 || SIGN(fare_amount) == -1 || SIGN(extra) == -1 || SIGN(mta_tax) == -1 || SIGN(tip_amount) == -1 || SIGN(tolls_amount) == -1 || SIGN(improvement_surcharge) == -1 || SIGN(total_amount) == -1 || SIGN(congestion_surcharge) == -1
- create table: [RecordID]  int IDENTITY(1,1) not null primary key ....

  ![](https://github.com/VOTUANANH01/OLAP/blob/b710830b6fde5881a51224836c901682311bf9b1/picture/ssis_preprocessing.png)


### Dim PU/DOLocation:
![](https://github.com/VOTUANANH01/OLAP/blob/b710830b6fde5881a51224836c901682311bf9b1/picture/ssis_dim_DOLocation.png)
![](https://github.com/VOTUANANH01/OLAP/blob/b710830b6fde5881a51224836c901682311bf9b1/picture/ssis_dim_PULocation.png)

### Dim Pickup/Dropoff Date:
![]

