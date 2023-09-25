<h1>Projeto Blog Pessoal</h1>



<br />

<h2><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="4%"/>Criar a Classe Model - User</h2>





<div align="center"><img src="https://i.imgur.com/iAKfz6A.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/2887ShF.png" title="source: imgur.com" /></div>



```typescript
interface Usuario {
    id: number;
    nome: string;
    usuario: string;
    senha: string;
    foto: string;
}

export default Usuario;
```



<br />

<div align="left"><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="3%"/> <a href="https://www.typescriptlang.org/docs/handbook/typescript-tooling-in-5-minutes.html#interfaces" target="_blank"><b>TypeScript - Interface</b></a></div>

<div align="left"><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="3%"/> <a href="https://www.typescriptlang.org/docs/handbook/modules.html#default-exports" target="_blank"><b>TypeScript - Default Export</b></a></div>

<br />



<h2><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="4%"/>Atualizar a Classe de Serviço - Service</h2>





<div align="center"><img src="https://i.imgur.com/mrj7l7F.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/fzJ4GMI.png" title="source: imgur.com" /></div>





```typescript
import axios from "axios"

export const api = axios.create({
  baseURL: 'Endereço do Backend do Blog Pessoal'
})

export const login = async(url: string, dados: Object, setDados: Function) => {
  const resposta = await api.post(url, dados)
  setDados(resposta.data)
}

export const cadastrarUsuario = async(url: string, dados: Object, setDados: Function) => { 
  const resposta = await api.post(url,dados)
  setDados(resposta.data)
}
```



<br />

<div align="left"><img src="https://i.imgur.com/A94hGdN.png" title="source: imgur.com" width="4%"/> <a href="https://www.npmjs.com/package/axios#axios-api" target="_blank"><b>Axios - Request e Response</b></a></div>

<br />



<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="5%"/>Atualização do Componente Cadastrar Usuario</h2>



implementar código





<br />


<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> <a href="https://pt-br.react.dev/reference/react" target="_blank"><b>Documentação: Hooks</b></a></div>

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> <a href="https://pt-br.react.dev/reference/react/useState" target="_blank"><b>Documentação: Hook - useState</b></a></div>

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> <a href="https://pt-br.react.dev/reference/react/useEffect" target="_blank"><b>Documentação: Hook - useEffect</b></a></div>

<div align="left"><img src="https://i.imgur.com/ey5iP4N.png" title="source: imgur.com" width="4%"/> <a href="https://reactrouter.com/en/6.11.0/hooks/use-navigate" target="_blank"><b>Documentação do React Router - Hook - useNavigate</b></a></div>

<div align="left"><img src="https://i.imgur.com/ey5iP4N.png" title="source: imgur.com" width="4%"/> <a href="https://reactrouter.com/en/6.11.0/components/link" target="_blank"><b>Documentação do React Router - Link</b></a></div>

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> <a href="https://pt-br.react.dev/reference/react-dom/components#form-components" target="_blank"><b>Documentação: Forms</b></a></div>

<div align="left"><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="4%"/> <a href="https://pt-br.react.dev/reference/react-dom/components/input" target="_blank"><b>Documentação: Change Event</b></a></div>

<div align="left"><img src="https://i.imgur.com/r9lrbPG.png" title="source: imgur.com" width="30px"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/Spread_syntax" target="_blank"><b>Documentação: Spread Operator</b></a></div>

<div align="left"><img src="https://i.imgur.com/r9lrbPG.png" title="source: imgur.com" width="30px"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Statements/async_function" target="_blank"><b>Documentação: Funções Assíncronas</b></a></div>

<div align="left"><img src="https://i.imgur.com/r9lrbPG.png" title="source: imgur.com" width="30px"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Promise" target="_blank"><b>Documentação: Promise</b></a></div>

<div align="left"><img src="https://i.imgur.com/r9lrbPG.png" title="source: imgur.com" width="30px"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/AsyncFunction" target="_blank"><b>Documentação: Async</b></a></div>

<div align="left"><img src="https://i.imgur.com/r9lrbPG.png" title="source: imgur.com" width="30px"/> <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/await" target="_blank"><b>Documentação: Await</b></a></div>

<br />



<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="5%"/>Testar o Componente</h2>





<div align="center"><img src="https://i.imgur.com/jzV2eSF.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/EM1w9Gw.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/b8Kb25b.png" title="source: imgur.com" /></div>





<div align="center"><img src="https://i.imgur.com/kHQVE3D.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/Fw1Escn.png" title="source: imgur.com" /></div>





<div align="center"><img src="https://i.imgur.com/4jgwcIw.png" title="source: imgur.com" /></div>





<div align="center"><img src="https://i.imgur.com/Wo6aFrp.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/ll6LTOM.png" title="source: imgur.com" /></div>



<br />

<div align="left"><img src="https://i.imgur.com/wSOp8FA.png" title="source: imgur.com" width="4%"/> <a href="https://mui.com/material-ui/react-text-field/" target="_blank"><b>Documentação do MUI - React Text Field</b></a></div>

<div align="left"><img src="https://i.imgur.com/wSOp8FA.png" title="source: imgur.com" width="4%"/> <a href="https://mui.com/material-ui/react-button/" target="_blank"><b>Documentação do MUI - React Button</b></a></div>

<br />
