<h1>Projeto Blog Pessoal - Criar o Componente Login</h1>

Vamos criar o Componente **Login**, que será a primeira página que os usuários irão ver ao acessar nosso Blog.

<br />

<h2>👣 Passo 01 - Criar o Componente Login</h2>

Vamos criar a pasta **login**, dentro da pasta **pages**:

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="80px"/> | <div align="left"> **ATENÇÃO:** *O nome da pasta deve ser o mesmo nome do nosso componente. Sempre que você for criar um componente, o nome da pasta onde o componente será criado deve ser o mesmo nome do componente escrito com letras minúsculas.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

1. Na pasta **pages**, clique com o botão direito do mouse e clique na opção **New Folder** (Nova Pasta).

2. O nome da pasta será **login** (letras minúsculas), como mostra a figura abaixo. Após digitar o nome da pasta, pressione a tecla **enter** do seu teclado para concluir.

   Na sequência, vamos criar o arquivo **Login.tsx**, dentro da pasta **login**:

<br />

| <img src="https://i.imgur.com/hOgWvSc.png" title="source: imgur.com" width="100px"/> | <div align="left"> **ATENÇÃO:** *Sempre que você for criar um arquivo tsx, o nome do arquivo deve ser escrito com a primeira letra maiúscula e as demais em letra minúsculas. Caso o nome do componente seja composto (ListaPostagem.tsx), cada palavra deve ser iniciada com a primeira letra maiúscula, sem espaços ou qualquer outro caractere especial entre as palavras.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

| <img src="https://i.imgur.com/vVDBDG0.png" title="source: imgur.com" width="100px"/> | <div align="left"> **ALERTA DE BSM:** *Mantenha a Atenção aos Detalhes ao criar o arquivo tsx do componente. Um erro muito comum é criar o arquivo fora da pasta do componente.* </div> |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

<br />

3. Clique com o botão direito do mouse sobre a pasta **login**, que foi criada dentro da pasta **pages**, como mostra a figura abaixo, e clique na opção **New File** (Novo Arquivo).
4. O nome do arquivo será **Login.tsx**, como mostra a figura abaixo. Após digitar o nome do arquivo, pressione a tecla **enter** do seu teclado para concluir.

Agora vamos criar o código do Componente **Home**, como mostra a figura abaixo:

