Aqui está uma versão do README adaptada especificamente para o estado do projeto até o commit mencionado, focando na implementação base da navegação e na estrutura essencial.

-----

# Navegação Base com Jetpack Compose

> **Status do Projeto:** Implementação inicial da estrutura de navegação.

[](https://www.google.com/search?q=LICENSE)
[](https://www.google.com/search?q=)
[](https://www.google.com/search?q=)

Este repositório apresenta a fundação de um sistema de navegação para Android, demonstrando como conectar múltiplas telas de forma declarativa e eficiente. Este estágio foca na configuração do `NavController` e na correta aplicação do `innerPadding` do `Scaffold`.

## ✨ Funcionalidades Implementadas

- **Navegação Declarativa:** Uso do `NavHost` para definir o grafo do aplicativo.
- **Login e Menu:** Fluxo inicial estabelecido entre a tela de autenticação e a tela principal.
- **Integração com Scaffold:** Garantia de que o conteúdo das telas respeite as barras do sistema (status bar e navigation bar) através do `innerPadding`.
- **Passagem de Controller:** Injeção do `navController` em cada Composable para permitir ações de navegação internas.

## 🚀 Tecnologias Utilizadas

- **Kotlin**
- **Jetpack Compose** (UI)
- **Navigation Compose** (Gerenciamento de rotas)
- **Material Design 3**

## 🧭 Lógica de Navegação

Nesta fase, a `MainActivity` atua como o orquestrador central:

1.  **Criação do Controller:** Utilizamos `rememberNavController()` para manter o estado da navegação durante recomposições.
2.  **Definição de Rotas:** O `NavHost` mapeia strings (IDs de rota) para funções Composable específicas.
3.  **Respeito ao Layout:** Cada tela recebe o `modifier` vindo do `Scaffold` da `MainActivity`, prevenindo que elementos da interface fiquem escondidos sob barras de navegação.

<!-- end list -->

```kotlin
// Exemplo da estrutura na MainActivity
Scaffold(modifier = Modifier.fillMaxSize()) { innerPadding ->
    NavHost(navController = navController, startDestination = "login") {
        composable("login") { 
            LoginScreen(navController, Modifier.padding(innerPadding)) 
        }
        // ... outras rotas
    }
}
```

## 📂 Estrutura de Pastas (Base)

```text
app/src/main/java/.../navigation_between_screens/
 ├── MainActivity.kt        # NavHost e Scaffold principal
 └── screens/               # Telas desacopladas
     ├── LoginScreen.kt     # Tela de entrada
     └── MenuScreen.kt      # Hub de navegação
```

## 📋 Observações Técnicas

- **Injeção de Padding:** É fundamental aplicar o `padding(innerPadding)` no componente raiz de cada tela para evitar sobreposição visual, um padrão essencial no Material 3.
- **Navegação Simples:** A navegação é feita via `navController.navigate("rota")` sem parâmetros complexos nesta etapa.

## 🛠️ Como rodar

1.  Clone este repositório.
2.  Abra no **Android Studio** (versão Ladybug ou superior recomendada).
3.  Execute o app; o fluxo inicial levará você da tela de Login para o Menu.

-----

## 👤 Autor e Referência

Este projeto é uma prática baseada nos conceitos de navegação do repositório do Professor [Ewerton Carreira](https://www.google.com/search?q=https://github.com/carreiras/android--navigation-between-screens-app).

**Luísa Souza Santos**

-----
