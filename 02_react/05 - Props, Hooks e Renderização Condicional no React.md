<h1>Projeto Blog Pessoal - Props, Hooks e Renderização Condicional no React</h1>

Antes de nos aprofundarmos nos nossos conhecimentos sobre React, é necessário sermos apresentados a 3 conceitos bastante importante dessa biblioteca, que são o uso de Propriedades em Componentes, as **Props**, as funções de Recursos, os **Hooks**, e por fim a **Renderização Condicional** de Componentes.

<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> 1. Props (Propriedades)</h2>

Em React, "props" é uma abreviação de "properties" (propriedades, em português), são um mecanismo de passagem de dados entre componentes.

Props são objetos que contêm dados que são passados de um componente pai para um componente filho. Esses dados podem ser passados como atributos HTML e, em seguida, acessados dentro do componente filho por meio de suas propriedades.

Para entendermos melhor as props, podemos fazer a seguinte analogia :

**IMAGEM** - Exemplo de parâmetro sendo passado para uma função

**IMAGEM** - Exemplo de Props

**Há várias vantagens em usar props em React, sendo algumas:**

1. **Comunicação entre componentes:** Através de props é possível passar dados de um componente pai para um componente filho, permitindo a comunicação entre esses componentes.
2. **Reutilização de componentes:** Usando props, um componente pode ser reutilizado em várias partes do aplicativo, pois pode ser configurado de maneira diferente em cada uso, dependendo dos dados que são passados para ele.
3. **Manutenção simplificada:** Com a passagem de dados usando props, a lógica de um componente pode ser mantida separada da lógica de outros componentes. Isso facilita a manutenção do código, já que cada componente pode ser modificado independentemente dos outros.
4. **Flexibilidade:** A passagem de dados usando props é uma das principais razões pelas quais o React é uma biblioteca tão flexível e escalável. É possível criar componentes genéricos que podem ser usados em diferentes partes do aplicativo, desde que os dados necessários sejam passados por meio de props.
5. **Legibilidade do código:** O uso de props pode tornar o código mais legível, pois os dados são passados explicitamente de um componente para outro, tornando o fluxo de dados mais fácil de entender.

<h3>👣 1.1 Criando Props no React usando TypeScript </h3>

Para usar props em React com TypeScript, é aconselhado definir o tipo de props que o componente espera receber. Para isso, podemos utilizar dois tipos de estruturas fornecidas pelo TypeScript, as **Interfaces** e os **Types**.

**Interfaces:** As interfaces no TypeScript definem a estrutura e os tipos de dados esperados que um objeto **deve** ter. As interfaces são usadas principalmente para definir a forma de objetos e classes, permitindo que você especifique quais propriedades e métodos um objeto deve ter, juntamente com seus tipos. Aqui está um exemplo simples de uma interface:

```typescript
interface Pessoa {
  nome: string;
  idade: number;
}

const pessoa: Pessoa = {
  nome: "João",
  idade: 30
};

```

**Types**, por outro lado, são uma forma mais genérica de definir tipos de dados personalizados. Eles não apenas podem ser usados para objetos, mas também para outros tipos de dados, como tipos de união, tipos literais e até mesmo tipos de funções. Aqui está um exemplo de um tipo:

```typescript
type Cores = "vermelho" | "verde" | "azul";

const cor: Cores = "vermelho";
```

Para nosso exemplo, optaremos pela estrutura **Interface**. Portanto siga os passos abaixo:

1. Na pasta **src**, clique com o botão direito do mouse e clique na opção **New Folder** (Nova Pasta).

<div align="center"><img src="https://i.imgur.com/UJl5dki.png" title="source: imgur.com" /></div>

2. O nome da pasta será **components**, como mostra a figura abaixo. Após digitar o nome da pasta, pressione a tecla **enter** do seu teclado para concluir.

IMAGEM PRINT 02

3. Na pasta **components**, clique com o botão direito do mouse e clique na opção **New Folder** (Nova Pasta).
4. O nome da pasta será **card** (letras minúsculas), como mostra a figura abaixo. Após digitar o nome da pasta, pressione a tecla **enter** do seu teclado para concluir.

IMAGEM PRINT 03

