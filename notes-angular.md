# Angular

` npm install --save --legacy-peer-deps  `<br>
` npm start  `<br>
` ng test "--test-name-pattern=^RedeOcorrenciaAreaAfetadaTableComponent"  `<br>
` npm run build  `<br>
` npm run lint  `<br>

[(minha_variavel)]="nome":

Isso representa a vinculação de dados bidirecional em Angular. É uma combinação de [minha_variavel] e (minha_variavel). Isso significa que qualquer alteração feita no componente será refletida no template e vice-versa.
```
<meu-input [(ngModel)]="valueFilter" [(minha_variavel)]="nome"></meu-input>
```

(minha_variavel)="nome":

Isso representa a vinculação de eventos em Angular. Quando ocorre um evento especificado (por exemplo, clique de botão), a expressão minha_variavel no template HTML é avaliada no contexto do componente e a função associada é chamada.
```
<meu-input [(ngModel)]="valueFilter" (minha_variavel)="nome"></meu-input>
```
[minha_variavel]="nome":

Isso representa a vinculação de atributos em Angular. É usado para passar valores do componente para o template HTML. O valor de nome no componente é atribuído ao atributo minha_variavel no elemento <meu-input>.
```
<meu-input [(ngModel)]="valueFilter" [minha_variavel]="nome"></meu-input>
```
### Publicar em prod
```
ng build --configuration=production
```
Copiar pasta dist para o dominio
