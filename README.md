1)Observe o trecho de código abaixo: int INDICE = 13, SOMA = 0, K = 0;
Enquanto K < INDICE faça { K = K + 1; SOMA = SOMA + K; }
Imprimir(SOMA);
Ao final do processamento, qual será o valor da variável SOMA? 

**R:** Vamos analisar o trecho de código fornecido. O código parece estar escrito em uma sintaxe semelhante a de linguagens como Pascal ou pseudo-código. Aqui está uma descrição detalhada do que acontece:

```plaintext
int INDICE = 13, SOMA = 0, K = 0;
Enquanto K < INDICE faça { 
    K = K + 1; 
    SOMA = SOMA + K; 
}
Imprimir(SOMA);
```

### Explicação do Código

1. **Inicialização das Variáveis**:
   - `INDICE` é inicializado com o valor `13`.
   - `SOMA` é inicializado com o valor `0`.
   - `K` é inicializado com o valor `0`.

2. **Loop**:
   - O loop `Enquanto K < INDICE faça` executa enquanto a condição `K < INDICE` for verdadeira. 
   - Dentro do loop:
     - `K` é incrementado em `1` (`K = K + 1`).
     - `SOMA` é atualizado com o valor de `SOMA + K`.

### Iteração do Loop

Vamos ver como o valor de `SOMA` muda a cada iteração:

- **Antes do loop**: `K = 0`, `SOMA = 0`.
- **1ª iteração**: `K = 1`, `SOMA = 0 + 1 = 1`.
- **2ª iteração**: `K = 2`, `SOMA = 1 + 2 = 3`.
- **3ª iteração**: `K = 3`, `SOMA = 3 + 3 = 6`.
- **4ª iteração**: `K = 4`, `SOMA = 6 + 4 = 10`.
- **5ª iteração**: `K = 5`, `SOMA = 10 + 5 = 15`.
- **6ª iteração**: `K = 6`, `SOMA = 15 + 6 = 21`.
- **7ª iteração**: `K = 7`, `SOMA = 21 + 7 = 28`.
- **8ª iteração**: `K = 8`, `SOMA = 28 + 8 = 36`.
- **9ª iteração**: `K = 9`, `SOMA = 36 + 9 = 45`.
- **10ª iteração**: `K = 10`, `SOMA = 45 + 10 = 55`.
- **11ª iteração**: `K = 11`, `SOMA = 55 + 11 = 66`.
- **12ª iteração**: `K = 12`, `SOMA = 66 + 12 = 78`.
- **13ª iteração**: `K = 13`, `SOMA = 78 + 13 = 91`.

Após a 13ª iteração, `K` se torna `13`, e o loop para porque `K` não é mais menor que `INDICE` (13).

### Resultado Final

O valor final da variável `SOMA` após a execução do loop é `91`.

Portanto, o valor da variável `SOMA` ao final do processamento é `91`.
___
2)Dado a sequência de Fibonacci, onde se inicia por 0 e 1 e o próximo valor sempre será a soma dos 2 valores anteriores (exemplo: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...), escreva um programa na linguagem que desejar onde, informado um número, ele calcule a sequência de Fibonacci e retorne uma mensagem avisando se o número informado pertence ou não a sequência.

**R:**

```plaintext
function pertenceFibonacci(n) {
    if (n < 0) return false;
    let a = 0, b = 1;
    while (a <= n) {
        if (a === n) return true;
        [a, b] = [b, a + b];
    }
    return false;
}
function main() {
    const numero = parseInt(prompt("Informe um número para verificar se pertence à sequência de Fibonacci:"), 10);
    if (isNaN(numero)) {
        console.log("Por favor, informe um número válido.");
    } else if (pertenceFibonacci(numero)) {
        console.log(`O número ${numero} pertence à sequência de Fibonacci.`);
    } else {
        console.log(`O número ${numero} não pertence à sequência de Fibonacci.`);
    }
}

main();
```
___
3)Dado um vetor que guarda o valor de faturamento diário de uma distribuidora, faça um programa, na linguagem que desejar, que calcule e retorne:
• O menor valor de faturamento ocorrido em um dia do mês;
• O maior valor de faturamento ocorrido em um dia do mês;
• Número de dias no mês em que o valor de faturamento diário foi superior à média mensal.

IMPORTANTE:
a) Usar o json ou xml disponível como fonte dos dados do faturamento mensal;
b) Podem existir dias sem faturamento, como nos finais de semana e feriados. Estes dias devem ser ignorados no cálculo da média;

**R:**

Para resolver o problema descrito, vamos criar um programa em Python que lê dados de faturamento de um arquivo JSON e calcula:

