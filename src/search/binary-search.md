# Binary Search

Binary Search é um algoritmo de busca que pode ser usado em um array ordenado, para buscar de forma eficiente um elemento, já que vai reduzindo pela metade o tamanho da busca a cada iteração.

Dado o aray <code>[10, 20, 30, 40, 50, 60, 80, 90, 100]</code>

<h3> Como podemos encontrar o elemento 100?

Uma forma de encontrar o elemento 100 seria ir checando cada elemento do array, uma vez que nós tivéssemos passado por cada elemento, poderiamos afirmar, com certeza, se esse elemento existe ou não e sua posição, seu index, que nesse caso é oito. 

Porém, essa é uma forma ineficiente de achar esse elemento, já que teriamos que passar pelo array inteiro para saber se o elemento 100, existe ou não. Executando um total de nove checagens

Sendo assim, usar o Binary Search é mais eficiente.
</h3>

## Aplicação do pseudo código

```
    var lista = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
    var alvo = 100
    var inicio = 0
    var final = lista.tamanho - 1
    var meio = (inicio + final) / 2    

    algoritmo

    inicio >= final? {
        elemento não está presente na lista, retornamos -1
    }

    alvo == lista[meio] {
        se sim retornamos o valor meio, já que ele é o index do alvo
    }

    alvo < lista[meio]? {
        se sim, como o alvo é menor que o meio, chamamos o algoritmo novamente passando como valor de final o meio - 1
    }

    alvo > lista[meio]? {
        se sim, como o alvo é maior que o meio, chamamos o algoritmo novamente passando como valor de inicio o meio + 1
    }

    fimAlgoritmo
```

## Explicação genérica mais detalhada.

<h3>O que nos interesa é a posição, index, do nosso alvo.

<br>
Então vamos pegar o tamanho do array menos um e dividir por dois, não podemos nos esquecer de arredondar o resultado, no nosso caso quando realizarmos essa operação vamos ter como retorno 4, já que a contagem do index do array começa por zero vamos pegar o quinto elemento que é o 50.


<br>
Checamos para ver se o 50 é igual ao nosso alvo se for retornamos o index = 4, no entanto, nesse caso 60 não é igual ao alvo, 100, então checamos se 60 é menor ou maior que o alvo. 

<br>
Caso fosse menor nós não precisariamos mais incluir os elementos do index 4 para cima, pois como a lista está ordenada, todos esses valores seriam maiores.

<br>
No nosso caso é menor então podemos ignorar todos os elementos do index 4 para baixo, nós então pegamos o sub-array formado a partir do index 5, e repetimos o processo até encontrarmos o alvo. Usando o index 5 como início da lista.
</h3>
    
<br>

> ### Aconselho, fortemente, você a tentar reproduzir o algoritmo sozinho antes de ver sua implementação. Mesmo que você não consiga, não fique triste, esse processo vai te ajudar no aprendizado.

<br>

### Algumas dicas:

<ul>
    <li>
    Crie variáveis para serem o início e o final da lista, são esses valores que você deve dividir por 2
    </li>
    <li>
    Não se esqueça de arredondar o valor encontrado
    </li>
    <li>
    Se o valor do início for maior ou igual ao valor do final o elemento não existe no array
    </li>
</ul> 

<br>

<details>
<summary> 
    Código em javascript
</summary>
<ul>
<ol>
<details>
<summary>
    Implementação com recurção
</summary>

~~~javascript
let arr = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]

function binarySearch(alvo, inicio, final) {
    let meio = Math.floor((inicio + final) / 2)
    
    if (inicio >= final) {
        return `O elemento não foi encontrado`
    }

    if (alvo == arr[meio]) {
        return `O elemento está no index ${meio}`
    }

    // Alvo menor que o meio
    if (alvo < arr[meio]) {
        // Não precisamos mais analizar os elementos
        // a partir do meio até o maior index
        return binarySearch(alvo, inicio, meio - 1)
    } 
    
    // alvo maior que o meio
    if (alvo > arr[meio]) {
        // Não precisamos mais analizar os elementos
        // a partir do meio até o menor index
        return binarySearch(alvo, meio + 1, final)
    }
}

console.log(binarySearch(110, 0, arr.length - 1))
~~~

</details>
</ol>
    
<ol>
<details>
<summary>
    Implementação com loop
</summary>

~~~javascript
let arr = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100]

function binarySearch(alvo) {
    let inicio = 0
    let final = arr.length - 1

    while (inicio < final) {
        let meio = Math.floor((inicio + final) / 2)
    
        if (alvo == arr[meio]) {
            return `O elemento está no index ${meio}`
        }
    
        if (alvo < arr[meio]) {      
            final = meio - 1
        } 
    
        if (alvo > arr[meio]) {
            inicio = meio + 1
        }
    }
    return `O elemento não foi encontrado`
}

console.log(binarySearch(110))
~~~


</details>
</ol>
</ul>
</details>