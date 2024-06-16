# Formatting

## Display full dataframe in Jupyter Notebook
```
from IPython.display import display, HTML
display(HTML(df.iloc[:10].to_html()))
```

## Formatting
Use `.map()`. The data type of `df_formatted['%EL']` will be string.
```
df_formatted = pd.DataFrame({})
df_formatted['%EL'] = df['%EL'].map('{:.0f}.format)
```
