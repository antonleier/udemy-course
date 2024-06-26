# California Housing

## Source
Bei diesem Datensatz handelt es sich um eine modifizierte Version des California Housing-Datensatzes, der auf der Seite von Luís Torgo (http://www.dcc.fc.up.pt/~ltorgo/Regression/cal_housing.html) (Universität Porto) verfügbar ist. Luís Torgo hat es aus dem StatLib-Repository bezogen (das jetzt geschlossen ist). Der Datensatz kann auch von StatLib-Spiegeln heruntergeladen werden.

Dieser Datensatz erschien 1997 in einem Artikel mit dem Titel *Sparse Spatial Autoregressions* von Pace, R. Kelley und Ronald Barry, der in der Zeitschrift *Statistics and Probability Letters* veröffentlicht wurde. Sie haben es anhand der kalifornischen Volkszählungsdaten von 1990 erstellt. Es enthält eine Zeile pro Volkszählungsblockgruppe. Eine Blockgruppe ist die kleinste geografische Einheit, für die das U.S. Census Bureau Beispieldaten veröffentlicht (eine Blockgruppe hat normalerweise eine Bevölkerung von 600 bis 3.000 Personen).

## Tweaks
Der Datensatz in diesem Verzeichnis ist nahezu identisch mit dem Original, mit zwei Unterschieden:

* 207 Werte wurden zufällig aus der Spalte „total_schlafzimmer“ entfernt, sodass wir besprechen können, was mit fehlenden Daten zu tun ist.
* Ein zusätzliches kategoriales Attribut namens „ocean_proximity“ wurde hinzugefügt, das (sehr grob) angibt, ob sich jede Blockgruppe in der Nähe des Ozeans, in der Nähe der Bay Area, im Landesinneren oder auf einer Insel befindet. Dies ermöglicht die Diskussion darüber, was mit kategorialen Daten geschehen soll.

Beachten Sie, dass die Blockgruppen in den Jupyter-Notizbüchern „Bezirke“ genannt werden, einfach weil der Name „Blockgruppe“ in manchen Zusammenhängen verwirrend war.

## Einblick in die Daten

    >>> housing.info()
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 20640 entries, 0 to 20639
    Data columns (total 10 columns):
    longitude             20640 non-null float64
    latitude              20640 non-null float64
    housing_median_age    20640 non-null float64
    total_rooms           20640 non-null float64
    total_bedrooms        20433 non-null float64
    population            20640 non-null float64
    households            20640 non-null float64
    median_income         20640 non-null float64
    median_house_value    20640 non-null float64
    ocean_proximity       20640 non-null object
    dtypes: float64(9), object(1)
    memory usage: 1.6+ MB
    
    >>> housing["ocean_proximity"].value_counts()
    <1H OCEAN     9136
    INLAND        6551
    NEAR OCEAN    2658
    NEAR BAY      2290
    ISLAND           5
    Name: ocean_proximity, dtype: int64
    
    >>> housing.describe()
              longitude      latitude  housing_median_age   total_rooms  \
    count  16513.000000  16513.000000        16513.000000  16513.000000   
    mean    -119.575972     35.639693           28.652335   2622.347605   
    std        2.002048      2.138279           12.576306   2138.559393   
    min     -124.350000     32.540000            1.000000      6.000000   
    25%     -121.800000     33.940000           18.000000   1442.000000   
    50%     -118.510000     34.260000           29.000000   2119.000000   
    75%     -118.010000     37.720000           37.000000   3141.000000   
    max     -114.310000     41.950000           52.000000  39320.000000   

           total_bedrooms    population    households  median_income  
    count    16355.000000  16513.000000  16513.000000   16513.000000  
    mean       534.885112   1419.525465    496.975050       3.875651  
    std        412.716467   1115.715084    375.737945       1.905088  
    min          2.000000      3.000000      2.000000       0.499900  
    25%        295.000000    784.000000    278.000000       2.566800  
    50%        433.000000   1164.000000    408.000000       3.541400  
    75%        644.000000   1718.000000    602.000000       4.745000  
    max       6210.000000  35682.000000   5358.000000      15.000100
 
