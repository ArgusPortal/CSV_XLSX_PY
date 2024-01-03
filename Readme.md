# CSV_XLSX_PY

Automatizando Processos e Otimizando Tarefas com Python 🚀

Quero compartilhar com vocês uma ferramenta valiosa que desenvolvi recentemente para otimizar tarefas diárias utilizando a linguagem de programação Python. Automatizar processos pode ser a chave para um fluxo de trabalho mais eficiente e produtivo. No meu caso, utilizei códigos Python para simplificar a conversão de arquivos CSV para XLSX, uma tarefa que frequentemente consome tempo.

A Necessidade:
Em um mundo onde o tempo é um recurso valioso, cada minuto economizado em tarefas rotineiras se traduz em maior produtividade. Lidar com grandes conjuntos de dados em formato CSV é comum, mas a necessidade de convertê-los para XLSX pode ser trabalhosa, especialmente quando lidamos com vários arquivos.

A Solução:
Desenvolvi um conjunto de scripts em Python que automatizam esse processo. O código verifica uma pasta de entrada, converte todos os arquivos CSV para XLSX utilizando a biblioteca Pandas, e organiza os resultados em uma pasta de saída. Essa automação não só economiza tempo, mas também reduz erros manuais.

Por Que Isso é Importante?

Eficiência Operacional: Ao automatizar tarefas repetitivas, liberei tempo para focar em atividades mais estratégicas e desafiadoras.
Redução de Erros: A automação minimiza a probabilidade de erros humanos, proporcionando resultados mais precisos e consistentes.
Escalabilidade: Esses scripts podem ser escalados para lidar com grandes volumes de dados, adaptando-se às necessidades crescentes.

Como Você Pode Aplicar Isso?
Se você trabalha com dados e realiza tarefas repetitivas, considere a automação. Python é uma linguagem versátil e acessível, e a automação de tarefas pode ser implementada em diversas áreas, desde processamento de dados até organização de arquivos.

Conclusão:
A automação é uma ferramenta poderosa para impulsionar a produtividade. Ao incorporar códigos Python em meu fluxo de trabalho, percebi uma melhoria significativa na eficiência e na qualidade dos resultados. Vamos explorar mais formas de otimizar nossas tarefas diárias e criar um ambiente de trabalho mais ágil e inovador.

Utilizei ainda o **Google Colab** que já entrega de forma gratuita um ambiente em nuvem para desenvolvimento, similarmente ao famoso Jupyter Notebook.

Este foi o meu contexto, mas a biblioteca **Pandas** é bastante versátil e poderá com certeza te ajudar de alguma forma.


Segue abaixo o código detalhado passo a passo:


1. **Importação de Módulos:**
   ```python
   import os
   import pandas as pd
   ```
   - `os`: Fornece uma maneira de interagir com o sistema operacional, neste caso, para verificar e criar pastas.
   - `pandas as pd`: Pandas é uma biblioteca muito utilizada para manipulação e análise de dados em Python. Ela oferece estruturas de dados poderosas, como o DataFrame, que é utilizado neste código.

2. **Definição da Função:**
   ```python
   def csv_to_xlsx(input_folder, output_folder):
   ```
   - `def`: Define uma função em Python.
   - `csv_to_xlsx`: Nome da função.
   - `input_folder` e `output_folder`: Parâmetros que a função recebe. Eles representam os caminhos para a pasta de entrada (onde estão os arquivos CSV) e a pasta de saída (onde os arquivos XLSX serão salvos), respectivamente.

3. **Verificação e Criação da Pasta de Saída:**
   ```python
   if not os.path.exists(output_folder):
       os.makedirs(output_folder)
   ```
   - `os.path.exists(output_folder)`: Verifica se a pasta de saída já existe.
   - `os.makedirs(output_folder)`: Cria a pasta de saída se ela não existir.

4. **Listagem de Arquivos na Pasta de Entrada:**
   ```python
   files = os.listdir(input_folder)
   ```
   - `os.listdir(input_folder)`: Obtém uma lista de todos os arquivos na pasta de entrada.

5. **Iteração sobre os Arquivos:**
   ```python
   for file in files:
   ```
   - `for file in files`: Itera sobre cada arquivo na lista de arquivos.