![](https://i.imgur.com/gidu7L0.png)

Vamos analisar o código:

**Linhas 01:** Faz a importação do Arquivo **Login.css** para dentro do Componente **Login**.

**Linhas 03:** Cria a Função **Login**, que retornará o componente **Login**. Lembre-se que um Componente React nada mais é do que uma Function JavaScript/TypeScript, que retorna código HTML e CSS.

**Linhas 06 e 45:** Foi inserido o fragment na linha 6 e o mesmo foi finalizado na linha 45. Como estamos inserindo mais de uma tag HTML, todo o código precisa estar envolvido pelo **fragment (`<> </>`)**, que é um recurso do React, que permite agrupar uma lista de elementos filhos (Tags HTML) sem adicionar nós extras ao DOM. Essa estratégia torna a renderização dos Componentes em tela mais rápida e eficiente.

**Linha 07:** Inserimos uma div com o **Display Grid**, já que essa configuração é a mais adequada para a criação de componentes grandes.

**Linhas 08 e 42:** Foi adicionado a tag **form** dentro da div. A tag form indica que estamos adicionando um formulário de preenchimento dentro da nossa página.

**Linhas 10 a 20 e 21 a 31:** Adicionarmos tags divs com o **display Flex** para organizarmos os campos de preenchimento do formulário.

**Linhas 11 e 22:** As tags labels servem como indicativos dos campos a serem preenchidos dentro de um formulário, para indicar a usuário que tipo de informação ela deve inserir em cada um dos campos.

**Linhas 12 e 23:** Foram inseridas as tags input logo abaixo das labels e dentro do formulário. Os inputs são nada mais do que os campos que serão preenchidos pela usuário de acordo com o tipo de informação informada nas labels e nas propriedades do próprio input.

**Linhas 13 a 17 e Linhas 24 a 28:** A propriedade **type** representa o tipo de informação que será inserida no input; **id** será usado para se referenciar a propriedade **htmlFor** do label e posteriormente a lógica do componente; **name** assim como o id será usado futuramente para implementarmos a lógica de login; **placeholder** é um texto guia, usado para auxiliar a usuário saber o formato da informação a digitada; **className** como visto antes será usado para aplicarmos estilos do Tailwind nesses elementos.

**Linhas 32 a 34:** A tag **button** é adicionada abaixo das divs dos campos para futuramente podermos submeter (enviar) os dados inseridos pelo usuário.

**Linha 36:** Essa tag serve para criar uma linha separadora. Aqui usamos apenas para criar uma divisão entre a parte de campos e o informativo para criar uma conta.

**Linha 43:** Nossa tela está sendo dividida em grids graças aos display que colocamos para construir a página, onde o formulário ocupa a parte da esquerda. Portanto, essa div é inserida abaixo/depois da tag form para ocupar a parte da direita da nossa tela. Nela passamos três configurações, sendo que as duas últimos são estilos do próprio Tailwind e a primeira é uma classe criada no arquivo Login.css que iremos construir.

<h2><img src="https://i.imgur.com/7IdCTXz.png" title="source: imgur.com" width="4%"/> Passo 02 - Criar o Arquivo Home.css</h2>

Vamos criar o arquivo de estilo desse componente e adicionar seus códigos. 

1. Clique com o botão direito do mouse sobre a pasta **login**, e clique na opção **New File** (Novo Arquivo).
2. O nome do arquivo será **Login.css**. Após digitar o nome do arquivo, pressione a tecla **enter** do seu teclado para concluir.
3. Em seguida, adicione os códigos abaixo:

```css
.fundoLogin {
    background-image: url("https://i.imgur.com/ZZFAmzo.jpg");
    background-repeat: no-repeat;
    min-height: 100vh;
    width: 100%;
    background-size: cover;
    background-position: center;
}
```

<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> Passo 03 - Atualizar o Componente App</h2>

Vamos atualizar o Componente **App** de modo a exibir o componente **Login**:

1. Abra o arquivo **App.tsx**, localizado na pasta **src**:
   <div align="center"><img src="https://i.imgur.com/Lb2kef6.png" title="source: imgur.com" /></div>

2. Insira o seguinte código no arquivo:

```tsx
import { BrowserRouter, Routes, Route } from 'react-router-dom'

import Footer from './components/Footer/Footer'
import Navbar from './components/Navbar/Navbar'
import Login from './pages/Login/Login'
import Home from './pages/Home/Home'

function App() {
    return (
        <>
            <BrowserRouter>
                <Navbar />
                <div className='min-h-[80vh]'>
                    <Routes>
                    	<Route path="/" element={<Login />} />
                        <Route path="/login" element={<Login />} />
                        <Route path="/home" element={<Home />} />
                    </Routes>
                </div>
                <Footer />
            </BrowserRouter>
        </>
    )
}

export default App

```

Vamos analisar as alterações efetuadas no código:

**IMAGEM**

**Linha 18:** Na primeira rota da aplicação, a que aponta para o endereço raiz da aplicação, definimos agora que o primeiro componente a ser renderizado será o Login.

**Linha 19:** Logo abaixo, criamos uma rota exclusiva para o componente Login, apontando para o endereço **/login**.

**Linha 20:** Criamos a terceira rota, apontando para o endereço **/home**, apontando para o Componente **Home**.

<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="5%"/>Passo 04 -Testar os Componentes</h2>

Chegou o momento de testarmos nossas modificações!

1. Para executar o Projeto no Navegador, digite o comando abaixo:

   ```bash
   npm dev
   ```

2. Após inicializar o projeto, será exibido o endereço onde a aplicação está sendo executada
3. Pressione a tecla **o** do seu teclado para abrir o Projeto no Navegador
4. O seu Projeto React será aberto no Navegador e o primeiro componente agora a ser exibido é o Login.