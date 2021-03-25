Exploring Typologies of Employment Subcentres in London, England
================
Jacob L. Macdonald, University of Liverpool; <Jacob.Macdonald@liverpool.ac.uk> & Pranjal Dave

1. Introduction
---------------

This *.Rmd* document explores an industry-based breakdown of business and employment densities within London's urban employment subcentres. A monocentric urban detection algorithm is first applied to identify the spatial extent of dense employment hot-spots in the peripheral areas surrounding the primary central business district (CBD) (available through x\_\_\_x). The sectoral composition of different employment subcentres in the city are tracked using spatially granular employment and business registry details according to broad industry typologies. We make a particular distinction between those subcentres and employment cores making up London's well defined Central Activity Zone (CAZ) - a central employment region itself on an international scale, orders of magnitude above other employment centres and subcentres across the country.

Employment subcentres are characterized by the spatial clustering of areas outside the traditional CBD with locally higher employment densities. The location of these employment hotspots within an urban area, and their broader use, typology and function, are important to consider in municipal planning as these zones oftentimes dualy serve as inter-city hubs for transportation, commercial or business networks and can have wide spill over influences to other urban markets such as residential or commercial real estate.

We identify employment subcentres in London as local clusters of census tracts deviating from the monocentric city model of centralized employment density. Employment and business density in London gravitate towards its geographic and historic centre, and employment subcentres are delineated here via a threshold cutoff model based on exponential density decay. This algorithmic application of the *Method of Exponentially Decaying Cutoffs* stems from Ban et al. (2017) and Macdonald (forthcoming x\_\_\_x), updating the flexibility of functional form decay and tailoring towards the London context.

After delineating the location of these employment hotspots within the urban area, this work explores the typological breakdown of different industry measures within these geographic employment subcentre zones. The identification of employment zones across an urban area are often conditional on total employment density. It is thus also important to consider how different employment subcentres may vary in terms of their broad function and relationship to the local environment, since different centres and hubs within a municipality may serve very different purposes depending on which industries are most prominent. This is particularly the case in London where employment and industry sectors are known to be heavily tied to geography.

Using spatially granular employment and business statistics at the (SIC 2007) industry level helps to bridge the gap in detailing the heterogeneity of different types of workzone hubs. One of the major caveats, however, is the temporal limitation which often comes at the expense and in tradeoff to spatial and geographic detail. In the case of small-area employment statistics, which are a fundamental parameter of many theoretical urban models, spatially detailed and comparable employment levels are often only available with every census release. We use the most recent, open and comprehensive granular small area employment levels at the Workplace Zone (WZ) geographic scale from the 2011 Census. Given the particular emphasis on delineating spatial extents in high density employment zones, WZ boundaries are more appropriate than traditional LSOA levels.

