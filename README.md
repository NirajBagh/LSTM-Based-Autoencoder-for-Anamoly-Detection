# LSTM-Based-Autoencoder-for-Anamoly-Detection
This notebook is intended to illustrate conditioning monitoring of industrial machinery by walking through a real life dataset of bearing vibration data.Generally, conditioning monitoring of a machine is done by looking at a sensor mesurement (Eg. Temperature, Vibration ) and imposing bounds to it, i.e. under normal operating conditions, the measurement values are bounded by a maximum and minimum value (similar to control charts). Any deviation is the defined bounds sends an alarm. This is often generally defined as anamoly detection. However, this method often sends false alarms (false positives) or misses an alarm (false negative). Furthermore, a single signal is observed/analysed in isolation. For example, an alarm may sound if the temperature exceeeds a certain level. A system defined above often cannot look at mutiple parameters and come to a conclusion about the state of a machine. Or technical parlance, one cannot take advantage of the multi-dimensionality of the data.
This is where machine learning and other AI based techniques step in.
This notes walks one through anamoly detection of a single dimension data (vibration). This is easier to visualise. The same principles hold true for mutildimensional data as well.
# NASA Bearing Dataset
# 1. Dataset Description
The dataset is sourced from the NASA repo https://ti.arc.nasa.gov/tech/dash/groups/pcoe/prognostic-data-repository/.
Four bearings were installed on a shaft. The rotation speed was kept constant at 2000 RPM by an AC motor coupled to the shaft via rub belts. A radial load of 6000 lbs is applied onto the shaft and bearing by a spring mechanism. All bearings are force lubricated.
Rexnord ZA-2115 double row bearings were installed on the shaft as shown in Figure 1. PCB 353B33 High Sensitivity Quartz ICP accelerometers were installed on the bearing housing (two accelerometers for each bearing [x- and y-axes] for data set 1, one accelerometer for each bearing for data sets 2 and 3). Sensor placement is also shown in Figure 1. All failures occurred after exceeding designed life time of the bearing which is more than 100 million revolutions.
3 2. Dataset Structure
Three (3) data sets are included in the data packet (IMS-Rexnord Bearing Data.zip). Each data set describes a test-to-failure experiment. Each data set consists of individual files that are 1-second vibration signal snapshots recorded at specific intervals. Each file consists of 20,480 points with the sampling rate set at 20 kHz. The file name indicates when the data was collected. Each record (row) in the data file is a data point. Data collection was facilitated by NI DAQ Card 6062E. Larger intervals of time stamps (showed in file names) indicate resumption of the experiment in the next working day.

Set No. 1:
Recording Duration: October 22, 2003 12:06:24 to November 25, 2003 23:39:56
No. of Files: 2,156
No. of Channels: 8
Channel Arrangement: Bearing 1 – Ch 1&2; Bearing 2 – Ch 3&4; Bearing 3 – Ch 5&6; Bearing 4 – Ch 7&8.
File Recording Interval: Every 10 minutes (except the first 43 files were taken every 5 minutes)
File Format: ASCII
Description: At the end of the test-to-failure experiment, inner race defect occurred in bearing 3 and roller element defect in bearing 4.

Set No. 2:
Recording Duration: February 12, 2004 10:32:39 to February 19, 2004 06:22:39
No. of Files: 984
No. of Channels: 4
Channel Arrangement: Bearing 1 – Ch 1; Bearing2 – Ch 2; Bearing3 – Ch3; Bearing 4 – Ch 4.
File Recording Interval: Every 10 minutes
File Format: ASCII
Description: At the end of the test-to-failure experiment, outer race failure occurred in bearing 1.

Set No. 3
Recording Duration: March 4, 2004 09:27:46 to April 4, 2004 19:01:57
No. of Files: 4,448
No. of Channels: 4
Channel Arrangement: Bearing1 – Ch 1; Bearing2 – Ch 2; Bearing3 – Ch3; Bearing4 – Ch4;
File Recording Interval: Every 10 minutes
File Format: ASCII
Description: At the end of the test-to-failure experiment, outer race failure occurred in bearing 3.


