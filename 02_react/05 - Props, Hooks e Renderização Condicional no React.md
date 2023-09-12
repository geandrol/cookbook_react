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

<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/>2. Hooks</h2>



<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> Renderização Condicional</h2>





<h2>👣 Passo 01 - Instalação do Tailwind</h2>



1. Para instalar o Tailwind, digite o comando abaixo:

```bash
npm install -D tailwindcss postcss autoprefixer
```

2. Após a instalação, será exibida uma mensagem semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/c1tt7b9.png" title="source: imgur.com" /></div>

3. O comando acima instalará os seguintes pacotes no seu projeto:

- O Core do Tailwind, ou seja, o pacote principal do Tailwind;
- O pacote Post CSS, que fornece plug-ins para executar diversas funcionalidades dp Tailwind;
- Autoprefixer, que é um plug-in para analisar o código CSS e adicionar os prefixos às regras CSS.

4. Para confirmar se a instalação dos pacotes deu certo, utilize o comando abaixo:

```bash
npm list
```

5. Será exibida a lista de pacotes instalados. Verifique se os pacotes indicados na imagem abaixo estão instalados:

<div align="center"><img src="https://i.imgur.com/w9OODtB.png" title="source: imgur.com" /></div>

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *As versões dos pacotes instalados no seu projeto podem ser diferentes das versões listadas na imagem acima. O mais importante são os pacotes estarem instalados.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

6. Na sequência, vamos gerar os arquivos de configuração do Tailwind, através do comando abaixo:

```bash
npx tailwindcss init -p
```

7. Após a geração dos arquivos de configuração do Tailwind, será exibida uma mensagem semelhante a imagem abaixo, informando que os arquivos foram gerados:

<div align="center"><img src="https://i.imgur.com/URGak9e.png" title="source: imgur.com" /></div>

8. A pasta do seu projeto no **VSCode**, deve ficar semelhante a imagem abaixo:

   <div align="center"><img src="https://i.imgur.com/su4n4uE.png" title="source: imgur.com" /></div>

9. O comando acima gerou dois novos arquivos: **tailwind.config.js** e **postcss.config.js**, que são os arquivos de configuração do Tailwind. Estes arquivos ajudam você a interagir com seu projeto e personalizar tudo.

Como o Tailwind é uma estrutura para criar interfaces de usuário sob medida, ele foi projetado desde o início com a personalização em mente. Por padrão, o Tailwind sempre procurará o arquivo **tailwind.config.js** na raiz do seu projeto onde você pode definir quaisquer personalizações, que fujam do padrão do Tailwind. Cada seção do arquivo de configuração é opcional, portanto, você só precisa especificar o que deseja alterar. 

Ao gerar o arquivo **tailwind.config.js** ele terá o seguinte conteúdo:

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: [],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

Como estamos usando o Tailwind como um plug-in PostCSS (instalamos a dependência postcss), será gerado o arquivo de configuração **postcss.config.js**, onde podemos especificar o caminho de configuração personalizado do PostCSS. 

Ao gerar o arquivo **postcss.config.js** ele terá o seguinte conteúdo:

