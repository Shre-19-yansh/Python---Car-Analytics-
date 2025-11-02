Q1.	Using Pandas, read the "cars.csv" dataset
``` python
cars_pd = pd.read_csv('C:\\Users\\shrey\\OneDrive\\Desktop\\cars.csv')
cars_pd
```
<img width="755" height="159" alt="image" src="https://github.com/user-attachments/assets/f28d0413-968c-474b-9dac-7bba0a3da8ad" /> <img width="373" height="154" alt="image" src="https://github.com/user-attachments/assets/56bd2296-bdfa-49fd-8b02-a6e3c2620bfb" />

- The data regarding cars, make, type etc in tabluar form

Q2.	Perform exploratory data analysis

``` python
cars_pd.info()
cars_pd.describe()
```

<img width="373" height="494" alt="image" src="https://github.com/user-attachments/assets/d010e3df-5b43-44e8-a6f2-72b97907dfe9" /> <img width="720" height="137" alt="image" src="https://github.com/user-attachments/assets/56dc439c-457f-4b21-bd0f-26b4224c3206" /> <img width="388" height="133" alt="image" src="https://github.com/user-attachments/assets/5d5cf9c9-d03f-4ddf-b3aa-6ef70a0a424f" />

- No Null data in the column
- Overall statistical data of the information 
  
Q3.	Remove $ sign and comma (,) from MSRP and Invoice columns

``` python
cars_pd['MSRP'] = cars_pd['MSRP'].str.replace('$', '', regex = False)
cars_pd
```

 <img width="894" height="191" alt="image" src="https://github.com/user-attachments/assets/0fa73e1b-a5f3-4024-b80b-63265ee1128d" />

 - $ has been removed from the MRSP column.

 
``` python
cars_pd['Invoice'] = cars_pd['Invoice'].str.replace(',','', regex = False)
cars_pd
```

<img width="1560" height="382" alt="image" src="https://github.com/user-attachments/assets/fa1941fa-ccc6-4920-b899-b136762c8074" />

- , has been removed from the Invoice column. 

Q4.	Convert MSRP and Invoice columns to integer datatypes.

``` python
cars_pd['MSRP'] = cars_pd['MSRP'].str.replace(',','', regex = False)
cars_pd['MSRP'] = cars_pd['MSRP'].astype(float)
cars_pd['Invoice'] = cars_pd['Invoice'].str.replace('$', '', regex = False)
cars_pd['Invoice'] =  cars_pd['Invoice'].astype(float)
```

 <img width="783" height="198" alt="image" src="https://github.com/user-attachments/assets/43fa035c-6ce9-4fd6-b324-fbef1889e74d" />

- Both the columns have been converted into integers

Q5.	Plot a scatterplot between 'Horsepower' and 'MSRP'. Use the 'Cylinders' column to display color.

``` python
cars_pd.plot(kind = 'scatter', x = 'Horsepower', y = 'MSRP', c = 'Cylinders')
plt.title('Horsepower vs MSRP')
```

 <img width="470" height="387" alt="image" src="https://github.com/user-attachments/assets/cc1b3e96-3a55-4bc2-b217-3162b80d8149" />

- The plot shows a positive link between Horsepower and MSRP — higher horsepower cars cost more. Vehicles with more cylinders are generally pricier and more powerful.
  
Q6.	Plot the wordcloud of the Make column

``` python
text = ' '.join(cars_pd['Make'].astype(str))
wordcloud = WordCloud().generate(text)
plt.imshow(wordcloud)
plt.axis('off')
plt.show()
```

 <img width="804" height="422" alt="image" src="https://github.com/user-attachments/assets/1c0c3240-1b99-4d8e-9b08-f2521ee8d780" />

- The word cloud shows that Toyota, Chevrolet, Mercedes-Benz, and Ford are the most common car manufacturers in the dataset, indicating their large model variety or strong market presence.

Q7.	Plot the histogram of Make and Type of the car using Plotly Express

``` python
cars_pd['Make'].value_counts().plot(kind='bar')
plt.title('Frequency of Car Makes')
plt.xlabel('Car Make')
plt.ylabel('Frequency')
```

 <img width="214" height="208" alt="image" src="https://github.com/user-attachments/assets/80591377-743b-44ff-b699-b74b20061c30" />

 - The bar chart shows that Toyota, Chevrolet, Ford, and Mercedes-Benz have the highest number of models, indicating they dominate the dataset with greater variety.

``` python
cars_pd['Type'].value_counts().plot(kind = 'bar')
plt.title('Frequency of Car type')
plt.xlabel('Car type')
plt.ylabel('Frequency')
```

 <img width="237" height="203" alt="image" src="https://github.com/user-attachments/assets/9f553bb6-4c8b-4973-a6a7-e1686122832c" />

 - The chart shows that Sedans dominate the dataset, followed by SUVs and Sports cars, while Hybrids are the least common type.

Q8.	Find out which manufacturer has high number of Sports type

``` python
sport_cars = cars_pd[cars_pd['Type'] == 'Sports']
sport_count = sport_cars['Make'].value_counts()
sport_count
```

 <img width="622" height="738" alt="image" src="https://github.com/user-attachments/assets/d90e776f-6b66-41be-afff-83974cac6175" />

- The table shows that Porsche has the highest number of car models (6), followed by Mercedes-Benz (5). Brands like Audi, BMW, and Jaguar also have multiple models, while several others have only one entry each.


Q9.	Find out which manufacturers has Hybrids

``` python
cars_pd.loc[cars_pd['Type'] == 'Hybrid']
```

 <img width="1354" height="142" alt="image" src="https://github.com/user-attachments/assets/0d6b938f-3e76-45cb-9e11-f7982ef0ed69" />

 - The table shows that all Hybrid cars in the dataset come from Asian manufacturers — specifically Honda and Toyota.

