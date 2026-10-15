# Sistema de Registro de Ponto com Reconhecimento Facial

Sistema de ponto em que o funcionário é identificado pelo rosto, sem crachá nem senha. Stack: **React** (frontend), **Python** (backend/API) e **DeepFace** (reconhecimento facial).

## Como funciona

1. O funcionário é cadastrado com nome, matrícula, cargo e uma foto do rosto.
2. Na hora de bater o ponto, a câmera captura o rosto e o usuário escolhe o tipo de registro (entrada, saída ou intervalo).
3. O backend compara a imagem capturada com as fotos cadastradas usando o DeepFace.
4. Se o rosto for reconhecido, o sistema grava o funcionário, a data, o horário e o tipo no banco de dados. Se não for, o registro é recusado.

O sistema também lista os funcionários cadastrados e o histórico de registros de ponto.

## Estrutura do repositório

```
frontend/   Aplicação React (telas de cadastro, ponto, lista e histórico)
backend/    API em Python com DeepFace e banco de dados
TODO.md     Etapas do trabalho
```

## Como rodar

Pré-requisitos: **Python 3.10+** e **Node.js 18+**, além de uma webcam.

### Backend

```bash
cd backend
python -m venv venv

# Windows
venv\Scripts\activate
# Linux / macOS
source venv/bin/activate

pip install -r requirements.txt
uvicorn main:app --reload
```

A API fica disponível em `http://localhost:8000`. Na primeira comparação de rostos, o DeepFace baixa os modelos de reconhecimento, o que pode levar alguns minutos.

### Frontend

Em outro terminal:

```bash
cd frontend
npm install
npm run dev
```

A aplicação abre em `http://localhost:5173`.

## Protótipo no Figma

- **Design (telas e Design System):** [Sistema de Ponto Facial - Protótipo](https://www.figma.com/design/5Y7FsRmhNjt7szVgpjcrXk/Sistema-de-Ponto-Facial---Prot%25C3%25B3tipo?node-id=0-1&p=f&t=81vKN0pl9Jsuuk34-0)
- **Protótipo navegável:** [abrir apresentação](https://www.figma.com/proto/5Y7FsRmhNjt7szVgpjcrXk/Sistema-de-Ponto-Facial---Prot%25C3%25B3tipo?node-id=10-133&starting-point-node-id=10%3A133)

O arquivo tem duas páginas:

- **🎨 Design System:** paleta, tipografia (Inter) e componentes (botão, campo de texto, card, badge, menu lateral, câmera, diálogo de resultado, linhas de tabela).
- **📱 Telas:** Cadastro de Funcionário, Registro de Ponto, resultado do ponto (sucesso e falha), Lista de Funcionários e Histórico de Registros.

No protótipo, o botão **Registrar ponto** leva ao resultado de sucesso; clicar na área da câmera simula a falha (rosto não reconhecido).

## Links

- Atividade no Google Classroom: https://classroom.google.com/u/2/c/ODc0NDk1NDYxNjE3/a/ODkwMDk0NjI0NjM0/details
- Rascunhos do time no Figma: https://www.figma.com/files/team/1692696062871435762/drafts?fuid=1237537487595721215
