## Descrição do projeto

O projeto consiste em um aplicativo Android desenvolvido utilizando **Kotlin** e **Jetpack Compose**, com foco na implementação de navegação entre múltiplas telas.

A aplicação possui quatro telas principais:

- **Login**: tela inicial do aplicativo
- **Menu**: tela intermediária de navegação
- **Perfil**: exibe informações do usuário
- **Pedidos**: exibe informações relacionadas a pedidos

O sistema utiliza o **NavController** e o **NavHost** para gerenciar a navegação entre as telas, permitindo a troca de informações por meio de parâmetros dinâmicos.

---

## Objetivo da prova

O objetivo da atividade foi aplicar os conceitos de **navegação no Jetpack Compose**, com ênfase na passagem de parâmetros entre telas.

Entre os principais objetivos, destacam-se:

- Compreender o funcionamento do **NavController** e do **NavHost**
- Implementar rotas dinâmicas
- Enviar e receber dados entre telas
- Trabalhar com parâmetros obrigatórios e opcionais
- Utilizar tipagem de argumentos (`NavType`)
- Evitar erros de navegação com valores padrão

---

## Explicação de cada evolução implementada

### O que foi implementado?

Foram implementadas melhorias na navegação do aplicativo utilizando **Jetpack Compose Navigation**, com foco no envio e recebimento de parâmetros entre telas.

As principais alterações realizadas foram:

- Adaptação das telas **Perfil** e **Pedidos** para receber dados dinâmicos.
- Inclusão de parâmetros nas funções `@Composable`:
    - **Perfil**: recebe `nome` e `idade`
    - **Pedidos**: recebe `cliente` (opcional)
- Exibição dos dados recebidos diretamente na interface.
- Implementação de navegação com passagem de parâmetros entre telas.
- Configuração do `NavHost` com rotas dinâmicas e tipagem de argumentos.

Com isso, o aplicativo passou a trabalhar com **dados dinâmicos**, ao invés de informações fixas.

---

## Como a navegação foi configurada?

A navegação foi implementada utilizando o **NavController** e o **NavHost**, definindo rotas para cada tela.

### Rotas definidas

- `login` → Tela inicial
- `menu` → Menu principal
- `perfil/{nome}/{idade}` → Rota com parâmetros obrigatórios
- `pedidos?cliente={cliente}` → Rota com parâmetro opcional

---

### Configuração no NavHost

#### Perfil (parâmetros obrigatórios)
```kotlin
composable(
    route = "perfil/{nome}/{idade}",
    arguments = listOf(
        navArgument("nome") { type = NavType.StringType },
        navArgument("idade") { type = NavType.IntType }
    )
)
```

### Como os parâmetros são enviados e recebidos?

A comunicação entre telas ocorre através de envio de parâmetros na navegação e recuperação desses parâmetros no destino.

#### Envio de parâmetros

Os dados são enviados utilizando o método:

`navController.navigate()`

#### Recebimento de parâmetros

Os parâmetros são recuperados dentro do NavHost através do objeto:

`it.arguments`

#### Estruturação

A navegação foi estruturada utilizando rotas dinâmicas com parâmetros, permitindo a comunicação entre telas de forma eficiente.

Foram utilizados dois tipos de passagem de dados:

- **Path Parameters** → `perfil/{nome}/{idade}`
- **Query Parameters** → `pedidos?cliente=...`

Além disso, foi aplicada tipagem de argumentos (NavType) e valores padrão, garantindo maior segurança e evitando erros durante a navegação.
