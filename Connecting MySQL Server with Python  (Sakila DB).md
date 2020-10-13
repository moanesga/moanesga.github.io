## Connecting MySQL Server with Python  (Sakila DB)

**Project description:** Description of two methods to connect MySQL databases to Python. With the first method it is possible easy access to the information converting tables in dictionary to have a first overview of the content. In the second method using sqlalchemy, the options are expanded to  use pandas and plotly express. Here the MySQL Sakila database (Movies) was taken as an example to transfer information in DataFrames and interactive charts with views of Customer by country including geolocation by continent.

### 1. Reading the film_list View into a pandas DataFrame

<img src="images/003_Connecting MySQL_with_Python_DataFrame_001.PNG?raw=true"/>

```film = pd.read_sql('SELECT * FROM film_list', engine)
film.head(5)
```

### 2. Assess assumptions on which statistical inference will be based

```javascript
if (isAwesome){
  return true
}
```

### 3. Support the selection of appropriate statistical tools and techniques

<img src="images/dummy_thumbnail.jpg?raw=true"/>

### 4. Provide a basis for further data collection through surveys or experiments

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
