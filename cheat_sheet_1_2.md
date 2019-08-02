## JOIN DATASETS

#### Concatenate

Stick two dataframes or series together along the X or Y axis. I haven't found a great use case for `concat` over `merge`.

Syntax: `df.concat([series1, series2], axis=X, default outer)`

Example: `order_products = pd.concat([order_products_prior, order_products_train])`

#### Merge

This is the important one. Seems to function in a similar fashion to a SQL `JOIN`.

Example 1: `merged = pd.merge(subset, order_products[['order_id', 'add_to_cart_order']], how='left', on='order_id')

Example 2: df = (income
          .merge(lifespan)
          .merge(population)
          .merge(entities[['country', 'name', 'world_6region']]
                 , left_on="geo", right_on="country")
          .drop(columns=['geo', 'country'])
          .rename(columns = {
              'time': 'year'
              , 'income_per_person_gdppercapita_ppp_inflation_adjusted': 'income'
              , 'life_expectancy_years': 'lifespan'
              , 'population_total': 'population'
              , 'name': 'country'
              , 'world_4region': 'region4'
              , 'world_6region': 'region6'
          }))`
         
The above example demonstrates merging, dropping, and renaming in one chain.

#### Melt

I haven't used this one much yet either. The use case for `melt` is conversion of a non-tidy dataset to a tidy one.

`Example: tidy1 = table1.melt(id_vars='index')`
