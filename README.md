# iZap Teste Front-end

Antes de começar, leia a nossa [página sobre cultura](https://izap.com.br/quem-somos.html) para entender um pouco sobre o que nós priorizamos no desenvolvimento e **faça o seu melhor, pois iremos avaliar o teste como se fosse seu melhor esforço** ;)

Envie o resultado do seu desafio para marcos.azevedo@izap.com.br (ele pode ser open source!).
Se possível, faça deploy da sua aplicação em algum serviço como [Netlify](https://www.netlify.com/), [Heroku](https://heroku.com/) ou qualquer outro de sua preferência.

## Objetivo

O objetivo do desafio é validar seus conhecimentos nos seguintes tópicos:

- **JavaScript**: aproveite o desafio para mostrar tudo o que sabe sobre as novas features da linguagem.
- **React**: siga boas práticas e mantenha o código idiomático. Busque utilizar features recentes e se mantenha atento a problemas comuns como re-renders desnecessários.
- **TypeScript**: Opcional. Caso opte por usá-lo, mostre todo o seu domínio.
- **Componentização**
- **CSS**: seja optando por vanilla, pré-processadores ou CSS-in-JS.
- **Testes unitários**
- **Testes end-to-end**

Analisaremos seu teste com base nos critérios acima.

## Restrições

1.  **Não é permitido** utilizar frameworks e/ou bibliotecas de UI que não seja o React (como Vue.js ou Angular).
2.  **São permitidas** ferramentas modernas de desenvolvimento como TypeScript, Babel, eslint, webpack, assim como o uso de polyfills (e outras ferramentas para melhorar o suporte a browsers, como Modernizr) e/ou bibliotecas para testes.
3.  **São permitidos** pré-processadores de CSS e/ou ferramentas CSS-in-JS.
4.  Não é uma regra, mas evite usar lodash, underscore, ramda e similares.

## Como Avaliaremos seu Teste Técnico

Sua performance será avaliada com base nos seguintes pontos:

1. A aplicação funciona conforme o esperado.
2. Os problemas foram resolvidos com eficiência.
3. A aplicação é fornecida com comandos de instalação e execução para ambientes de desenvolvimento e de testes.
4. Você demonstra conhecimento de como testar as partes críticas da aplicação. Não exigimos 100% de cobertura.
5. A aplicação tem uma estrutura lógica e bem organizada.
6. O teste acompanha documentação com o raciocínio sobre as decisões tomadas.
7. O código está documentado e/ou é de fácil leitura.
8. Segue algum guia de estilo de código padronizado.
9. Possui um histórico do git (mesmo que breve) com mensagens claras e concisas.

## O Teste

Hoje nossos clientes precisam saber quanto custa antecipar uma transação, e para isso, precisamos desenvolver uma calculadora de antecipação para que os mesmos consigam saber quais valores receberão caso optem por antecipar o recebimento.

Você deverá desenvolver o teste seguindo os requisitos abaixo.

## Requisitos

- Use componentização.
- Os períodos de recebimento devem ser configuráveis já que a API pode receber uma lista de períodos para realizar os cálculos.
- Faça testes unitários e/ou de ponta-a-ponta (end-to-end)

Os possíveis cenários devem ser cobertos e terem soluções implementadas. Não foi desenvolvido layout para isso, pois queremos observar como você lidará com eles:

- Demora de respostas da API
- Timeout da API
- Conexão lenta
- Usuário estar offline

## Front

O layout proposto para essa calculadora pode ser visto no link abaixo.

[Link para o layout](https://www.figma.com/proto/416G79R57F4som5jvuZgxo/simule-sua-antecipa%C3%A7%C3%A3o?scaling=scale-down-width&node-id=101%3A215&hide-ui=1) - **Lembrando que a sua aplicação deve seguir o layout pixel by pixel**

## API

Você consumirá uma API já existente no endereço abaixo. Em seguida há uma especificação simplificada dela.

`https://izap-frontend-challenges.herokuapp.com`

### Post

| Parâmetro      | Obrigatório? | Tipo            | Descrição                                                   |
| -------------- | ------------ | --------------- | ----------------------------------------------------------  |
| `amount`       | Sim          | `number`        | Valor total da transação em centavos                        |
| `installments` | Sim          | `number`        | Número de débito                                            |

### Exemplo

```bash
$ curl --request POST \
  --url https://izap-frontend-challenges.herokuapp.com \
  --header 'content-type: application/json' \
  --data '{
	"amount": 1000,
	"installments": 3
}'

{"1":941,"15":950,"30":960,"90":980}
```

### Simulando Timeout e Internal Server Error de resposta

Para **Timeout** basta executar a request post passando `timeout` através da query string, exemplo:
`https://izap-frontend-challenges.herokuapp.com?timeout`

Para **Internal Server Error** basta executar a request post passando `internalError` através da query string, exemplo:
`https://izap-frontend-challenges.herokuapp.com?internalError`

