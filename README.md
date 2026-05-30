# 📖 Meu Livro de Receitas

> Projeto de aprendizado e portfólio — Aplicativo Android desenvolvido com C# e Xamarin.Forms

Este projeto foi desenvolvido com o objetivo de praticar o desenvolvimento mobile multiplataforma com o ecossistema Xamarin: criação de interfaces com XAML, persistência local com SQLite, acesso à galeria do dispositivo e operações de CRUD com validações.

**Não se trata de um sistema pronto para produção**, mas de um projeto estruturado para aprendizado.

---

## 🛠️ Stack

| Tecnologia | Versão | Descrição |
|---|---|---|
| C# | — | Linguagem principal |
| Xamarin.Forms | 5.0.0.2196 | Framework de UI multiplataforma (Android/iOS) |
| Xamarin.Essentials | 1.7.0 | Acesso à galeria de fotos do dispositivo |
| sqlite-net-pcl | 1.8.116 | ORM leve para banco de dados SQLite local |
| .NET Standard | 2.0 | Target framework do projeto compartilhado |
| Visual Studio | 2022 | IDE de desenvolvimento |

---

## 🖼️ Demonstração

> 📌 *Adicione aqui um GIF ou vídeo demonstrando o fluxo completo do aplicativo.*

<!-- Sugestão: grave um GIF mostrando: abrir o app → cadastrar receita → buscar → editar → excluir -->
<!-- ![Demo](./assets/demo.gif) -->

| Tela Inicial | Cadastrar Receita | Buscar Receitas |
|:---:|:---:|:---:|
| ![Home](./assets/screenshot-home.png) | ![Cadastro](./assets/screenshot-register.png) | ![Busca](./assets/screenshot-search.png) |

> 📌 *Substitua os placeholders acima pelas capturas de tela reais do aplicativo.*

---

## ✅ Funcionalidades

- Cadastrar receitas com nome, tempo de preparo, porções, ingredientes e modo de preparo
- Selecionar foto da galeria do dispositivo para ilustrar a receita
- Marcar e filtrar receitas como **favoritas**
- Listar e buscar receitas por nome
- Editar e excluir receitas com confirmação de diálogo
- Armazenamento 100% local com SQLite (sem necessidade de internet)
- Validações nos campos obrigatórios (nome, ingredientes e modo de preparo)

---

## 🗂️ Arquitetura de Pacotes

```
AppMeuLivroDeReceitas/
├── AppMeuLivroDeReceitas/               # Projeto compartilhado (Core)
│   ├── Models/
│   │   └── ModelRecipes.cs              # Entidade mapeada para a tabela "Recipes" no SQLite
│   ├── Services/
│   │   └── ServiceRecipesDB.cs          # CRUD + busca por nome e filtro de favoritos
│   ├── Views/
│   │   ├── PageHome.xaml(.cs)           # Tela inicial — navegação entre as seções
│   │   ├── PageRegister.xaml(.cs)       # Cadastro, edição e exclusão de receitas
│   │   ├── PageSearch.xaml(.cs)         # Listagem, busca por nome e filtro de favoritos
│   │   └── PageAbout.xaml(.cs)          # Informações sobre o aplicativo
│   └── App.xaml(.cs)                    # Ponto de entrada e caminho do banco SQLite
│
└── AppMeuLivroDeReceitas.Android/       # Projeto Android
    ├── MainActivity.cs                  # Inicializa o app e resolve o caminho do banco
    └── FileAccessHelper.cs              # Retorna o diretório local de armazenamento
```

---

## 🗄️ Modelo de Dados

Tabela `Recipes` — gerenciada pelo `sqlite-net-pcl` com criação automática:

| Campo | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `Id` | `int` | ✅ (PK, Auto) | Identificador único |
| `Name` | `string` | ✅ | Nome da receita |
| `Ingredients` | `string` | ✅ | Lista de ingredientes |
| `Preparation` | `string` | ✅ | Modo de preparo |
| `Favorite` | `bool` | ✅ | Marcada como favorita |
| `Time` | `string` | ❌ | Tempo de preparo (opcional) |
| `Portions` | `string` | ❌ | Número de porções (opcional) |
| `PhotoPath` | `string` | ❌ | Caminho da foto na galeria |

---

## 🚀 Como Executar

### Pré-requisitos

- [Visual Studio 2022](https://visualstudio.microsoft.com/) com a carga de trabalho **Desenvolvimento Móvel com .NET** (Xamarin)
- Android SDK configurado
- Emulador Android ou dispositivo físico com **Android 5.0 (API 21)** ou superior

### 1. Clone o repositório

```bash
git clone https://github.com/devDougie/app-meu-livro-de-receitas.git
cd app-meu-livro-de-receitas/projeto
```

### 2. Extraia o projeto

Extraia o arquivo `AppMeuLivroDeReceitas.7z` (requer [7-Zip](https://www.7-zip.org/)).

### 3. Abra e execute

1. No Visual Studio: **Arquivo → Abrir → Projeto/Solução → `AppMeuLivroDeReceitas.sln`**
2. Defina `AppMeuLivroDeReceitas.Android` como projeto de inicialização
3. Selecione um emulador ou dispositivo Android conectado
4. Pressione **F5**

O banco de dados `RecipesDB.db3` é criado automaticamente no armazenamento interno do dispositivo na primeira execução.

---

## 📱 Instalação via APK

Para instalar diretamente no dispositivo sem compilar:

1. Baixe o arquivo `com.companyname.appmeulivrodereceitas.apk` disponível na pasta `apk/`
2. No dispositivo: **Configurações → Segurança → Fontes desconhecidas** (ou **Instalar apps desconhecidos** no Android 8+)
3. Abra o `.apk` no dispositivo e confirme a instalação

> ⚠️ O APK disponível é uma build de Debug gerada para testes.

---

## 🎯 Objetivos de aprendizado

- ✅ Estrutura de projeto Xamarin.Forms com projeto compartilhado e projeto Android
- ✅ Criação de interfaces com XAML e code-behind em C#
- ✅ Persistência local com SQLite via `sqlite-net-pcl`
- ✅ CRUD completo com validações na camada de serviço
- ✅ Acesso à galeria de fotos com `Xamarin.Essentials`
- ✅ Navegação entre páginas com `NavigationPage`
- ✅ Listagem com `ListView`, binding de dados e filtros dinâmicos