5. Clique com o botão direito do mouse sobre a pasta **home**, como mostra a figura abaixo, e clique na opção **New File** (Novo Arquivo).

<div align="center"><img src="https://i.imgur.com/9lEKo3x.png" title="source: imgur.com" /></div>



6. O nome do arquivo será **Card.tsx**, como mostra a figura abaixo. Após digitar o nome do arquivo, pressione a tecla **enter** do seu teclado para concluir.

IMAGEM PRINT 04

7. Agora basta adicionar o código como mostra a figura abaixo:

```react
interface CardProps{
    titulo: string
    descricao: string
}

function Card({ titulo, descricao }: CardProps) {
  return (
    <div style={{
        width: "500px",
        border: "5px solid crimson",
        margin: "0 0 1rem 0"
    }}>
        <h1>{ titulo }</h1>
        <p>{ descricao }</p>
    </div>
  )
}

export default Card
```

IMAGEM PRINT 05

**Vamos analisar o código:**

**Linhas 01 a 04:** Estamos definindo uma interface chamada `CardProps` que especifica o tipo de cada propriedade que `Card.tsx` espera receber. O tipo de `titulo` e `descricao` são definidos como `string`.

**Linha 06:** Após definir a estrutura das props, passamos suas propriedades para o componente usando uma sintaxe chamada **Desestruturação**. Onde, ao invés de termos que acessar aos propriedades como um objeto, podemos desestruturar seus atributos e acessar seus campos diretamente. 

**Exemplo (Não adicionar):**

```react
// Exemplo de Props sem Desestruturação
function Card(props: CardProps) {
  return (
        <h1>{ props.titulo }</h1>
        <p>{ props.descricao }</p>
    </div>
  )
}
```

**Vamos analisar o código:**

**Linhas 13 e 14:** Após desestruturar as propriedades desse componente, passamos elas para dentro do corpo do componente, para essas informações serem exibidas.

**Agora, vamos adicionar o componente Card.tsx no App.tsx e passar as respectivas informações de suas propriedades para serem exibidas.**

8. Abra o App.tsx e insira o código abaixo:

```react
import Card from "./components/card/Card"
import Home from "./pages/home/Home"

function App() {
    return (
        <>
            <Card />
            {/* <Home /> */}
        </>
    )
}

export default App
```

IMAGEM PRINT 06

**Vamos analisar o código:**

**Linha 01:** Fazemos a importação do Componente Card.tsx

**Linha 06 e 09:** Colocamos um Fragment para envolver os componentes Card e Home

**Linha 07:** Perceba que ao inserirmos o componente Card, o mesmo fica com um sublinhado em vermelho. Isso se dá pois o VsCode integrado ao Typescript, nos indica que para esse componente deve ser passado 2 propriedades, titulo e descricao, respectivamente.

**Linha 08:** Comentamos o componente Home, pois não o usaremos agora.

9. Agora, termine de adicione os seguintes códigos:

```react
import Card from "./components/card/Card"
import Home from "./pages/home/Home"

function App() {
    return (
        <>
            <Card titulo='React' descricao='Biblioteca JS' />
            <Card titulo='Spring' descricao='Framework Java' />
            {/* <Home /> */}
        </>
    )
}

export default App
```

IMAGEM PRINT 07

**Vamos analisar o código:**

**Linhas 07 e 08:** Aqui na primeira linha, inserimos as propriedades titulo e descricao passando valores de acordo com suas tipagens, no caso dos valores string. Na segunda linha, adicionamos mais um componente Card, mas agora com valores diferentes em sua propriedades, evidenciando duas das vantagens de utilizar **Props** no React, a questão de **Reutilização e Flexibilidade de Componentes**.

10. Agora vamos testar nossos códigos no Navegador. Se você parou o seu projeto, execute o comando abaixo:

```bash
yarn dev
```

11. Após inicializar o projeto, será exibido o endereço onde a aplicação está sendo executada, como mostra a figura abaixo:

<div align="center"><img src="https://i.imgur.com/8tSoYJp.png" title="source: imgur.com" /></div>

11. Pressione a tecla **o** do seu teclado para abrir o Projeto no Navegador
12. O seu Projeto React será aberto no Navegador e componente Home será exibido, como mostra a figura abaixo:

