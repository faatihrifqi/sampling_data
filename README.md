# sampling_data

Simple data sampling using bash script.

## Load the data

First of all we need to download sample data
```
curl -L --create-dirs -O --output-dir data https://github.com/labusiam/dataset/raw/main/weather_data.xlsx
```

## Preprocess the data

Since the downloaded excel had two sheets, we convert both of them to csv
```
in2csv -n weather_data.xlsx
in2csv weather_data.xlsx --sheet weather_2014 > weather_2014.csv
in2csv weather_data.xlsx --sheet weather_2015 > weather_2015.csv
```

We no longer need weather_data.xlsx
```
rm weather_data.xlsx
```

## Sampling Time

Finally, we did the sampling using shuf command, since I couldn't get sample-stream to work
```
# sample -r 0.3 weather.csv > sample_weather.csv
shuf -n 110 weather.csv > sample_weather.csv
```
