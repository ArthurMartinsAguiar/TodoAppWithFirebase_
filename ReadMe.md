# 📝 Gerenciador de Tarefas - Firebase + Jetpack Compose

Este é um aplicativo nativo para Android focado em produtividade, desenvolvido com **Kotlin**. A aplicação utiliza o **Jetpack Compose** para uma interface moderna e o **Firebase** como infraestrutura de backend, priorizando práticas recomendadas como injeção de dependência e arquitetura escalável.

## 🚀 Recursos Principais

* **Sistema de Autenticação:**
    * Fluxo de Login e Registro via e-mail/senha utilizando Firebase Authentication.
    * Validação de campos e tratamento de erros nativo.
* **Controle de Tarefas (CRUD):**
    * Adição rápida de novas pendências.
    * Listagem dinâmica com sincronização em tempo real.
    * Alternância de status (concluído/pendente) via Checkbox.
    * Remoção simplificada de registros.
* **UI Declarativa:** Interface 100% responsiva e reativa, aproveitando o poder do Compose para refletir mudanças de estado instantaneamente.

## 🏗️ Estrutura e Arquitetura

O software foi construído seguindo os princípios de **Clean Architecture** e o padrão **MVVM (Model-View-ViewModel)**, garantindo um código modular e fácil de testar.

### 1. Camadas do MVVM
* **View:** Implementada com Compose, foca estritamente na renderização da interface e na observação dos estados fornecidos pela ViewModel.
* **ViewModel:** Atua como ponte entre os dados e a UI. Utiliza `StateFlow` ou `LiveData` para gerenciar estados e lida com a lógica de apresentação, mantendo-se íntegra durante mudanças de configuração.
* **Model:** Define as entidades de dados da aplicação, como a classe `TodoTask`.

### 2. Injeção de Dependência com Hilt
Para gerenciar o ciclo de vida dos componentes e reduzir o acoplamento, utilizamos o **Hilt (Dagger)**.
* **Vantagem:** Facilita a escalabilidade. Com anotações como `@AndroidEntryPoint`, as dependências (como os repositórios) são fornecidas automaticamente, eliminando a necessidade de instanciar classes manualmente dentro das Activities ou ViewModels.

### 3. Repository Pattern
Implementamos uma camada de abstração para o acesso a dados.
* **Estratégia:** O repositório centraliza a comunicação com o Firebase. Isso permite que, caso o projeto precise migrar para uma API REST ou banco de dados local (Room) no futuro, a mudança seja feita em um único local sem afetar a lógica da interface.

### 4. Navegação Moderna
A transição entre telas (ex: autenticação para a Home) é gerida pelo **Navigation Compose**, seguindo a arquitetura de "Single Activity".

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Kotlin
* **Interface:** Jetpack Compose (Material Design 3)
* **DI:** Hilt
* **Backend:** Firebase (Auth & Firestore/Realtime Database)
* **Concorrência:** Coroutines & Flow para operações assíncronas

---

## 📱 Visão Geral das Telas

### Autenticação
Interface intuitiva voltada para a experiência do usuário (UX), com feedbacks visuais claros para erros de digitação ou falhas de login.

### Home (Painel de Tarefas)
Central de controle onde o usuário visualiza sua