IMAGEM PRINT 08

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="35px"/> <a href="https://legacy.reactjs.org/docs/components-and-props.html" target="_blank"><b>Documentação Legada: Props</b></a></div>

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="35px"/> <a href="https://react.dev/learn/passing-props-to-a-component" target="_blank"><b>Documentação Oficial: Props</b></a></div>

<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/>2. Hooks</h2>

Em React, um Hook é uma função especial que permite que você use recursos do React, como estado, contexto, ciclo de vida do componente, entre outros recursos, em componentes funcionais. Os hooks foram introduzidos na versão 16.8 do React e são uma maneira de compartilhar lógica entre componentes sem a necessidade de herança de classes.

Existem vários hooks integrados ao React, como useState, useEffect, useContext, useRef, useMemo, useCallback, entre outros. Cada um desses hooks oferece um conjunto específico de recursos que podem ser usados em componentes funcionais.

Em resumo, os hooks são uma maneira poderosa de compartilhar lógica entre componentes em React, e eles permitem que você escreva componentes funcionais mais simples e reutilizáveis.

**Há várias vantagens em usar Hooks em React, sendo algumas:**

1. **Melhor reutilização de código:** os hooks permitem que você compartilhe lógica entre componentes funcionais, evitando a duplicação de código em vários lugares. 
2. **Mais legibilidade e simplicidade:** os hooks permitem que você escreva componentes funcionais mais simples e mais fáceis de entender, reduzindo a complexidade do código e tornando-o mais legível.
3. **Maior flexibilidade:** os hooks permitem que você adicione recursos do React, como estado, ciclo de vida do componente, contexto, entre outros recursos, a componentes funcionais, o que antes só era possível em componentes de classe.
4. **Fácil migração de código:** os hooks tornam mais fácil a migração de código de componentes de classe para componentes funcionais, pois você pode reutilizar a lógica que já existe nos seus componentes de classe usando hooks.
5. **Melhor desempenho:** os hooks são mais eficientes do que as soluções anteriores para compartilhar lógica em componentes, como HOCs (Higher-Order Components) e render props, pois eles evitam a criação de componentes adicionais no DOM e ajudam a evitar problemas de desempenho.

<h3>👣 2.1 Estrutura do hook useState em React</h3>

O **useState** é um hook do React que permite que componentes funcionais tenham estado, ou seja, possam armazenar e atualizar dados ao longo do tempo. A estrutura básica do useState é a seguinte:

```react
const [state, setState] = useState(initialState);
```

Onde:

- `state` é a variável que armazena o estado atual do componente;
- `setState` é uma função que permite atualizar o valor de `state`;
- `initialState` é o valor inicial de `state`.

Vamos criar um exemplo do Hook **useState**, para isso, sigo os passos abaixo:

1. Na pasta **components**, crie uma nova pasta chamada **contador**.
2. Em seguida, crie um arquivo dentro dessa pasta chamado de **Contador.tsx**. 
3. Dentro do arquivo, digite **rfce** para gerar a estrutura inicial do componente.
4. Seguindo esses passos, você deve ter uma estrutura idêntica a essa:

IMAGEM PRINT 09

5. Agora basta adicionar o código como mostra a figura abaixo:

```react
import { useState } from 'react'

function Contador() {
    const [valor, setValor] = useState(0);

    function somarMaisUm() {
        setValor(valor + 1);
    }

    return (
        <div>
            <p>O valor é: {valor}</p>
            <button onClick={somarMaisUm}>Adicionar +1</button>
        </div>
    )
}

export default Contador
```

IMAGEM PRINT 10

**Vamos analisar o código:**

**Linha 01:** Fazemos a importação do hook **useState** direto da biblioteca do React

**Linha 04:** Construímos a estrutura do hook, definindo a variável de estado com o nome de **valor** e sua função de atualização chamada **setValor** (por boas práticas e conversão da comunidade, a função de atualização sempre recebe o prefixo **set** e o nome da variável que ela atualiza). E o valor inicial para essa variável definimos para começar em 0 (zero).

