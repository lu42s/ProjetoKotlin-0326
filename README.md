Navegação e Parâmetros com Jetpack Compose
Este projeto demonstra como transitar entre telas em um aplicativo Android e, principalmente, como carregar dados de uma tela para outra utilizando diferentes tipos de argumentos.

🎯 O que este projeto resolve?
Em um app real, raramente apenas "abrimos" uma tela. Geralmente, abrimos a tela de um produto específico ou a tela de um usuário logado. Este projeto explora as duas formas de fazer isso com o Navigation Compose.

🧭 Tipos de Parâmetros na Navegação
Implementamos duas estratégias de passagem de dados no NavHost:

1. Parâmetros Obrigatórios (Path Arguments)
Utilizados na tela de Perfil. O app entende que não faz sentido exibir um perfil se não soubermos de quem ele é.

Como funciona: O dado faz parte da própria URL da rota.

Rota definida: perfil/{nome}

Chamada: navController.navigate("perfil/Lucas")

Obrigatório: Se você tentar navegar para perfil/ sem o nome, o app gerará um erro, pois a rota não será encontrada.

2. Parâmetros Opcionais (Query Strings)
Utilizados na tela de Pedidos. Imagine uma lista de pedidos que pode ou não estar filtrada por um cliente.

Como funciona: Usamos a sintaxe de interrogação ?, igual em endereços de sites (URLs).

Rota definida: pedidos?cliente={cliente}

Chamada com dado: navController.navigate("pedidos?cliente=Android Store")

Chamada sem dado: navController.navigate("pedidos")

Opcional: Se o nome do cliente não for enviado, o sistema de navegação ainda abre a tela, e nós tratamos o valor como "vazio" ou "padrão" no código.

🛠 Componentes Técnicos
navController: O objeto que recebe a ordem de navegar e transporta os dados.

backStackEntry: O "recipiente" onde os dados chegam na tela de destino. É através dele que recuperamos as Strings enviadas.

innerPadding: Aplicado em todas as telas para garantir que o texto não fique escondido atrás do entalhe (notch) da câmera ou da barra de navegação do celular.

📂 Estrutura Simplificada
MainActivity.kt: Contém o "mapa" de rotas e a lógica de captura dos argumentos.

screens/: Contém a interface visual de cada etapa do fluxo (Login, Menu, Perfil e Pedidos).

🚀 Como testar no código
Para entender a diferença na prática, observe estas linhas no arquivo de navegação:

Baseado nos estudos de Jetpack Compose e Navigation.
