# TODO: Sistema de Registro de Ponto com Reconhecimento Facial

Stack exigida pelo trabalho: **React** (frontend), **Python** (backend/API) e **DeepFace** (reconhecimento facial).

Fluxo básico: cadastro do funcionário → captura da foto → armazenamento dos dados → captura facial no ponto → comparação pelo DeepFace → funcionário identificado → registro de data e horário no banco de dados.

---

## 1. Protótipo no Figma (fazer primeiro)

- [x] Criar o arquivo no Figma e definir paleta, tipografia e componentes básicos (botões, inputs, cards)
- [x] Tela de **Cadastro de Funcionário**: campos nome, matrícula e cargo + área de captura/upload da foto facial
- [x] Tela de **Registro de Ponto**: visualização da câmera, botão de captura e seleção do tipo (entrada, saída, intervalo)
- [x] Estados de resultado do ponto: sucesso (funcionário identificado + data/hora) e falha (rosto não reconhecido)
- [x] Tela de **Lista de Funcionários** cadastrados
- [x] Tela de **Histórico de Registros** (funcionário, data, horário, tipo)
- [x] Ligar as telas em um protótipo navegável
- [ ] Adicionar o link do Figma no README.md

## 2. Estrutura do repositório

- [ ] Criar as pastas `frontend/` (React) e `backend/` (Python)
- [ ] Criar `.gitignore` (node_modules, venv, `__pycache__`, banco local, fotos cadastradas)
- [ ] Atualizar o README.md com a descrição do projeto e as instruções para rodar

## 3. Backend (Python)

- [ ] Criar o ambiente virtual e o `requirements.txt`
- [ ] Escolher o framework da API (ex.: FastAPI ou Flask) e configurar CORS para o React
- [ ] Instalar e testar o DeepFace isoladamente (comparar duas fotos com `DeepFace.verify`)

### Banco de dados

- [ ] Escolher o banco (ex.: SQLite para começar)
- [ ] Tabela **funcionarios**: id, nome, matrícula (única), cargo, caminho da foto, data de cadastro
- [ ] Tabela **registros_ponto**: id, funcionario_id, data, horário, tipo (entrada / saída / intervalo)

### Endpoints

- [ ] `POST /funcionarios`: recebe nome, matrícula, cargo e foto, salva a imagem e os dados
- [ ] `GET /funcionarios`: lista os funcionários cadastrados
- [ ] `POST /ponto`: recebe a imagem capturada e o tipo de registro, compara com as fotos cadastradas via DeepFace e, se reconhecer, grava funcionário, data, horário e tipo
- [ ] `GET /registros`: lista o histórico de registros de ponto
- [ ] Tratar os erros: nenhum rosto detectado na imagem, rosto não reconhecido, matrícula duplicada

## 4. Frontend (React)

- [ ] Criar o projeto React (ex.: Vite) dentro de `frontend/`
- [ ] Configurar rotas entre as telas
- [ ] Implementar a tela de Cadastro de Funcionário seguindo o protótipo
- [ ] Capturar a foto pela webcam (ex.: `react-webcam` ou `getUserMedia`) no cadastro
- [ ] Implementar a tela de Registro de Ponto: abrir a câmera, capturar o rosto e enviar para `POST /ponto`
- [ ] Exibir o resultado do ponto (nome do funcionário, data, horário e tipo, ou mensagem de erro)
- [ ] Implementar a Lista de Funcionários
- [ ] Implementar o Histórico de Registros

## 5. Integração e testes

- [ ] Testar o fluxo completo: cadastrar → bater o ponto → conferir o registro no banco
- [ ] Testar com uma pessoa não cadastrada (deve recusar)
- [ ] Testar entrada, saída e intervalo para o mesmo funcionário

## 6. Entrega

- [ ] README.md final com: objetivo, tecnologias, como rodar backend e frontend, link do Figma e prints das telas
- [ ] Revisar o código e fazer o commit/push final
