Sistema Picos Extintor

Escopo do Módulo

Este projeto é um sistema de gestão para a empresa Picos Extintor, com foco nas seguintes áreas:

 1. Administração de Veículos (`apps/administracao/veiculos) Gabriel de Sousa Rodrigues
- Cadastro, edição, listagem e visualização de veículos
- Gerenciamento de placa, modelo, capacidade de carga e quilometragem atual

2. Compras  (`apps/compras`): Marcos Emanuel de Macedo Sousa e Luiz Antonio Rodrigues Carvalho
- Cadastro e gerenciamento de produtos
- Controle de estoque por filial (3 filiais: Picos Centro, Picos Paraibinha, Paulistana)
- Solicitação de entrega de produtos
- Gerenciamento de fornecedores
- Relatórios de movimentações

3. Extintores (`apps/extintor`): Diego Morais Sousa
- Registro de vendas e recargas de extintores
- Registro de visitas
- Listagem de produtos e serviços
- Relatórios de vendas, recargas e visitas

4. Rotas e Logística (`apps/rotas`):**GUstavo Henrique de Macedo e Lucas Reis Araujo**
- Criação, edição e gerenciamento de rotas
- Associação de veículos e vendedores às rotas
- Controle de carga (produtos) em cada rota
- Registro de despesas da rota
- Cálculo de quilometragem rodada
- Relatórios de rotas, incluindo lucro, km rodado, despesas por categoria, etc.
- Integração com geocoding para cálculo de rotas

Instruções de Instalação:

1. Pré-requisitos
- Python 3.10 ou superior
- PostgreSQL (ou outro banco de dados configurado no .env)
- wkhtmltopdf (para geração de PDFs)

2. Passo a passo de instalação

1. Clone o repositório e navegue até o diretório do projeto:
   ```bash
   cd d:\Nova pasta\picos-extintor-main\picos-extintor-main
   ```

2. Crie e ative um ambiente virtual (opcional, mas recomendado):
   - Windows:
     ```bash
     python -m venv venv
     venv\Scripts\activate
     ```

3. Instale as dependências:
   ```bash
   pip install -r requirements.txt
   ```

4. Configure o arquivo .env:
   - Copie o arquivo de exemplo (se existir) ou crie um novo arquivo `.env` na raiz do projeto com as seguintes variáveis:
     ```
     SECRET_KEY=Chave_secreta
     STATUS_DEBUG=True
     DB_ENGINE=django.db.backends.postgresql
     DB_NAME=nome_do_banco
     DB_USER=usuario_do_banco
     DB_PASSWORD=senha_do_banco
     DB_HOST=localhost
     DB_PORT=5432
     DBBACKUP_STORAGE=caminho/para/backups
     ```

5. Realize as migrações do banco de dados:
   ```bash
   python manage.py migrate
   ```

6. Crie um superusuário (para acessar o admin):
   ```bash
   python manage.py createsuperuser
   ```

7. Colete os arquivos estáticos (opcional para desenvolvimento):
   ```bash
   python manage.py collectstatic
   ```

8. Inicie o servidor local:
   ```bash
   python manage.py runserver
   ```

9. Acesse o sistema:
   - Acesse `http://localhost:8000` no seu navegador
   - Acesse o admin em `http://localhost:8000/admin`

 Manual de Utilização

 Geral
- Faça login com suas credenciais de usuário
- Navegue pelo menu principal para acessar os módulos

 Administração de Veículos
1. Acesse o módulo de Veículos
2. Clique em "Cadastrar Veículo" para adicionar um novo veículo
3. Preencha os campos: placa, modelo, capacidade de carga e quilometragem atual
4. Clique em "Salvar"
5. Use a lista para visualizar, editar ou excluir veículos

Compras 
1. acesse o Modulo de Compras
2. clique em pedidos e depois no botão **criar pedidos**
3. na pagina de criar pedidos, selecione os formularios a seguir: filial, rota,produtos(qual tipo de extintor vai ser entregue), a quantidade, metodo de pagamento, observações, data de vencimento
4. Clique em "Salvar"
5. relatorio de pedidos
5. 1. visualizar os pedidos criados
5. 2. exportar para pdf

Extintores
1. Acesse o módulo de Extintores
2. Vendas/Recargas: Registre novas vendas ou recargas
3. Visitas: Registre visitas a clientes
4. Relatórios: Visualize e exporte relatórios de vendas, recargas e visitas

Rotas
1. Acesse o módulo de Rotas
2. Criar Rota: Adicione uma nova rota, preenchendo código, nome, vendedor, veículo, KM inicial e data de saída
3. Gerenciar Cargas: Adicione produtos à rota (isso diminui o estoque da filial)
4. Registrar Despesas: Adicione despesas como combustível, pedágio, alimentação, etc.
5. Iniciar Rota: Altere o status da rota para "Em Andamento"
6. Concluir Rota: Preencha a data de chegada e KM final, devolvendo sobras ao estoque
7. Relatórios: Visualize relatórios detalhados de rotas, incluindo lucro, km rodado, despesas, etc.

Tecnologias Utilizadas
- Django 5.2.5
- PostgreSQL
- Bootstrap 5
- ApexCharts (gráficos)
- wkhtmltopdf (geração de PDFs)
- Geopy/Geocoding (cálculo de rotas)
