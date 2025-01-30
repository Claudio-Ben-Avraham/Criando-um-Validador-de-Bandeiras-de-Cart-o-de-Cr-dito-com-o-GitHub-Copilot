Validador de Bandeiras de Cartão de Crédito com o GitHub Copilot

Este repositório contém um projeto simples que usa o GitHub Copilot para criar um validador de bandeiras de cartão de crédito. O validador verifica se um número de cartão de crédito corresponde a uma das bandeiras populares, como Visa, MasterCard, American Express, Discover, entre outras.
Funcionalidades

    Verificar o número do cartão de crédito e identificar a bandeira correspondente (Visa, MasterCard, American Express, etc.).
    Validação de formato com base nos números típicos das bandeiras de cartões.
    Uso do GitHub Copilot para gerar código de forma rápida e eficiente.

Requisitos

Antes de começar, você precisará de:

    Conta no GitHub com GitHub Copilot habilitado.
    Editor de código como Visual Studio Code.
    Dependências mínimas (se necessário, como bibliotecas de regex).

Como Criar o Validador com o GitHub Copilot

Siga os passos abaixo para criar o validador utilizando o GitHub Copilot:
1. Configuração Inicial do Projeto

    Abra o Visual Studio Code (ou seu editor de preferência).
    Crie um novo diretório para o projeto e entre nele:

mkdir validador-cartao-credito
cd validador-cartao-credito

Inicialize um repositório Git:

    git init

2. Criação do Script para Validação

No editor, crie um arquivo chamado validador.js para implementar a validação.

Você pode usar o GitHub Copilot para gerar funções de validação simples. O Copilot sugerirá código à medida que você digitar.
3. Definindo as Bandeiras

As bandeiras de cartões de crédito geralmente possuem prefixos específicos e a quantidade de dígitos. O GitHub Copilot pode sugerir expressões regulares para identificar esses prefixos e tamanhos de número.
Exemplo de código:

// Função para verificar a bandeira do cartão de crédito
function identificarBandeira(numeroCartao) {
    const bandeiras = {
        visa: /^4[0-9]{12}(?:[0-9]{3})?$/,
        mastercard: /^5[1-5][0-9]{14}$/,
        amex: /^3[47][0-9]{13}$/,
        discover: /^6(?:011|5[0-9]{2})[0-9]{12}$/,
        // Adicione outras bandeiras conforme necessário
    };

    for (const [bandeira, regex] of Object.entries(bandeiras)) {
        if (regex.test(numeroCartao)) {
            return bandeira; // Retorna o nome da bandeira encontrada
        }
    }
    return "Desconhecida"; // Caso não corresponda a nenhuma bandeira
}

4. Adicionando Funcionalidades de Validação

Além da identificação da bandeira, podemos adicionar a validação do número do cartão com o algoritmo de Luhn, que verifica se o número do cartão de crédito é válido.
Exemplo de Validação com o Algoritmo de Luhn:

// Função para validar o número do cartão de crédito usando o algoritmo de Luhn
function validarCartao(numeroCartao) {
    let soma = 0;
    let par = false;
    for (let i = numeroCartao.length - 1; i >= 0; i--) {
        let digito = parseInt(numeroCartao.charAt(i));
        if (par) {
            digito *= 2;
            if (digito > 9) digito -= 9;
        }
        soma += digito;
        par = !par;
    }
    return soma % 10 === 0;
}

5. Combinando Validação e Identificação da Bandeira

Combine as funções de identificação da bandeira e a validação para um processo completo de verificação.

function validarEIdentificar(numeroCartao) {
    if (validarCartao(numeroCartao)) {
        const bandeira = identificarBandeira(numeroCartao);
        console.log(`Cartão válido! Bandeira: ${bandeira}`);
    } else {
        console.log("Número de cartão inválido.");
    }
}

6. Testando o Validador

Após escrever o código, você pode testar seu validador chamando a função com diferentes números de cartão.

validarEIdentificar('4111111111111111'); // Exemplo de número de cartão Visa
validarEIdentificar('5111111111111111'); // Exemplo de número de cartão MasterCard

7. Usando o GitHub Copilot

Durante o desenvolvimento, você pode utilizar o GitHub Copilot para gerar trechos de código com base no contexto e nas suas intenções. Basta começar a digitar uma função ou descrição, e o Copilot fornecerá sugestões para completar seu código.
