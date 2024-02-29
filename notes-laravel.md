**Illuminate\Database\Eloquent\Collection** oferece uma ampla variedade de métodos para manipulação e iteração de coleções de modelos Eloquent. Aqui está uma lista de alguns dos métodos mais comuns com descrições e exemplos:

1. **all()**: Retorna todos os itens da coleção.
```
$collection = App\Models\User::all();
```
2. **avg()**: Retorna a média de um valor específico para todos os itens da coleção.
```
$averageAge = App\Models\User::all()->avg('age');
```
3. **count()**: Retorna o número de itens na coleção.
```
$totalUsers = App\Models\User::all()->count();
```
4. **each()**: Itera sobre cada item na coleção e executa uma função de retorno de chamada para cada um.
```
$users = App\Models\User::all();
$users->each(function ($user) {
    echo $user->name;
});
```
5. **first()**: Retorna o primeiro item na coleção.
```
$firstUser = App\Models\User::all()->first();
```
6. **last()**: Retorna o último item na coleção.
```
$lastUser = App\Models\User::all()->last();
```
7. **pluck()**: Obtém uma lista de valores de uma determinada chave dos itens da coleção.
```
$userNames = App\Models\User::all()->pluck('name');
```
8. **push()**: Adiciona um item à coleção.
```
$user = new App\Models\User();
$user->name = 'John Doe';
$users = App\Models\User::all();
$users->push($user);
```

Recupera todos os registros de um modelo específico do banco de dados, você pode usar uma variedade de outros métodos disponíveis na classe Illuminate\Database\Eloquent\Collection e no próprio Eloquent para recuperar registros de forma mais específica. Aqui estão alguns exemplos:

1. **find()**: Recupera um único modelo pelo seu ID.
```
$user = App\Models\User::find(1);
```
2. **findOrFail()**: Recupera um único modelo pelo seu ID e lança uma exceção **ModelNotFoundException** se o modelo não for encontrado.
```
$user = App\Models\User::findOrFail(1);
```
3. **where()**: Recupera todos os modelos que correspondem a uma condição específica.
```
$users = App\Models\User::where('status', 'active')->get();
```
4. **first()**: Recupera o primeiro modelo que corresponde a uma condição específica.
```
$user = App\Models\User::where('status', 'active')->first();
```
5. **orderBy()**: Ordena os resultados da consulta por uma coluna específica.
```
$users = App\Models\User::orderBy('created_at', 'desc')->get();
```
6. **limit()**: Limita o número de resultados retornados.
```
$users = App\Models\User::limit(10)->get();
```
7. **offset()**: Define o número de resultados a serem ignorados antes de retornar os resultados.
```
$users = App\Models\User::offset(10)->get();
```
8. **groupBy()**: Agrupa os resultados da consulta por uma coluna específica.
```
$orders = App\Models\Order::groupBy('user_id')->get();
```
9. **exists()**: Verifica se há algum resultado correspondente à consulta.
```
$exists = App\Models\User::where('status', 'active')->exists();
```
10. **doesntExist()**: Verifica se não há nenhum resultado correspondente à consulta.
```
$doesntExist = App\Models\User::where('status', 'deleted')->doesntExist();
```