1. O menor valor de faturamento ocorrido em um dia do mês.
2. O maior valor de faturamento ocorrido em um dia do mês.
3. O número de dias no mês em que o valor de faturamento diário foi superior à média mensal, ignorando os dias sem faturamento.

### Passos a Seguir

1. **Preparar o arquivo JSON com os dados do faturamento.**
2. **Escrever o código Python para processar os dados e calcular os valores desejados.**

### Exemplo de Arquivo JSON

Vamos supor que temos um arquivo JSON chamado `faturamento.json` com o seguinte conteúdo:

```json
[
    {"dia": 1, "valor": 1500},
    {"dia": 2, "valor": 0},
    {"dia": 3, "valor": 2000},
    {"dia": 4, "valor": 0},
    {"dia": 5, "valor": 1800},
    {"dia": 6, "valor": 1600},
    {"dia": 7, "valor": 0},
    {"dia": 8, "valor": 1900},
    {"dia": 9, "valor": 0},
    {"dia": 10, "valor": 1700},
    {"dia": 11, "valor": 0},
    {"dia": 12, "valor": 2200},
    {"dia": 13, "valor": 0},
    {"dia": 14, "valor": 0},
    {"dia": 15, "valor": 2400}
    // Adicione mais dias conforme necessário
]
```

### Código Python

Aqui está o código Python para ler o arquivo JSON, processar os dados e calcular os valores desejados:

```python
import json

def calcular_faturamento(filepath):
    
    with open(filepath, 'r') as file:
        dados = json.load(file)
    
    
    valores = [registro['valor'] for registro in dados if registro['valor'] > 0]
    
    if not valores:
        print("Não há dados de faturamento para calcular.")
        return
    

    menor_faturamento = min(valores)
    maior_faturamento = max(valores)
    

    media_mensal = sum(valores) / len(valores)
    

    dias_acima_media = sum(1 for valor in valores if valor > media_mensal)
    

    print(f"Menor valor de faturamento: R${menor_faturamento:.2f}")
    print(f"Maior valor de faturamento: R${maior_faturamento:.2f}")
    print(f"Número de dias com faturamento acima da média mensal: {dias_acima_media}")


calcular_faturamento('faturamento.json')
```

### Explicação do Código

1. **Leitura do Arquivo JSON**:
   - O código usa `json.load` para ler o arquivo JSON e carregar os dados em uma lista de dicionários.

2. **Filtragem dos Dados**:
   - Filtra os valores de faturamento, ignorando os dias com valor 0.

3. **Cálculo dos Valores**:
   - Usa `min()` e `max()` para encontrar o menor e o maior valor de faturamento, respectivamente.
   - Calcula a média mensal dos valores de faturamento.
   - Conta quantos dias têm faturamento acima da média mensal usando uma compreensão de lista.

4. **Exibição dos Resultados**:
   - Imprime os resultados formatados.

O programa exibirá o menor valor, o maior valor e o número de dias com faturamento acima da média mensal.

___
4)Dado o valor de faturamento mensal de uma distribuidora, detalhado por estado:
• SP – R$67.836,43
• RJ – R$36.678,66
• MG – R$29.229,88
• ES – R$27.165,48
• Outros – R$19.849,53

Escreva um programa na linguagem que desejar onde calcule o percentual de representação que cada estado teve dentro do valor total mensal da distribuidora.

**R:**

Vamos criar uma página HTML com JavaScript para calcular e exibir as informações baseadas nos valores de faturamento mensal detalhados por estado. O que queremos fazer é calcular:

1. O percentual de faturamento de cada estado em relação ao total.
2. O estado com o maior faturamento.
3. O estado com o menor faturamento.

