<h1>Projeto Blog Pessoal</h1>



<br />

<h2><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="4%"/>Criar a Classe Model - Postagem</h2>





<div align="center"><img src="https://i.imgur.com/iAKfz6A.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/bTEtms5.png" title="source: imgur.com" /></div>



```typescript
import Tema from './Tema';
import Usuario from './Usuario';

export default interface Postagem {
  id: number;
  titulo: string;
  texto: string;
  data: string;
  tema: Tema | null;
  usuario: Usuario | null;
}

```



<br />

<div align="left"><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="3%"/> <a href="https://www.typescriptlang.org/docs/handbook/typescript-tooling-in-5-minutes.html#interfaces" target="_blank"><b>TypeScript - Interface</b></a></div>

<div align="left"><img src="https://i.imgur.com/izFuHID.png" title="source: imgur.com" width="3%"/> <a href="https://www.typescriptlang.org/docs/handbook/modules.html#default-exports" target="_blank"><b>TypeScript - Default Export</b></a></div>

<br />



<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="5%"/>Atualizar o Componente ListarPostagens</h2>





<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="5%"/>Atualizar o Componente CardPostagens</h2>







<h2><img src="https://i.imgur.com/H9wEgsJ.png" title="source: imgur.com" width="5%"/>Testar o Componente</h2>



<div align="center"><img src="https://i.imgur.com/00cFzd1.png" title="source: imgur.com" /></div>



<div align="center"><img src="https://i.imgur.com/PirHRWR.png" title="source: imgur.com" /></div>

<br /><br />
	

<div align="left"><a href="README.md"><img src="https://i.imgur.com/XMgF3gl.png" title="source: imgur.com" width="3%"/>Voltar</a></div>