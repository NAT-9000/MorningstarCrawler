# MorningstarCrawler
Morningstar fund sheet data scrapper and parser

Inputs:   CSV file directory with the ISIN list & MS reference
Output:   CSV file with type of asset and region allocation for each fund, plus table of consolidated stats considering list as a portfolio.

## Example of usage

### Step 1. Crawl data, save it as JSON file
```
import msDataMerge as msdm
import MorningstarScrap as scrap

path = "this is the directory where Inputs are "
scrapped_data = scrap.get_all_data(path)
scrap.save_json(scrapped_data,path)
```
### Step 2. Filter, process and merge the data into human-readable csv format.
```
table = msdm.consolidate_all_data(scrapped_data)
```
### Step 3. Save CSV in same directory as the ISIN file provided.
```
table.to_csv(path[0:path.rfind('/')]+'/'+'composition.csv', sep=',', index=True, encoding='utf-8')
```