6. **Verificação se o Arquivo é um CSV:**
   ```python
   if file.endswith(".csv"):
   ```
   - `file.endswith(".csv")`: Verifica se o nome do arquivo termina com ".csv".

7. **Leitura do Arquivo CSV com o Pandas:**
   ```python
   df = pd.read_csv(csv_path, encoding='utf8')
   ```
   - `pd.read_csv(csv_path, encoding='utf8')`: Utiliza o Pandas para ler o arquivo CSV especificado em `csv_path` e armazena os dados em um DataFrame chamado `df`.

8. **Geração do Nome do Arquivo XLSX e Caminho:**
   ```python
   xlsx_file = os.path.splitext(file)[0] + ".xlsx"
   xlsx_path = os.path.join(output_folder, xlsx_file)
   ```
   - `os.path.splitext(file)[0]`: Divide o nome do arquivo em uma tupla, usando o ponto como separador. `[0]` pega o primeiro elemento da tupla, que é o nome do arquivo sem a extensão.
   - `os.path.join(output_folder, xlsx_file)`: Combina o nome do arquivo XLSX com o caminho da pasta de saída para obter o caminho completo.

9. **Escrita do DataFrame no Arquivo XLSX:**
   ```python
   df.to_excel(xlsx_path, index=False)
   ```
   - `df.to_excel(xlsx_path, index=False)`: Escreve o DataFrame (`df`) no arquivo XLSX especificado em `xlsx_path`. O parâmetro `index=False` evita que o índice seja incluído no arquivo.

10. **Exibição de Mensagem de Conversão Concluída:**
   ```python
   print(f'Conversão concluída: {file} -> {xlsx_file}')
   ```
   - `print(f'Conversão concluída: {file} -> {xlsx_file}')`: Exibe uma mensagem indicando a conclusão da conversão para cada arquivo processado.

11. **Definição dos Caminhos de Entrada e Saída:**
   ```python
   input_folder = "/content/"
   output_folder = "/content/XLSX"
   ```
   - Essas linhas definem os caminhos para a pasta de entrada e a pasta de saída. Esses valores podem ser alterados conforme necessário.

12. **Chamada da Função:**
   ```python
   csv_to_xlsx(input_folder, output_folder)
   ```
   - Finalmente, a função `csv_to_xlsx` é chamada, usando os caminhos de entrada e saída definidos anteriormente. Isso inicia o processo de conversão dos arquivos CSV para XLSX.


---------------------------------------------------------------------------------------------------------------------------------------
Compactação dos Arquivos 

1. **Importação do Módulo `shutil`:**
   ```python
   import shutil
   ```
   - `shutil`: Um módulo em Python que oferece uma variedade de operações de alto nível em arquivos e coleções de arquivos. Neste caso, está sendo usado para operações relacionadas a arquivos e pastas.

2. **Compactação da Pasta de Saída em um Arquivo Zip:**
   ```python
   shutil.make_archive("/content/XLSX", 'zip', "/content/XLSX")
   ```
   - `shutil.make_archive("/content/XLSX", 'zip', "/content/XLSX")`: Cria um arquivo zip da pasta de saída. Os parâmetros são:
      - `"/content/XLSX"`: O nome base para o arquivo zip que será criado.
      - `'zip'`: O formato do arquivo (no caso, um arquivo zip).
      - `"/content/XLSX"`: O caminho da pasta que será compactada.

3. **Movimentação do Arquivo Zip para uma Localização mais Conveniente:**
   ```python
   shutil.move("/content/XLSX.zip", "/content/XLSX.zip")
   ```
   - `shutil.move("/content/XLSX.zip", "/content/XLSX.zip")`: Move o arquivo zip criado para a pasta raiz (`/content`). Isso pode facilitar o download do arquivo zip, uma vez que estará em um local de fácil acesso.

Este segundo bloco de código complementa o primeiro, compactando a pasta de saída (que contém os arquivos XLSX gerados) em um arquivo zip e, em seguida, movendo esse arquivo zip para a pasta raiz. Isso pode ser útil para organizar e disponibilizar de forma mais acessível o resultado da conversão dos arquivos CSV para XLSX.

Espero ter ajudado !

Forte Abraço.
