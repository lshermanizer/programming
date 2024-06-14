# Formatting


Use `.map()`. The data type of `df_formatted['%EL']` will be string.
```
df_formatted = pd.DataFrame({})
df_formatted['%EL'] = df['%EL'].map('{:.0f}.format)
```
