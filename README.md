# Investigating Netflix Movies (Investigando Filmes da Netflix)

## O que deve ser feito? 

- Realize uma análise exploratória de dados no arquivo 'netflix_data.csv' para entender melhor os filmes da década de 1990.

- Qual foi a duração de filme mais frequente na década de 1990? Salve uma resposta aproximada como um número inteiro chamado duração (use 1990 como o ano de início da década).

```
# Nessa primeira parte criei um DataFrame auxiliar para receber os dados que passarem nos filtros:
# O tipo ser 'Movie', e o 'release_year' estar entre 1990 e 1999 (década de 90)
df_aux = netflix_df[
    (netflix_df['type'] == 'Movie') &
    (netflix_df['release_year'] >= 1990) &
    (netflix_df['release_year'] < 2000)]

# Nessa parte vou usar a função 'mode()' para encontrar a moda (valor mais frequente) da coluna 'duration'
duration = int(df_aux['duration'].mode()[0])
print(duration)
```

- Um filme é considerado curto se tiver menos de 90 minutos. Conte o número de curtas-metragens de ação lançados na década de 1990 e salve esse número inteiro como 'short_movie_count'.

```
# Criando um segundo DataFrame auxiliar para receber dados de filmes que sejam do gênero ação ('Action')
df_aux2 = df_aux[df_aux['genre'] == 'Action']

# Criando uma nova coluna para definir 'short_movie' para os filmes com menos de 90 minutos
df_aux2['duration_size'] = np.where(df_aux2['duration'] < 90, "short_movie", "")

# Contando quantos filmes estão com o valor 'short_movie'
short_movie_count = (df_aux2['duration_size']== "short_movie").sum().astype(int)
print(short_movie_count)
```

## Conhecimentos reforçados:

- Python básico
- Pandas