While employment density statistics may be limited in temporal scope, other datasets like business registries, for example, may be able to supplement and serve as a proxy to identify patterns of economic density and spatial clustering. The [CDRC Business Census](https://data.cdrc.ac.uk/dataset/business-census) datasets provide yearly snapshots of registered businesses and industry typologies across England with granular location information. This allows us to extend beyond the limitations of only having detailed (openly accessible) employment detail at small area scales available from 2011 by comparing the granular spatial patterns of employment and business density and tracking the subsequent evolution of business and sector dynamics.

Employment subcentres, and their location, are inherently complex and linked to any number of urban dynamics from population densities, transportation links, urban or natural amenities. Using the distribution of registered businesses by industry sector located within subcentres can identify commonalities and differences between these key urban locations. The spatial distribution of a city's workforce can have important implications on any number of urban policies. Even more, as different sectors and industries of the economy can have varying workforces and geographic patterns, open source spatial and granular tools and data to explore these dynamics can be just one way to explore and highlight these dynamics for informed research-based decision making.

2. Data and Study Region
------------------------

### 2.1. Granular Employment and Business Data

This work is conducted using entirely open and accessible data and tools. The most recent geographically granular available data on employment levels is from the UK Census 2011, obtained online through the [Nomis](https://www.nomisweb.co.uk/ "ONS Nomis Labour Market Statistics") platform. Detailed working day population statistics are available for small area Workplace Zone (WZ) tract boundaries allowing spatial measures of employment density to be constructed. We are specifically interested in the employment levels (Table WP102EW), along with corresponding industry sector breakdown, as they are distributed across space.

While no choice of spatial unit to use for research and statistical purposes can be uniquely accurate, WZ boundaries provide the most granular detail in key employment zones such as the main CBD of London. The WZ boundaries are geographically delineated to align better with patterns of the employed workday population as opposed to the resident population. While other census geographic areas, such as Output Areas, are constructed around consistent populations within each spatial unit, WZ boundaries are constructed around consistent workers in each unit (ONS 2014). With this in mind, the WZ areas are significantly more detailed in city centre areas where employment levels and densities are largest.

Employment subcentres in a given region are delineated based only on total employment, local densities, and distances to some central, densest, location. Clusters of high density total employment areas are organized into contiguous tracts representing geographic workplace hubs across the city. This total employment distribution however can mask significant heterogeneity in the types and functions of different workforces and geographic locations. While an employment subcentre more tailored to financial services workforces may attract only the local working population, retail or service based subcentres may draw in residents and people from the urban peripherals.

Additional data at the WZ level are further included to help characterize the different typologies and varying characteristics of these different areas. Employment data for each industry grouping is obtained from Census Table WP605EW coded according to the [UK Standard Industrial Classification (SIC) Hierarchy](https://onsdigital.github.io/dp-classification-tools/standard-industrial-classification/ONS_SIC_hierarchy_view.html). Broad Industry Groups (BIG) of SIC codes are used to define the highest level of sector aggregation. We also make use of the two-digit SIC Division for more detailed tracking of the specific industry sectors which are associated to London as a whole and namely to the CBD and subcentre areas of the city towards where employment gravitates.

To complement employment levels, and better understand the built and physical surroundings of these employment areas, we merge in data on registered businesses from the [Consumer Data Research Centre (CDRC) Business Census](https://data.cdrc.ac.uk/dataset/business-census) data from Companies House. While granular employment data is limited in terms of temporal frequency, more detailed and up to date open data is available for business registries. Understanding the link between employment subcentres and the types of businesses making them up can thus be used to explore higher frequency changes to these areas than what traditionally limited employment data can provide.

Registered businesses for London are provided along with SIC industry classification code and post code location identifier. A series of cleaning is done to the data to retain only active (and non-dormant) companies with a valid post code and SIC classification. Complete data is available in yearly snapshots from 2013 to 2019. Using the National Statistics Postal Lookup 2020 we obtain a proxy latitude and longitude from the postcode and run a spatial join to get a count of businesses of different industries for each WZ location. We use the first two-digits of the SIC code representing industry Divisions in the hierarchical scheme (nested within Sections and BIG groupings) allowing us to get a distribution of counts for different types of businesses in each area.

Granular business data is more easily available consistently over space and time compared to spatially detailed employment data. Other sources of workday employment levels may be available at more frequent temporal updates including, for example, small area estimates from the [Business Registry and Employment Survey](https://www.ons.gov.uk/surveys/informationforbusinesses/businesssurveys/businessregisterandemploymentsurvey). These estimates however are only openly available at the Lower Super Output Area (LSOA) level which have relatively large units in areas where employment density is highest - by design. As LSOA boundaries are delineated with the idea of consistent populations, high density employment areas will necessarily have less refined spatial units to match benchmark resident population.

Finally, the CDRC [London Workplace Zone Classification (LWZC)](https://data.cdrc.ac.uk/dataset/london-workplace-zone-classification) is a geogdemographic at the WZ level providing a clustering classification for each geography based on a series of input data, and tailored to London specific. This classification identifies different types of WZ compositions across six domains including the areas employment structure, dynamism, employee characteristics, job characteristics, commuting, and residential context. Each WZ is assigned to one of six supergroups classifying areas into residential, city focus, or metropolitan among other finer disaggregations. All together, this gives us a view of each individual WZ tract in terms of its sector-based employment, density, and characteristics of the local demographics. As WZ are self-organized into employment subcentre clusters, we will be able to compare the composition and evolution of these geographic areas relative to the remainder of the city.

### 2.2. Study Region: London, England

The focus of this work is London, England. As capital and international city, London attracts a sizeable workforce and population with around 6 million jobs in 2019 and steadily increasing over the long run (ONS 2020). Much of this workforce come from outside of the UK either from the EU or elsewhere in the world (PwC 2017) attracted by jobs in professional services, scientific and technical industries, finance and insurance, information and communication, and business administration and support services.

London has a total of 8,154 WZ tracts spread over a total area of 157,353 hectares (1,573.5 km**<sup>2</sup>). The map of WZ employment density deciles reveal a clear central clustering pattern, however several periphiral employment hotspots are visible as well. From an aerial perspective, London follows clear patterns of monocentricity centered around the city's geographic and historic centre. Total employment densities are highest primarily in the central area along the Thames river, with a decaying pattern of declining densities moving in any direction towards the city peripheral.

<img src="https://github.com/jacobmacdonald02/Subcentre_Typologies/blob/master/README_files/figure-markdown_github/Central%20London%20%26%20CBD-1.png" width="100%" />

This general indication of monocentricity in employment density is important to verify prior to the application of a subcentre identification model built on density gradient decay. While many cities follow patterns of clustered employment density towards the geographic centre of the city, a first stage mapping of current employment densities is important.

The central point of London which serves as the main employment hub is known as the Central Activities Zone (CAZ), a well delineated geographic area serving as the anchor for London's economy and competitive location for businesses and industries. This CAZ encompasses the heart of London, the UK and even international financial industries, cultural amenities, entertainment, shopping and tourism. As a relatively small geographic zone, this particular employment centre is responsible for around 10% of all UK output (City of London XXXX).

The definition of the main CBD, from which monocentric distances are calculated, is key for the identification of employment subcentres with the exponentially decaying method. While there is much discussion on defining a potentially unique CBD point within urban areas, we choose the CBD to be the WZ with the highest employment density. In the sample for London this corrsponds to the area covering Plantation Place in the City of London, one of the largest office development areas and the primary financial district of London. While choosing the densest employment tract may not necessarily correspond to a city's central business district location, in the case of London this location is well centrally placed. The CBD is found to be in the main hub of the CAZ and located almost directly halfway between Charing Cross - the conventional "Centre of London", and Canary Wharf - London's well known secondary CBD housing much of the country's financial sector.

    ##         WZ_CD    LAD_CD         LAD_NM    area_ha employment  density
    ## 524 E33031521 E09000001 City of London 0.05872121       5173 88094.23

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/Central London & CBD-1.png" width="100%" />

Patterns of registered business density deciles follow very similar patterns as with employment level density. A central core area of very high business density towards the central area of the city decaying over space as we move into the city periphery. There are marginal changes to the spatial pattern of business density in London from 2013 to 2019, both highlighting the importance and stability of the geographic centre of the city for business and employment concentrations.

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/London Map of Business Density 2013-1.png" width="100%" />

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/London Map of Business Density 2019-1.png" width="100%" />

Total employment in 2011 was 4,500,481 across 157,353 hectares. London is split into 32 boroughs alongside the central City of London. These 33 regions vary in terms of the size and distribution of employment levels, and the respective density of employment. Below we show the general distribution of employment across the WZ census tracts for each of the 33 boroughs in the Greater London Municipality, ranked by their average distance to the dense CBD of the city.

|                        | Area (ha) | Employment | Avg. Tract Size | Avg. Tract Employment | Max. Density | Avg. Density | Avg. Dist to CBD (km) |
|------------------------|:---------:|:----------:|:---------------:|:---------------------:|:------------:|:------------:|:---------------------:|
| City of London         |   290.12  |   356706   |       0.83      |        1022.08        |   88094.23   |    1828.54   |          0.93         |
| Southwark              |  2884.47  |   183496   |      10.09      |         641.59        |    8140.60   |    311.24    |          2.88         |
| Tower Hamlets          |  1973.80  |   234726   |       7.86      |         935.16        |   14751.53   |    456.90    |          3.01         |
| Islington              |  1485.73  |   167159   |       4.82      |         542.72        |    5562.65   |    437.92    |          3.41         |
| Hackney                |  1907.36  |   103604   |       8.51      |         462.52        |    2968.11   |    256.51    |          3.84         |
| Camden                 |  2180.31  |   272367   |       4.39      |         548.02        |    6734.58   |    556.12    |          4.48         |
| Westminster            |  2147.12  |   579739   |       2.00      |         539.29        |   15821.82   |    880.70    |          4.49         |
| Lambeth                |  2681.28  |   137664   |      11.61      |         595.95        |    1322.35   |    116.20    |          6.04         |
| Kensington and Chelsea |  1213.47  |   116546   |       4.87      |         468.06        |    2954.71   |    192.69    |          7.50         |
| Lewisham               |  3516.74  |    78895   |      20.93      |         469.61        |    460.73    |     43.81    |          7.87         |
| Newham                 |  3623.53  |   103887   |      20.02      |         573.96        |    710.35    |     57.41    |          8.35         |
| Haringey               |  2958.42  |    81001   |      16.91      |         462.86        |    1732.03   |     62.06    |          9.11         |
| Wandsworth             |  3426.79  |   117924   |      13.65      |         469.82        |    712.91    |     74.21    |          9.46         |
| Waltham Forest         |  3881.80  |    79221   |      25.21      |         514.42        |    285.07    |     37.21    |          9.77         |
| Hammersmith and Fulham |  1638.90  |   124530   |       8.15      |         619.55        |    2166.53   |    140.86    |          9.79         |

This table shows the extent to which employment and employment density fall as we move further away from the central area of the city. Significant employment densities are found in the most central boroughs in London which correspond to those inner CAZ areas responsible for a large portion of the workforce, output and economic activity of the city and country as a whole including: City of London, Southwark, and Tower Hamlets. These aggregate borough level statistics however mask much more detailed spatial patterns. Building a series of employment centre and subcentre zones using granular open data allows us to identify these employment hotspots across the entire municipality.

3. Employment Subcentre Identification
--------------------------------------

The literature on subcentre identification is wide and employs a range of different methodologies. Primarily, subcentres can be identified using a functional form approach in comparing employment densities to expected values with appropriate decaying on distance from a central point; or highlight spatial clusters and similarities in employment dynamics based on local spatial autocorrelation parameters. The choice of method is dependant on the study context and underlying assumptions on the spatial structure of the urban area. In urban areas described well by some historic and geographic area (CBD) from which employment decays exponentially, we can use the estimated shape of this decay to identify outlier areas based on some threshold values.

The subcentre identification algorithm here is based off a parametric model of monocentric employment density (sources xxxxx). A more flexible functional form approach to the Giuliano and Small (1991) and Ban et al. (2017). The subcentre identification algorithm used is based on exponentially decaying cutoffs used to identify clusters of local tracts of employment which have densities and total employment levels exceeding the expected value of density from a purely monocentric decay model of employment density.

### 3.1. Method of Exponentially Decaying Cutoffs

This method of exponential decay is adopted from Ban et al. (2017) and adopted for the London context.

The method of exponentially decaying cutoff is undertaken in two parts: firstly by identifying candidate tracts which have significant employment density, and secondly in grouping contiguous candidate tracts and identifying subcentres via total employment levels.

Underlying the identification is the concept of exponentialy decaying employment density from a monocentric CBD. Specifying this formulation, where *x* represents distance to the CBD (such that at the CBD *x* = 0), the expected employment density at any location periphiral to the CBD (*D*<sub>*x*</sub>) can be estimated under the assumption of monocentric decay over space. Using the corresponding value of peak employment density at the CBD, $\\underline{D}$, as we move further away from the core employment centre density can be expected to decay at an exponential rate along some density gradient defined by (some negative function) *f*(*x*).

$$D\_x = \\underline{D} \\cdot e^{f(x)}$$

In this above specification $\\underline{D}$ represents some basline value of employment density at the central location, with absolute density declining at an exponential rate. The log version represents the relative change, or the proportional rate at which density decays with respect to the CBD.

$$\\ln(D\_x) = \\ln(\\underline{D}) + f(x)$$

The function, *f*(*x*), represents the form of the assumed employment density gradient decline over space. In Ban et al. (2017), a linear form of *f*(*x*)= − *α* ⋅ *x* was used to estimate the gradient. assumption on the gradient (linear in the proportional decrease in density; exponential in the absolute) thus would dictate that the rate at which employment density changes is constant over space. This is the functional form assumed in the subcentre identification work for Los Angeles (Eq. page 10 Ban et al. (2017)).

*f*(*x*)=*α* + *β* ⋅ ln(*x*)

In the case of London, employment density patterns across the city highlight clear strong central tendencies. The unique relative symmetry of the city further enforces this centrality. As such, identifying subcentre outliers from an exponential decay from this clearly centrally dense employment location will be able to identify global subcentres and candidate areas where employment positively deviates from this expectation.

We update the Ban et al. (2017) method for London by allowing for a more flexible selection of input parameters accounting for core employment density, and further by choosing a more flexible functional form for the employment decay gradient.

The subcentre identification algorithm proceeds as follows:

1- 2- 3- Candidate tracts are elevated to subcentres if

### 3.2. Parameter Fine-Tuning

Two key parameters on employment level and density are used in the exponentially decaying subcentre identification method by Giuliano and Small (1991) and subsequently adapted by Ban et al. (2017). These include the

An updated computational algorithm to delineate urban employment subcentres is provided and applied in Macdonald (xxxxx). This open source tool reads in small area employment density statistics and applies the above model of exponentionally decaying cutoff thresholds to identify employment areas. The density of employment at each WZ tract is compared against the expected value from that which could be predicted from a monocentrically decaying model. Where contiguous tracts of peripheral WZ's meet the above criteria, relative to the central zone, exceed employment and density values, then it can be classified as an urban employment subcentre.

The input paremeters are based on identifying the benchmark employment density from which we expect monocentric decay, the A parameter above, and the density of this central area. The updated algorithm in Macdonald (xxxx) allows for increased flexibility from Ban et al. (2017) and can thus be applied in a variety of different settings. Rather than input a direct value of starting employment and density, as is the case in the so-called "(20, 49)" model - which are essentially fine tuned exactly to the California 1980 context. Instead, we input a value of distance for both the employment and density respectively. The value, A, and density, D, needed for the model are taken as the respective sum and average value of total employment taken directly from the statistics in the area surrounding directly from the CBD point.

Secondly, the updated algorithm allows for the choice of density decay gradient function to better match observed spatial patterns. We can thus explore and evaluate the fit of varying models of moncentric decay to see which fits the data most sensibly, and against which urban employment subcentres should be evaluates.

We fine tune the choice of these two parameters in the model for London: the first to input the distance from which total employment and density are calculated; and second the functional form of the density decay. Various models and subcentre patterns are identified. The choice of model from which we continue is that where the identified CBD from the employment data and WZ geographic boundaries aligns with the broad delineation of the CAZ of central London. With this as our basis starting point, urban employment subcentres are those peripheral areas which have locally dense employment peaks in line with the central zone of the city.

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/Estimated Gradient Functions-1.png" width="100%" />

The choice of parameters for London are drawn to match the CAZ area. We want to pick up this extent as our CBD and see how peripherial subcentres emerge which have similar local density and employment peaks as London's central area.

We choose our baseline density and total employment level following a series of parameter estimation and subcentre identification. The main choices are on the value of density and employment we choose as the baseline from which threshold cutoff values are determined. Too high a baseline density or employment, too few peripherial subcentres will be identified, too low a density or employment....

We choose parameter values of D= and E= to correspond to the distance from the central area from which we will draw the baseline values of CBD employment or density. As we increase the parameter values for E, we are capturing more total employment and thus increasing the radius will increase E. The converse is true for B. As we increase the radius from which we calculate the baseline density, then we will be including more non-central WZs and the average density value will be brought down marginally.

We need to scale these parameters appropriately for the London context.

### 3.3. London's Employment Subcentres

After fine tuning the algorithm parameters for the London context, we reveal a map of employment subcentres across the city. With the granularity of WZ boundaries in core employment areas, we are able to delineate geographically granular employment areas in the city. The extent of the core CBD in central London is also highlighted with additional areas of high employment out around the city peripheral.

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/London Employment Subcentre Map-1.png" width="100%" />

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/London Employment Subcentre Map - CAZ-1.png" width="100%" />

The economy of London very much linked to geography with well defined industries tending to be associated with well defined areas.

|                 | Employment | Area (ha.) | Avg. Dist to CBD (km) | Avg. Density | Tract Size (WZ Count) |
|-----------------|:----------:|:----------:|:---------------------:|:------------:|:---------------------:|
| subcentreID\_1  |   1481900  |   3976.36  |          3.90         |    372.68    |          2314         |
| subcentreID\_35 |    26565   |   133.97   |          3.81         |    198.30    |           26          |
| subcentreID\_68 |    5051    |    70.41   |          6.27         |     71.73    |           10          |
| subcentreID\_77 |    4696    |    65.60   |          6.74         |     71.59    |           9           |
| subcentreID\_8  |   128433   |   277.03   |          1.46         |    463.61    |          130          |

|     | SC\_employment  |     SC\_area    |  SC\_distance |   SC\_density  |     tractN     |
|-----|:----------------|:---------------:|:-------------:|:--------------:|:--------------:|
|     | Min. : 4696     |   Min. : 65.60  |  Min. :1.463  |  Min. : 71.59  |   Min. : 9.0   |
|     | 1st Qu.: 5051   |  1st Qu.: 70.41 | 1st Qu.:3.812 | 1st Qu.: 71.73 |  1st Qu.: 10.0 |
|     | Median : 26565  | Median : 133.97 | Median :3.902 | Median :198.30 |  Median : 26.0 |
|     | Mean : 329329   |  Mean : 904.67  |  Mean :4.436  |  Mean :235.58  |  Mean : 497.8  |
|     | 3rd Qu.: 128433 | 3rd Qu.: 277.03 | 3rd Qu.:6.267 | 3rd Qu.:372.68 | 3rd Qu.: 130.0 |
|     | Max. :1481900   |  Max. :3976.36  |  Max. :6.738  |  Max. :463.61  |  Max. :2314.0  |

|     | SC\_employment |     SC\_area    |  SC\_distance  |   SC\_density  |     tractN    |
|-----|:---------------|:---------------:|:--------------:|:--------------:|:-------------:|
|     | Min. : 230     |   Min. : 2.354  |  Min. : 4.419  |  Min. : 61.43  |  Min. : 1.00  |
|     | 1st Qu.: 4182  | 1st Qu.: 30.902 | 1st Qu.: 6.171 | 1st Qu.: 98.02 | 1st Qu.: 5.00 |
|     | Median : 6592  | Median : 47.954 | Median : 8.072 | Median :159.26 | Median : 9.50 |
|     | Mean : 10379   |  Mean : 51.180  |  Mean : 9.924  |  Mean :198.12  |  Mean :10.47  |
|     | 3rd Qu.: 9438  | 3rd Qu.: 60.158 | 3rd Qu.:10.676 | 3rd Qu.:228.66 | 3rd Qu.:13.50 |
|     | Max. :112919   |  Max. :150.511  |  Max. :28.222  |  Max. :799.33  |  Max. :33.00  |

4. Decomposing London Subcentres By Industry Typologies
-------------------------------------------------------

We decompose employment areas in the greater municipal area according to the industry sectors of prominence located within, considering both employment and business composition. Detailed sectoral employment levels over space are limited to Census 2011 WZ aggregates of broad SIC industry sector. More detailed SIC divisions can be extracted using the open business registries to provide another indication of the types of industry sectors located over space. Additionally, relative proportions and distributions across the London WZ Classification geodemographic are used to identify any potential differences in employment areas and hotspots of the city.

The distribution of SIC industry typologies for employment subcentres are plotted and compared. In particular, we are interested in differences which exist between these industry variables for WZ which form part of employment subcentres, and in particular the core CAZ employment centre, and those which are not part of an employment area.

This analysis has a few main advantages. While detailed employment data is relatively scarce, information on registered businesses is much more common and available for many time scales (see CDRC business census datasets). While the direct modelling of employment levels themselves is too detailed to be supported by just registered businesses, we are able to link the clusters of location of employment centres to these businesses if we can identify the underlying signature of what types, and quantities, of different industries in a given area are most commonly attributed to our employment subcentre hotspots.

Thus, the signature of the SIC-codes present in an employment center can be used as a justification of the region being a center. A similar signature if detected in a region, can make the region a contender for an employment center. This approach is beneficial as we are basing the analysis on business census data which is more readily available than the employement data.

![](/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/SIC%20Colour%20Guide-1.png)

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/SIC Sector Based Proportions-1.png" width="100%" />

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/Counts and Broad SIC Breakdowns - Business Census 2013-1.png" width="100%" />

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/Counts and Broad SIC Breakdowns - Business Census 2019-1.png" width="100%" />

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/Counts and Broad SIC Breakdowns - Employment 2011-1.png" width="100%" />

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/Yearly Growth of Top Sectors-1.png" width="100%" />

<img src="/Users/jake_mac02/Dropbox/Research/Employment/Subcentre_Typologies/README_files/figure-markdown_github/LWZC Breakdown-1.png" width="100%" />
