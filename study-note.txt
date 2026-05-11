React -> component -> follow logic and appeareance

function MyButton() {
return (
<button>Eu sou um botão</button>
);
}

export default function MyApp() {
return (

<div>
<h1>Bem-vindo ao meu aplicativo</h1>
<MyButton /> /* React component names should always begin with a capital letter. */
</div>
);
}

JSX -> all tags need to be closed - and involved on a parent tag

className -> to add css

## Displaying data:

const user = {
name: 'Hedy Lamarr',
imageUrl: 'https://i.imgur.com/yXOvdOSs.jpg',
imageSize: 90,
};

export default function Profile() {
return (
<>

<h1>{user.name}</h1>
<img
className="avatar"
src={user.imageUrl}
alt={'Foto de ' + user.name}
style={{
          width: user.imageSize,
          height: user.imageSize
        }}
/>
</>
);
}

## Render condictional:

let content;
if (isLoggedIn) {
content = <AdminPanel />;
} else {
content = <LoginForm />;
}
return (

  <div>
    {content}
  </div>
);

## Render list:

const products = [
{ title: 'Repolho', isFruit: false, id: 1 },
{ title: 'Alho', isFruit: false, id: 2 },
{ title: 'Maçã', isFruit: true, id: 3 },
];

export default function ShoppingList() {
const listItems = products.map(product =>

<li
key={product.id}
style={{
        color: product.isFruit ? 'magenta' : 'darkgreen'
      }} >
{product.title}
</li>

## Events:

function MyButton() {
function handleClick() {
alert('Você clicou no botão!');
}

return (
<button onClick={handleClick}>
Clique aqui
</button>
);
}

## Update the screen

import { useState } from 'react';

export default function MyApp() {
return (
<div>
<h1>Contadores que atualiza separadamente</h1>
<MyButton />
<MyButton />
</div>
);
}

function MyButton() {
const [count, setCount] = useState(0);

function handleClick() {
setCount(count + 1);
}

return (
<button onClick={handleClick}>
Clicado {count} vezes
</button>
);
}

## Sharing same states

import { useState } from 'react';

export default function MyApp() {
const [count, setCount] = useState(0);

function handleClick() {
setCount(count + 1);
}

return (
<div>
<h1>Contadores que são atualizados juntos</h1>
<MyButton count={count} onClick={handleClick} />
<MyButton count={count} onClick={handleClick} />
</div>
);
}

function MyButton({ count, onClick }) {
return (
<button onClick={onClick}>
Clicado {count} vezes
</button>
);
}
