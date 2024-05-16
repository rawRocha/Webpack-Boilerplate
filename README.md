# Webpack-Boilerplate
 Boilerplate, no contexto de desenvolvimento de software, refere-se a um código padrão, genérico e reutilizável que pode ser aplicado em várias 
 situações sem muita modificação. Essencialmente, é um conjunto de código que é utilizado repetidamente em diferentes projetos para realizar 
 tarefas comuns ou estabelecer estruturas básicas. Em resumo, o boilerplate ajuda os desenvolvedores a economizar tempo e esforço ao fornecer um 
 ponto de partida consistente para seus projetos.

# Instalando Dev-dependences
No terminal:

    1. npm init -y

npm init -y é um comando usado no Node.js para inicializar um novo projeto npm rapidamente, sem a necessidade de responder a uma série de 
perguntas interativas. Quando você executa esse comando, ele cria um arquivo package.json no diretório atual com valores padrão para as 
configurações do projeto, como nome, versão, descrição, autor, licença, etc. O parâmetro -y é uma abreviação de --yes, que indica ao npm para 
aceitar automaticamente todas as configurações padrão, sem solicitar nenhuma entrada do usuário. Isso é útil quando você quer configurar 
rapidamente um novo projeto e não precisa especificar detalhes personalizados de imediato. 

    2. npm i --save-dev @babel/core @babel/cli @babel/preset-env babel-loader webpack webpack-cli core-js@2 regenerator-runtime

Esse comando npm i --save-dev @babel/core @babel/cli @babel/preset-env babel-loader webpack webpack-cli core-js@2 regenerator-runtime instala várias dependências do Babel, Webpack e outras ferramentas úteis para configurar e transpilar seu código JavaScript para versões compatíveis com navegadores mais antigos.

Vamos dar uma olhada no que cada uma dessas dependências faz:

1. @babel/core, @babel/cli, @babel/preset-env: São pacotes do Babel, uma ferramenta de transpilação JavaScript. @babel/core é o núcleo do Babel, @babel/cli fornece uma interface de linha de comando para o Babel, e @babel/preset-env é um conjunto de plugins que permite transpilar seu código para a versão do ECMAScript que os navegadores alvo suportam.

2. babel-loader: Um loader para o Webpack que permite transpilar arquivos JavaScript usando o Babel durante o processo de construção.
webpack, webpack-cli: São pacotes do Webpack, uma ferramenta de construção de módulos para JavaScript. webpack é o próprio Webpack e webpack-cli fornece uma interface de linha de comando para o Webpack.

3. core-js@2: Uma biblioteca que fornece polyfills para recursos JavaScript modernos em navegadores mais antigos.

4. regenerator-runtime: Uma dependência do Babel que é usada para habilitar o suporte para funcionalidades avançadas do ECMAScript, como async/await, em navegadores que não têm suporte nativo para elas.

Essas dependências são comumente usadas juntas para configurar um ambiente de desenvolvimento moderno para projetos JavaScript, permitindo escrever código usando recursos modernos do ECMAScript enquanto garante a compatibilidade com navegadores mais antigos.

# Configuração
1. Crie o arquivo webpack.config.js 

O arquivo webpack.config.js é usado para configurar o Webpack, uma ferramenta popular de empacotamento de módulos para JavaScript. Este arquivo contém as configurações que o Webpack usará para processar os arquivos do seu projeto.

```javascript
const path = require('path');

module.exports = {
    mode: 'development', // Define o modo de construção como desenvolvimento
    entry: './src/index.js', // Ponto de entrada do seu aplicativo
    output: {
        path: path.resolve(__dirname, 'public', 'assets', 'js'), // Diretório de saída para os arquivos gerados
        filename: 'bundle.js' // Nome do arquivo de saída
    },
    module: {
        rules: [{
            exclude: /node_modules/, // Exclui a pasta node_modules
            test: /\.js$/, // Selecione arquivos JavaScript
            use: {
                loader: 'babel-loader', // Use o babel-loader para transpilar arquivos JS
                options: {
                    presets: ['@babel/env'] // Use o preset @babel/env para transpilar para a versão do ECMAScript compatível
                }
            }
        }]
    },
    devtool: 'source-map' // Gera mapas de origem para depuração
};
```


