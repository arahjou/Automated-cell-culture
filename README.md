Automated cell culture with raspberry pi. Code in python.

Cell culture media provides essential resources for cell survival and expansion. On the other hand, cells change the cell culture media properties and components. Carbon dioxide is one of this component which is produced  in the mitochondrial matrix during the TCA or Krebs cycle. Carbon dioxide dissolves into the media forming carbonic acid as it reacts with water and change the pH. Cells with a higher metabolism and  proliferation rate create a higher level of Co2 and probably each cell types has different  CO2 food print in the media which can be affected by stress, differentiation , cell death and etc. 

To measure the pH with a high accuracy (0.001 pH) and a high frequency (1/10 sec), I made a device base on "raspberry pi" and  "python". This device is able to measure pH constantly, creates a report and send it by email to the researcher. Furthermore, this device is programmed in the way that if pH reach to a predefined level ,  it takes sample and change the media and redo the experiment infinite times.

The idea is to use the recorded number and label them based on cell condition. The output will be used for supervised machine learning. In the way that just by measuring the change of pH in the course of time, we can predict the cell characteristic and condition. 
