# 🖨️ Impressora em C — Controle de Impressora Térmica Elgin (i8 / i9)

---

## 📘 Sobre o Projeto

Trabalho em grupo desenvolvido para a disciplina de **Construção de Algoritmos** do 2º semestre do curso de **Ciência da Computação** da **UNASP**.

O programa é uma aplicação de console escrita em **linguagem C** que se comunica com impressoras térmicas **Elgin i8** e **Elgin i9** utilizando a biblioteca `E1_Impressora01.dll`. Ele conta com autenticação por login, menu interativo em laço e comandos para impressão de texto, QR Code, código de barras, cupons XML SAT (venda e cancelamento), abertura de gaveta de dinheiro e emissão de sinal sonoro.

---

## 🧰 Tecnologias Utilizadas

- **Linguagem C**
- **GCC / MinGW** (ou **Code::Blocks**)
- **SDK / DLL Elgin E1 (`E1_Impressora01.dll`)**
- **Windows API (`windows.h`)** para carregamento dinâmico da DLL (`LoadLibraryA` / `GetProcAddress`)

---

## 📁 Estrutura do Projeto

```text
Impressora-em-C/
├── main.c                          # Código-fonte principal em C
├── E1_Impressora01.dll             # Biblioteca de comunicação com a impressora Elgin
├── Bibliotecas E1 Impressora.zip   # Pacote com as versões x86 (32 bits) e x64 (64 bits) da DLL
├── XMLSAT.xml                      # XML de teste para impressão de cupom SAT
├── CANC_SAT.xml                    # XML de teste para impressão de cancelamento SAT
├── ASS_QRCODE Cancelamento Sat.txt # Assinatura QR Code usada no cancelamento SAT
├── Trabalho_C_Impressora.pdf       # Documentação e especificação completa do trabalho
└── README.md                       # Documentação do repositório
```

---

## ⚙️ Como Compilar e Executar

### 1. Escolher a DLL correta (32 bits ou 64 bits)
A `E1_Impressora01.dll` na raiz do projeto precisa ter a **mesma arquitetura** do seu compilador C. Para verificar qual arquitetura o seu GCC utiliza, execute no terminal:

```bash
gcc -dumpmachine
```

- **`x86_64-w64-mingw32` (64 bits):** utilize a `E1_Impressora01.dll` da pasta **x64** (disponível em `Bibliotecas E1 Impressora.zip`).
- **`mingw32` ou `i686-w64-mingw32` (32 bits — padrão do MinGW no Code::Blocks):** utilize a `E1_Impressora01.dll` da pasta **x86**.

> **Importante:** os arquivos `E1_Impressora01.dll`, `XMLSAT.xml` e `CANC_SAT.xml` devem estar na **raiz do projeto** (mesmo diretório de onde o executável é iniciado).

### 2. Compilar e executar pelo terminal (GCC)
Com a impressora ligada e conectada via USB, execute na pasta do projeto:

```bash
gcc main.c -o impressora.exe
impressora.exe
```

### 3. Executar pelo Code::Blocks
1. Crie um projeto em *File → New → Project → Console application → C*.
2. Substitua o conteúdo de `main.c` pelo arquivo deste repositório.
3. Copie `E1_Impressora01.dll`, `XMLSAT.xml` e `CANC_SAT.xml` para a pasta do projeto (mesma pasta do arquivo `.cbp`).
4. Em *Project → Properties → Build targets*, confirme que *Execution working dir* aponta para a pasta do projeto.
5. Compile e execute o projeto.

---

## 🔐 Login de Teste

Ao iniciar o programa, o usuário tem até **3 tentativas** para realizar login:

- **Usuário:** `admin`
- **Senha:** `1234`

### Parâmetros padrão para teste (USB)
- **Tipo de conexão:** `1` (USB)
- **Modelo:** `i9` (ou `i8`)
- **Porta:** `USB`
- **Parâmetro:** `0`

---

## 📋 Opções do Menu

| Opção | Funcionalidade |
| :---: | --- |
| `1` | Configurar conexão |
| `2` | Abrir conexão |
| `3` | Fechar conexão |
| `4` | Imprimir texto |
| `5` | Imprimir QR Code |
| `6` | Imprimir código de barras |
| `7` | Imprimir XML SAT |
| `8` | Imprimir XML de cancelamento SAT |
| `9` | Abrir gaveta (Elgin) |
| `10` | Abrir gaveta |
| `11` | Emitir sinal sonoro |
| `0` | Sair (fecha a conexão e encerra o programa) |

---

## 📚 Documentação Adicional

- [Trabalho_C_Impressora.pdf](Trabalho_C_Impressora.pdf) — Especificação completa do projeto
- [Documentação Oficial do SDK Elgin E1](https://elgindevelopercommunity.github.io/group___m1.html)

---

## 👥 Autores


- Iago Melo Santos
- João Pedro Silva de Souza
- Pedro Henrique Dias
- Pedro Henrique Menardi