```javascript
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

No React, por recomendação da própria Documentação Oficial do Tailwind, ao invés de especificar o caminho neste arquivo, iremos especificar o caminho de configuração usando a diretiva `@config` no arquivo **index.css** (Folha de Estilos principal do React).

<br />

<div align="left"><img src="https://i.imgur.com/FkcNWAL.png" title="source: imgur.com" width="4%"/> <a href="https://tailwindcss.com/docs/installation" target="_blank"><b>Instalação do Tailwind</b></a></div>

<div align="left"><img src="https://i.imgur.com/FkcNWAL.png" title="source: imgur.com" width="4%"/> <a href="https://tailwindcss.com/docs/configuration" target="_blank"><b>Configuração do Tailwind</b></a></div>

<br />

<h2>👣 Passo 02 - Configurando o Tailwind</h2>



Vamos adicionar o caminho da pasta onde estarão os nossos Componentes e os tipos de arquivos que serão estilizados através do Tailwind, dentro do arquivo **tailwind.config.cjs**. Os tipos de arquivos estilizados incluem o HTML, componentes JavaScript, Componentes TypeScript e entre outros. 

1. Abra o arquivo **tailwind.config.js**, localizado na pasta raíz do seu projeto:

<div align="center"><img src="https://i.imgur.com/z4Fz75t.png" title="source: imgur.com" /></div>

2. O arquivo **tailwind.config.js** do seu projeto, deve estar semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/xvNkfUU.png" title="source: imgur.com" /></div>

3. Vamos atualizar o conteúdo arquivo, adicionando as linhas abaixo, no array **content**.

```javascript
"./index.html",
"./src/**/*.{js,ts,jsx,tsx}",
```

4. Após adicionar as linhas acima, o conteúdo do arquivo estará semelhante a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/zfZWCza.png" title="source: imgur.com" /></div>

<br />

<h2>👣 Passo 03 - Adicionar as Diretivas do Tailwind no index.css</h2>



As Diretivas do Tailwind são instruções personalizadas, específicas do Tailwind, que instruem o CSS sobre como se comportar. Você precisará adicionar diretivas para as três camadas do Tailwind:

- **@tailwind base:** Injeta os estilos base do Tailwind e os estilos base registrados pelos plug-ins;
- **@tailwind components:** Injeta as classes de componentes do Tailwind e as classes de componentes registradas pelos plug-ins;
- **@tailwind utilities:** Injeta as classes de utilitários do Tailwind e as classes de utilitários registradas pelos plug-ins.

1. Abra o arquivo **index.css**, localizado na pasta **src** do seu projeto:

<div align="center"><img src="https://i.imgur.com/VE3JEMV.png" title="source: imgur.com" /></div>

2. Se ainda tiver algum conteúdo dentro do arquivo **index.css**, apague todo o conteúdo do arquivo
3. Adicione as declarações abaixo no arquivo **index.css**

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

4. Após adicionar estas linhas, o seu arquivo **index.css**, ficará igual a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/mT24r37.png" title="source: imgur.com" /></div>

Agora estamos prontos para utilizar o Tailwind!

<br />

<div align="left"><img src="https://i.imgur.com/FkcNWAL.png" title="source: imgur.com" width="4%"/> <a href="https://tailwindcss.com/docs/installation" target="_blank"><b>Instalação do Tailwind</b></a></div>

<div align="left"><img src="https://i.imgur.com/FkcNWAL.png" title="source: imgur.com" width="4%"/> <a href="https://tailwindcss.com/docs/configuration" target="_blank"><b>Configuração do Tailwind</b></a></div>

<br />

<hr>

<br />

<h2>⚠ Warning: Unknown at rule @tailwindcss (unknownAtRules)</h2> 

 Ao inserir as linhas acima no arquivo **index.css**, o VSCode pode emitir um Warning (Aviso), que ele não reconheceu as propriedades do CSS. Esse alerta é emitido pelo **Lint** (ferramenta de análise de código) do CSS, caso ele esteja instalado no seu VSCode. Para desabilitar este alerta, siga os passos abaixo:

 1. Abra as **Configurações do VSCode** através do menu **File 🡪 Preferences 🡪 Settings** (Arquivo 🡪 Preferências 🡪 Configurações)

<div align="center"><img src="https://i.imgur.com/HHV5tH8.png" title="source: imgur.com" /></div>

2. Será aberta janela do **Settings** (Configurações)

<div align="center"><img src="https://i.imgur.com/FAIEW4J.png" title="source: imgur.com" /></div>

 3. No item **Search Settings** (Procurar Configurações), digite: **Unknown At Rules** e altere esta configuração para **ignore**, conforme indicado na imagem abaixo:

<div align="center"><img src="https://i.imgur.com/fEvFAYG.png" title="source: imgur.com" /></div>

4. A mensagem de alerta não será mais exibida.

<br /><br />
	

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>