**Linhas 06 a 08:** Adicionamos uma função chamada **somarMaisUm**, cujo objetivo será sempre atualizar o valor da variável de estado em + 1. Para isso, dentro de seu escopo, usamos a função **setValor**, passando dentro do seus parênteses o valor atual armazenado no estado, somando sempre com +1. 

**Linha 12:** Dentro do paragrafo, mostramos o valor atual armazenado no estado do componente (variável de estado)

**Linha 13:** Criamos um botão com a propriedade **onClick**. Sempre que ele for clicado, irá disparar a função **somarMaisUm**, executando a lógica vista.

6. Agora abra o App.tsx e insira o código abaixo:

```react
import Contador from "./components/contador/Contador"
import Home from "./pages/home/Home"

function App() {
    return (
        <>
            <Contador />
            {/* <Home /> */}
        </>
    )
}

export default App
```

IMAGEM PRINT 11

**Vamos analisar o código:**

**Linha 01:** Importamos o componente Contador.

**Linha 07:** Inserimos o componente Contador.

7. Agora vamos testar nossos códigos no Navegador. Se você parou o seu projeto, execute o comando abaixo

```bash
yarn dev
```

8. Após inicializar o projeto, será exibido o endereço onde a aplicação está sendo executada.
9. Pressione a tecla **o** do seu teclado para abrir o Projeto no Navegador
10. O seu projeto será aberto no Navegador e componente **Contador** será exibido, como mostra a figura abaixo:

IMAGEM PRINT 12

11. E ao clicar no botão, o valor da variável de estado é atualizado.

Imagem print 13

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *É importante notar que o useState deve ser usado apenas em componentes funcionais e deve ser chamado sempre no início do componente. Além disso, é possível usar o useState mais de uma vez em um mesmo componente para gerenciar diferentes estados.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="35px"/> <a href="https://legacy.reactjs.org/docs/hooks-state.html" target="_blank"><b>Documentação Legada: useState</b></a></div>

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="35px"/> <a href="https://react.dev/reference/react/useState" target="_blank"><b>Documentação Oficial: useState</b></a></div>

<h3>👣 2.2 Estrutura do hook useEffect em React</h3>

O **useEffect** é um dos hooks mais importantes do React. Ele permite que os componentes sejam atualizados em resposta a alterações em certas propriedades, variáveis ou eventos.

Com esse hook, você pode executar efeitos colaterais em seu componente. Isso inclui a busca de dados de um servidor, a atualização do título da página, a manipulação de eventos de formulário e muitas outras ações que não estão diretamente relacionadas à renderização do componente.

O **useEffect** é executado após cada renderização do componente e pode ser configurado para ser executado apenas uma vez (como em uma busca de dados inicial), ou para ser executado sempre que uma ou mais dependências mudam (como quando uma variável específica é atualizada).

A estrutura básica do useEffect é a seguinte:

```react
useEffect(função, [dependências])
```

Onde:

- `função` é uma função que será executada sempre que uma das variáveis de dependência sobre uma mudança em seu estado;
- `dependências` é um array que pode receber uma, duas ou nenhuma variável que funcionam como uma gatilho para que o useEffect execute a função definida;

Vamos criar um exemplo do Hook **useEffect**, para isso, sigo os passos abaixo:

1. Na pasta **components**, crie uma nova pasta chamada **task**.
2. Em seguida, crie um arquivo dentro dessa pasta chamado de **Task.tsx**. 
3. Dentro do arquivo, digite **rfce** para gerar a estrutura inicial do componente.
4. Seguindo esses passos, você deve ter uma estrutura idêntica a essa:
5. Seguindo esses passos, você deve ter uma estrutura idêntica a essa:

IMAGEM PRINT 14

6. Agora basta adicionar o código como mostra a figura abaixo:

```react
import { useState, useEffect } from 'react'

function Task() {
    const [isCompletado, setIsCompletado] = useState(false)
    const [tarefa, setTarefa] = useState('')

    useEffect(() => {
        if (isCompletado) {
            setTarefa('Parabéns! Você concluiu a tarefa!')
        }
    }, [isCompletado])

    return (
        <div>
            <h1>Tarefa</h1>
            <h3>{tarefa}</h3>
            <p>Conclua a tarefa</p>
            <button onClick={() => setIsCompletado(true)}>Concluir Tarefa</button>
        </div>
    )
}

export default Task
```

