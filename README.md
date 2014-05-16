# Phenotypic Data Collection API

## Overview

This document outlines the use cases and possible API to support the manual collection of phenotypic data on a portable device.

## User Stories

### Assumptions

- Data will be entered on some kind of portable, hand-held device
- An internet connection will be available for initial device setup (if necessary)
- An internet connection may not be available when entering data

### Users

The intended users of this application are plant breeders, data collectors or outsourced staff who have been charged with manually measuring and recording traits of a set of plants.

### Collection Preparation

1. As a data collector, I want to be able to select the trial for which I will be measuring plants today, so I can retrieve information about the trial that may be relevant to my collection, such as plot layout, traits intended to be measured, previously recorded data

2. As a data collector, I want to be able to specify one or more traits to be prompted for measurement at each plant, so that I don't have to manually specify which traits I am recording data for each time I enter data

#### Notes

This will likely involve:

* Retrieving a list of trials, scoped sensibly. This could be done by:
** Providing trial search functionality
** Providing a list of ways we can scope trials to the user to select from before retrieving appropriate trials (e.g. programs, location, season)
** Providing a list of trials potentially relevant to the user (as determined by previous interaction with that trial) - this is very system dependant
* There may be other data relevant to the trial that would be useful to pull down - the above is not an exhaustive list

### Data Collection

1. As a data collector, I want to be able to specify how I want to walk the plots, so that I am prompted for measurement entry in the order I visit plants

2. As a data collector, I want to have access to data that has already been recorded for the plant I am measuring at the time I am measuring a trait, so that I am aware of any potentially relevant information

4. As a data collector, I want to be able to record any number of traits at once, so I can be efficient in my data collection

5. As a data collector, I want to be able to easily see what plot I am expecting to record data for at any point in time, in case I get interrupted and have to resume later

6. As a data collector, I want my trait information to be validated as I enter it, so that I can be made aware of any mistakes I have made and correct them quickly

7. As a data collector, I want to be able to record any arbitrary trait at the point of measurement, so that I can record any unexpected information I deem relevant

8. As a plant breeder, I want as much information about the collection of phenotypic data as possible, so that (...?)

#### Notes

* May we want the concept of 'pausing' collection?
* What about "notes" on the collection as a whole? Is that something that's needed?
* Metadata collected about the collection itself may include location data, who did the collection, information about the device data was entered on, time and date etc - basically as much as possible

### Data Curation and Publishing

As a plant breeder, I want access to collected data as soon as possible so that I can curate and analyse it.

## API Calls

See the documentation on [Apiary](http://docs.fieldbook.apiary.io/).

### Get Data Sets /fieldbook/getDataSets

Get a list of data sets to choose from.

### Get Data Set Information /fieldbook/{dataSetId}

Returns all information we need about a trial to initiate the collection device and allow the user to specify what they want to measure. May need a separate call to get previously measured data..?

### Get Traits /fieldbook/{dataSetId}/traits

Get a list of traits to be measured for that data set.

### Upload Data /fieldbook{dataSetId} (POST - for example)

Feed data back to a central agent for curation / analysing / publication. What happens to the data beyond the point of "upload" is out of the scope of this API.

## Miscellaneous Notes

- There is a relatively small known set of ways you would traverse plots - these can be hard coded in the app.
- Nice to haves: photos of plants, barcode scanning
- An alternative workflow could involve starting from a grid of plots, not a trail

