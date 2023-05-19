<h1>Projeto Blog Pessoal</h1>



<br />

<h2><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="4%"/>Criar a Classe Model - Tema</h2>





<div align="center"><img src="https://i.imgur.com/iAKfz6A.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/bTEtms5.png" title="source: imgur.com" /></div>



```typescript
export default interface Tema {
    id: number;
    descricao: string;
  }
```



<br />

<div align="left"><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="3%"/> <a href="https://www.typescriptlang.org/docs/handbook/typescript-tooling-in-5-minutes.html#interfaces" target="_blank"><b>TypeScript - Interface</b></a></div>

<div align="left"><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="3%"/> <a href="https://www.typescriptlang.org/docs/handbook/modules.html#default-exports" target="_blank"><b>TypeScript - Default Export</b></a></div>

<br />



<h2><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="4%"/>Atualizar a Classe de Serviço - Service</h2>





<div align="center"><img src="https://i.imgur.com/mrj7l7F.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/fzJ4GMI.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/okcSKmS.png" title="source: imgur.com" /></div>





```typescript
import axios from "axios"

export const api = axios.create({
    baseURL: 'https://blogpessoal.onrender.com/'
  })
  
  export const login = async(url: string, dados: Object, setDados: Function) => {
    const resposta = await api.post(url, dados)
    setDados(resposta.data)
  }

  export const cadastrarUsuario = async(url: string, dados: Object, setDados: Function) => {
    const resposta = await api.post(url, dados)
    setDados(resposta.data)
  }

  export const listar = async(url: string, setDados: Function, header: Object) => {
    const resposta = await api.get(url, header)
    setDados(resposta.data)
  }
```



<br />

<div align="left"><img src="https://i.imgur.com/A94hGdN.png" title="source: imgur.com" width="4%"/> <a href="https://www.npmjs.com/package/axios#axios-api" target="_blank"><b>Axios - Request e Response</b></a></div>

<br />

<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="5%"/>Atualizar o Componente ListarTemas</h2>





<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="5%"/>Atualizar o Componente CardTemas</h2>





<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="5%"/>Testar o Componente</h2>



<div align="center"><img src="https://i.imgur.com/00cFzd1.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/PirHRWR.png" title="source: imgur.com" /></div>

<br /><br />
	

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>