IMAGEM PRINT 15

**Vamos analisar o código:**

**Linha 01:** Fazemos a importação do hook **useState** e **useEffect** direto da biblioteca do React

**Linha 04 e 05:** Adicionamos duas variáveis de estado, a primeira com o nome de **isCompletado** e sua função de atualização chamada **setIsCompletado**, iniciada com o valor **false** e, a segunda com o nome **tarefa**, iniciada com um **string vazia** e sua função **setTarefa**.

**Linhas 07 a 11:** Adicionamos a estrutura  do hook **useEffect**. No primeiro parâmetro, criamos uma Arrow Fuction que no seu interior existe uma estrutura de decisão **IF**. Nessa estrutura, verificamos se a variável de estado **isCompletado** tem o valor verdadeiro (true). Se sim, usamos a função **setTarefa** para alterar o texto: " Parabéns! Você concluiu a tarefa! ".

**Linha 11:** Definimos como variável de dependência desse hook, a variável de estado **isCompletado**. Sempre que seu estado mudar, a função dentro do **useEffect** será disparada.

**Linha 16:** Dentro do h3, mostramos o valor atual armazenado na variável **tarefa**.

**Linha 18:** Criamos um botão com a propriedade **onClick**. Sempre que ele for clicado, irá disparar uma Arrow Function que tem por ação executar a função **setIsCompletado**, executando a lógica vista.

7. Agora abra o App.tsx e insira o código abaixo:

```react
import Task from "./components/task/Task"
import Home from "./pages/home/Home"

function App() {
    return (
        <>
            <Task />
            {/* <Home /> */}
        </>
    )
}

export default App
```

IMAGEM PRINT 16

**Vamos analisar o código:**

**Linha 01:** Importamos o componente Task.

**Linha 07:** Inserimos o componente Task.

8. Agora vamos testar nossos códigos no Navegador. Se você parou o seu projeto, execute o comando abaixo

```bash
yarn dev
```

9. Após inicializar o projeto, será exibido o endereço onde a aplicação está sendo executada.
10. Pressione a tecla **o** do seu teclado para abrir o Projeto no Navegador
11. O seu projeto será aberto no Navegador e componente **Task** será exibido, como mostra a figura abaixo:

IMAGEM PRINT 17

12. E ao clicar no botão, o valor da variável **isCompletado** é atualizado, disparando a função dentro do **useEffect** que atualiza o texto da outra variável de estado.

IMAGEM PRINT 18

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="35px"/> <a href="https://legacy.reactjs.org/docs/hooks-effect.html" target="_blank"><b>Documentação Legada: useEffect</b></a></div>

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="35px"/> <a href="https://react.dev/reference/react/useEffect" target="_blank"><b>Documentação Oficial: useEffect</b></a></div>

<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> 3. Renderização Condicional</h2>

A renderização condicional em React é uma técnica usada para renderizar diferentes elementos ou componentes com base em determinadas condições. Em outras palavras, é uma maneira de controlar quais elementos são exibidos na interface do usuário com base em alguma lógica definida pelo desenvolvedor.

A renderização condicional pode ser feita de várias maneiras em React, incluindo o uso de declarações **"if" ou "switch"** em conjunto com a lógica JavaScript ou **expressões ternárias** que avaliam uma condição e retornam um componente ou null.

Por exemplo, se quisermos mostrar uma mensagem diferente para usuários logados e não logados em nosso aplicativo React, podemos usar a renderização condicional para exibir o componente de login para usuários não logados e o componente de boas-vindas para usuários logados. Podemos usar uma declaração "if" ou expressão ternária para verificar se o usuário está logado e, em seguida, renderizar o componente apropriado com base nessa condição.

A estrutura básica da **expressão ternária** é a seguinte:

```react
{ condição ? expressão1 : expressão2 }
```

Onde:

- `condição`: Uma expressão que é avaliada como `true` ou `false`;
- `expressão1 e expressão2`: São expressões com valores de qualquer tipo e/ou lógica a ser executada. Em nosso caso, será usada para mostrar determinado tipo de componente;

