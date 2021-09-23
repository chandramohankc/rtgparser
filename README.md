
About:
========
This parser takes in a directory path and goes through all .txt files creates a JSON  (It does not go through sub directory 
need to work on that ) from RTG files, parses and stores data in mysql db. The RTG file format parsing logic is very
rigid it will only be able to parse RTG files with all valid data.


Steps to follow:
=================

1. Give input path in application.properies file input.path variable.
2. Place files in path and update mysql db config in application.properties if needed
3. Execute Spring boot application
4. Results will be stored in rtg table in mysql db.
5. In most cases RTG table will be automatically created when application starts up.

DB Table Script:
===================
SELECT * FROM sampleDb.rtg;

Select COUNT(*) FROM sampleDb.rtg;

CREATE TABLE `rtg` (
`id` bigint NOT NULL,
`longitude` varchar(255) DEFAULT NULL,
`event_timestamp_vehicle` varchar(255) DEFAULT NULL,
`heading` varchar(255) DEFAULT NULL,
`ignition_status` varchar(255) DEFAULT NULL,
`instrument_cluster_speed` varchar(255) DEFAULT NULL,
`lateral_acceleration` varchar(255) DEFAULT NULL,
`latitude` varchar(255) DEFAULT NULL,
`longitudinal_acceleration` varchar(255) DEFAULT NULL,
`odometer` varchar(255) DEFAULT NULL,
`seat_belt_state0` varchar(255) DEFAULT NULL,
`seat_belt_state1` varchar(255) DEFAULT NULL,
`seat_belt_state2` varchar(255) DEFAULT NULL,
`seat_belt_state3` varchar(255) DEFAULT NULL,
`seat_belt_state4` varchar(255) DEFAULT NULL,
`seat_belt_state5` varchar(255) DEFAULT NULL,
`seat_belt_state6` varchar(255) DEFAULT NULL,
`seat_belt_state7` varchar(255) DEFAULT NULL,
`vehicle_id` varchar(255) DEFAULT NULL,
PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;


Additional Notes:
===================

Sample Input used for parsing is stored in sampleRTG.txt under root path. The parser looks for
"messageCounter" : 1 pattern to decide start and end of JSON. If this is interchanged the parser will not work.

This parser is created under assumption that all files which will be supplied as input will be of format of sample
RTG file

Sample Model:
===============
{
     "RTG": [
     {

     "VehichleId" : "123-123-13312",

        "eventTimestampVehicle" : "16201200120",

        "ignitionStatus": "ON",

        "odometer"  : "200303",

        "heading" : "2476",

        "latitude" : "37384585", 

        "longitude": "-121831374",	

        "lateralAcceleration" : "-0.01",

        "longitudinalAcceleration" : "-0.01",

        "instrumentClusterSpeed" : "-0.01",

        "seatBeltState0" : "true",

        "seatBeltState1" : "true",

        "seatBeltState2" : "false",

        "seatBeltState3" : "true",

        "seatBeltState4" : "3",

        "seatBeltState5" : "true",

        "seatBeltState6" : "true",

        "seatBeltState7" : "true"
     }, 

     {
        "eventTimestampVehicle" : "312001233",

        "ignitionStatus": "ON",

        "odometer"  : "200303",

        "heading" : "2476",

        "latitude" : "127747212", 

        "longitude": "-121831374",	

        "lateralAcceleration" : "-0.01",

        "longitudinalAcceleration" : "-0.01",

        "instrumentClusterSpeed" : "-0.01",

        "seatBeltState0" : "true",

        "seatBeltState1" : "true",

        "seatBeltState2" : "false",

        "seatBeltState3" : "true",

        "seatBeltState4" : "3",

        "seatBeltState5" : "true",

        "seatBeltState6" : "true",

        "seatBeltState7" : "true"
     }



]

}
