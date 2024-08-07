+++
title = "10. Joins 👩‍🎓👨‍🎓"
weight = 11
tags = ["sql"] 
+++

# Joining Bird Bands

When information could unintentionally be duplicated, data is often stored in separate tables with reference to an `id`. In the case of the dataset you will explore, most of the unique identifiers are labeled with the word `code`.

In this activity, you will be using joins to learn more about North American bird banding. The example contains data reduced from its original source, so if you would like to explore the data further, click the link in the Reference section.

## Instructions

* Create a new database named `bird_banding_DB`, and create eight new tables with pgAdmin named `bird_bands`, `age`, `band_type`, `bird_status`, `country_state`, `event_type`, `extra_info` and `sex`.

* Copy the code from `schema.sql` to create the tables, and then import the corresponding data from the CSV files with the same names. **Note:** Remember to refresh the database. Newly created tables will not immediately appear.

* Perform joins that will generate the following outputs:

  * Basic Information Table:


  | | band<br>character varying | event_date<br>character varying | species_name<br>character varying | age_description<br>character varying | sex_description<br>character varying |
  |----|----|----|----|----|----|
  | 1 | B06814289038 | 5/22/02 | Warbling Vireo | After Hatching Year | Unknown |
  | 2 | B06834226076 | 2/5/97 | White-eyed Vireo | After Hatching Year | Unknown |
  | 3 | B06834537033 | 9/28/01 | Red-eyed Vireo | After Hatching Year | Unknown |
  | 4 | B06834538078 | 9/6/01 | Red-eyed Vireo | Hatching Year | Unknown |
  | 5 | B06834760300 | 2/8/96 | La Sagra's Flycatcher | After Hatching Year | Unknown |
  | 6 | B06834762078 | 12/8/95 | La Sagra's Flycatcher | Unknown | Unknown |
  | 7 | B06834824074 | 2/9/96 | Yellow-bellied Flycatcher | After Hatching Year | Unknown |
  | 8 | B07033377537 | 2/26/19 | Yellow-bellied Flycatcher | Second Year | Unknown |
  | 9 | B07033378413 | 12/20/18 | Yellow-bellied Flycatcher | Hatching Year | Unknown |
  | 10 | B07033378577 | 12/5/18 | Yellow-bellied Flycatcher | Unknown | Unknown |

  * Extended Information where sex is not unknown:</br>


  | | band<br>character varying | event_date<br>character varying | species_name<br>character varying | band_type_description<br>character varying | bird_status_description<br>character varying | age_description<br>character varying | sex_description<br>character varying |
  |----|----|----|----|----|----|----|----|
  | 1 | B07324722072 | 6/22/15 | Bahama Swallow | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Hatching Year | Female |
  | 2 | B07383058128 | 7/15/13 | Black-capped Vireo | aluminum\butt-end (toll-free /web address) | Normal wild bird. | Hatching Year | Male |
  | 3 | B07383058283 | 7/12/13 | Black-capped Vireo | aluminum\butt-end (toll-free /web address) | Normal wild bird. | Hatching Year | Male |
  | 4 | B07404371540 | 3/18/14 | Black-whiskered Vireo | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Second Year | Female |
  | 5 | B07423509254 | 9/9/11 | Vermilion Flycatcher | aluminum\butt-end toll free | Normal wild bird. | After Hatching Year | Male |
  | 6 | B07463640300 | 4/3/11 | Northern Rough-winged Swallow | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Hatching Year | Female |
  | 7 | B07463640387 | 4/3/11 | Northern Rough-winged Swallow | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Hatching Year | Male |
  | 8 | B01924380221 | 2/13/06 | Tropical Kingbird | aluminum\butt end | Normal wild bird. | After Second Year | Male |
  | 9 | B01974875034 | 4/7/00 | Gray Kingbird | aluminum\butt end | Normal wild bird. | After Hatching Year | Female |
  | 10 | B07514549034 | 3/29/11 | Tropical Kingbird | aluminum\butt-end (toll-free /web address) | Normal wild bird. | After Second Year | Male |
  | 11 | B08623850540 | 1/11/75 | Yellow-bellied Flycatcher | aluminum\butt end | Normal wild bird. | Second Year | Male |
  | 12 | B08623850863 | 2/12/75 | Least Flycatcher | aluminum\butt end | Normal wild bird. | After Hatching Year | Female |

  * **Note:** You will need to include a `WHERE` clause on sex_description.

## Reference

Celis-Murillo, A., Malorodova, M., and Nakash, E., 2020, North American Bird Banding Program Dataset 1960-2020 retrieved 2020-06-26: U.S. Geological Survey data release, [https://doi.org/10.5066/P9R1L6Q7](https://doi.org/10.5066/P9R1L6Q7).
Specifically files NABBP_2020_grp_06.csv [reduced in pandas to locations outside of the US and Canada] and NABBP_Lookups_2020.zip

---



## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
-- Join bird_bands with age and sex
SELECT bird_bands.band, 
  bird_bands.event_date, 
  bird_bands.species_name, 
  age.age_description, 
  sex.sex_description
FROM bird_bands
INNER JOIN age ON
bird_bands.age_code = age.age_code
INNER JOIN sex ON
bird_bands.sex_code = sex.sex_code;

-- Join bird_bands with age and sex using aliases
SELECT b.band, 
  b.event_date, 
  b.species_name, 
  a.age_description, 
  s.sex_description
FROM bird_bands as b
INNER JOIN age as a ON
b.age_code = a.age_code
INNER JOIN sex as s ON
b.sex_code = s.sex_code;

-- Join bird_bands with band_type, bird_status, age, sex
-- where sex_description is not "Unknown"
SELECT bird_bands.band, 
	bird_bands.event_date, 
	bird_bands.species_name, 
	band_type.band_type_description, 
	bird_status.bird_status_description, 
	age.age_description, 
	sex.sex_description
FROM bird_bands
INNER JOIN band_type ON
bird_bands.band_type_code = band_type.band_type_code
INNER JOIN bird_status ON
bird_bands.bird_status = bird_status.bird_status
INNER JOIN age ON 
bird_bands.age_code = age.age_code
INNER JOIN sex ON
bird_bands.sex_code = sex.sex_code
WHERE sex_description != 'Unknown';

-- Join bird_bands with band_type, bird_status, age, sex using aliases
-- where sex_description is not "Unknown"
SELECT b.band, 
	b.event_date, 
	b.species_name, 
	bt.band_type_description, 
	bs.bird_status_description, 
	a.age_description, 
	s.sex_description
FROM bird_bands as b
INNER JOIN band_type as bt ON
b.band_type_code = bt.band_type_code
INNER JOIN bird_status as bs ON
b.bird_status = bs.bird_status
INNER JOIN age as a ON 
b.age_code = a.age_code
INNER JOIN sex as s ON 
b.sex_code = s.sex_code
WHERE sex_description != 'Unknown';
```
{{% /expand%}}