Vamos criar um exemplo de **Renderização Condicional**. Para isso, sigo os passos abaixo:

1. Na pasta **pages**, abra o componente **Home**.
2. Agora basta adicionar o código como mostra a figura abaixo:

```react
import { useState } from "react"

function Home() {
    const [isLogged, setIsLogged] = useState(false)

    return (
        <>
            {
                isLogged ? (
                    <div style={{
                        width: "100vw",
                        display: "flex",
                        justifyContent: "center"
                    }}>
                        <div>
                            <div style={{
                                 width: "80vw",
                                 display: "flex",
                                 flexDirection: "column",
                                 alignItems: "center"
                            }}>
                                <h2>Seja Bem Vinde!</h2>
                                <p>Expresse aqui seus pensamentos e opniões</p>
                            </div>
        
                            <div style={{
                                 width: "80vw",
                                 display: "flex",
                                 flexDirection: "column",
                                 alignItems: "center"
                            }}>
                                <img 
                                    src="https://i.imgur.com/VpwApCU.png" 
                                    alt="Imagem da Página Home" 
                                    width="400px"
                                />
                            </div>
                        </div>
                    </div>
                ) : (

                    <button onClick={() => setIsLogged(true)}>Entrar</button>

                )
            }
        </>
    )
}

export default Home
```

IMAGEM PRINT 19

**Vamos analisar o código:**

**Linha 01:** Fazemos a importação do hook **useState** direto da biblioteca do React

**Linha 04:** Adicionamos uma variáveis de estado com o nome de **isLogged** e sua função de atualização chamada **setIsLogged**, iniciada com o valor **false**.

**Linhas 09 e 46:** Inserimos as **chaves ( { } )** indicando que vamos adicionar um código de **Javascript/Typescript** dentro do retorno do componente. Isso só é possível graças a extensão .**jsx/.tsx** dos componentes do React.

**Linha 10:** Adicionamos a variável **isLogged**. Seu proposito aqui é ser nosso expressão condicional, podendo ter o valor verdadeiro ou falso. O **Ponto de Interrogação ( ? )** funciona como um separador entre a condição e a primeira expressão. Como estamos retornando mais de uma linha de código, envolvemos o HTML/CSS do componente em **parênteses ( )**.  

**Linhas 11 a 40:** Código do nosso componente.

**Linha 41:** Os **dois pontos ( : )** são os separadores entre a primeira expressão (que é executada quando a condição é verdadeira) e a segunda expressão (executada quando a condicional é falsa).

Definimos como variável de dependência desse hook, a variável de estado **isCompletado**. Sempre que seu estado mudar, a função dentro do **useEffect** será disparada.

**Linha 43:** Dentro dos parênteses da segunda expressão, adicionamos um botão com a propriedade **onClick**. Sempre que ele for clicado, irá disparar uma Arrow Function que tem por ação executar a função **setIsLogged**, mudando o valor da variável **isLogged** para **true (verdadeiro).**

3. Agora abra o App.tsx e insira o código abaixo:

```react
import Home from "./pages/home/Home"

function App() {
    return (
        <>
            <Home />
        </>
    )
}

export default App
```

4. Agora vamos testar nossos códigos no Navegador. Se você parou o seu projeto, execute o comando abaixo

```bash
yarn dev
```

5. Após inicializar o projeto, será exibido o endereço onde a aplicação está sendo executada.
6. Pressione a tecla **o** do seu teclado para abrir o Projeto no Navegador
7. O seu projeto será aberto no Navegador e componente **Home** será exibido, como mostra a figura abaixo:

IMAGEM PRINT 20

12. E ao clicar no botão, o valor da variável **isLogged** é atualizado para true (verdadeiro). Com isso, nossa condição ternária verificar que agora a condição está retornando verdadeiro e então mostra os códigos que tínhamos feito anteriormente.

IMAGEM PRINT 21

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="35px"/> <a href="https://pt-br.legacy.reactjs.org/docs/conditional-rendering.html" target="_blank"><b>Documentação Legada: Renderização Condicional</b></a></div>

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="35px"/> <a href="https://react.dev/learn/conditional-rendering" target="_blank"><b>Documentação Oficial: Renderização Condicional</b></a></div>

<br /><br />

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