Aqui está o código HTML com o JavaScript incluído para realizar esses cálculos:

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Faturamento Mensal por Estado</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-bottom: 20px;
        }
        table, th, td {
            border: 1px solid black;
        }
        th, td {
            padding: 8px;
            text-align: right;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>
    <h1>Faturamento Mensal por Estado</h1>
    <table id="faturamentoTabela">
        <thead>
            <tr>
                <th>Estado</th>
                <th>Faturamento (R$)</th>
                <th>Percentual (%)</th>
            </tr>
        </thead>
        <tbody>
        </tbody>
    </table>
    <div id="resultados">
        <p id="estadoMaior">Estado com o maior faturamento: </p>
        <p id="estadoMenor">Estado com o menor faturamento: </p>
    </div>
    <script>
        const faturamento = {
            "SP": 67836.43,
            "RJ": 36678.66,
            "MG": 29229.88,
            "ES": 27165.48,
            "Outros": 19849.53
        };

        function calcularFaturamento() {
            const totalFaturamento = Object.values(faturamento).reduce((acc, valor) => acc + valor, 0);


            const tabela = document.getElementById('faturamentoTabela').getElementsByTagName('tbody')[0];
            const estadoMaior = document.getElementById('estadoMaior');
            const estadoMenor = document.getElementById('estadoMenor');

            let maiorFaturamento = -Infinity;
            let menorFaturamento = Infinity;
            let estadoMaiorFaturamento = '';
            let estadoMenorFaturamento = '';

            for (const [estado, valor] of Object.entries(faturamento)) {
                const percentual = ((valor / totalFaturamento) * 100).toFixed(2);
                

                const row = tabela.insertRow();
                row.insertCell().textContent = estado;
                row.insertCell().textContent = valor.toFixed(2);
                row.insertCell().textContent = `${percentual}%`;


                if (valor > maiorFaturamento) {
                    maiorFaturamento = valor;
                    estadoMaiorFaturamento = estado;
                }

                if (valor < menorFaturamento) {
                    menorFaturamento = valor;
                    estadoMenorFaturamento = estado;
                }
            }


            estadoMaior.textContent += `${estadoMaiorFaturamento} (R$${maiorFaturamento.toFixed(2)})`;
            estadoMenor.textContent += `${estadoMenorFaturamento} (R$${menorFaturamento.toFixed(2)})`;
        }


        window.onload = calcularFaturamento;
    </script>
</body>
</html>
```

### Explicação do Código

1. **HTML**:
   - A estrutura HTML inclui um título, uma tabela para exibir os dados e uma seção para mostrar os resultados.
   - A tabela possui cabeçalhos para os estados, faturamento e percentual.

2. **CSS**:
   - Inclui estilos básicos para a tabela e o corpo da página.

3. **JavaScript**:
   - **Dados de Faturamento**: Um objeto contém os valores de faturamento para cada estado.
   - **Função `calcularFaturamento()`**: Calcula o total de faturamento, percentual de cada estado em relação ao total, e preenche a tabela com esses dados.
   - Identifica o estado com o maior e menor faturamento e atualiza os elementos correspondentes com essas informações.
   - **`window.onload`**: Garante que a função de cálculo seja chamada assim que a página for carregada.
___
5)Escreva um programa que inverta os caracteres de um string.

IMPORTANTE:
a) Essa string pode ser informada através de qualquer entrada de sua preferência ou pode ser previamente definida no código;
b) Evite usar funções prontas, como, por exemplo, reverse;

**R:**

Vou fornecer um exemplo de como criar uma página HTML com JavaScript para inverter os caracteres de uma string. O código inclui um campo de entrada onde o usuário pode digitar uma string, e um botão para inverter a string. O resultado será exibido na página.

### Código HTML e JavaScript

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inverter String</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        label, input, button {
            display: block;
            margin: 10px 0;
        }
        #resultado {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1>Inverter String</h1>
    <label for="entrada">Digite uma string:</label>
    <input type="text" id="entrada" placeholder="Digite aqui">
    <button onclick="inverterString()">Inverter</button>
    <div id="resultado"></div>

    <script>
        function inverterString() {
            const entrada = document.getElementById('entrada').value;
            
            function inverter(s) {
                let invertida = '';
                for (let i = s.length - 1; i >= 0; i--) {
                    invertida += s[i];
                }
                return invertida;
            }

            const resultado = inverter(entrada);

            document.getElementById('resultado').textContent = `String invertida: ${resultado}`;
        }
    </script>
</body>
</html>
```

### Explicação do Código

1. **HTML**:
   - **Campo de Entrada**: Um campo de texto (`<input>`) onde o usuário pode digitar a string.
   - **Botão**: Um botão que, quando clicado, chama a função `inverterString()` para processar a string.
   - **Div de Resultado**: Um `<div>` onde o resultado da string invertida será exibido.

2. **CSS**:
   - Adiciona alguns estilos básicos para melhorar a aparência da página.

3. **JavaScript**:
   - **Função `inverterString()`**:
     - Obtém o valor da string do campo de entrada.
     - Chama a função interna `inverter(s)` para inverter a string.
     - Exibe o resultado invertido na `<div>` com o id `resultado`.
   - **Função `inverter(s)`**:
     - Recebe a string `s` como argumento.
     - Cria uma nova string `invertida` e preenche-a com os caracteres de `s` na ordem inversa usando um loop.
     - Retorna a string invertida.

### Executando o Código

1. Salve o código em um arquivo chamado `inverter_string.html`.
2. Abra o arquivo em um navegador.

A página permitirá que você digite uma string, clique no botão para inverter, e veja o resultado imediatamente na mesma página.
