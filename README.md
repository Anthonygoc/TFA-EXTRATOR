# Extrator TCFA IBAMA

Sistema desktop desenvolvido em Python para automatizar a extração de dados de relatórios PDF de inadimplentes da TCFA/IBAMA e preencher uma planilha Excel modelo com os registros encontrados.

O objetivo do projeto é reduzir o trabalho manual de copiar informações do relatório PDF para a planilha, garantindo maior agilidade, padronização e menor risco de erro no preenchimento dos dados.

## Funcionalidades

- Leitura automática de relatório PDF da TCFA/IBAMA.
- Extração dos dados dos contribuintes inadimplentes.
- Identificação automática de:
  - CNPJ;
  - Contribuinte;
  - Categoria;
  - Porte;
  - Número do débito IBAMA;
  - Valor em reais;
  - Valor por extenso;
  - Trimestre;
  - Ano de referência;
  - Cidade/Município.
- Tratamento de registros quebrados em múltiplas linhas no PDF.
- Preenchimento automático de planilha Excel `.xlsx` ou `.xlsm`.
- Preservação de macros da planilha quando o arquivo base for `.xlsm`.
- Limpeza dos dados antigos da planilha antes do novo preenchimento.
- Interface gráfica simples para seleção do PDF e da planilha base.
- Geração de nova planilha preenchida automaticamente.

## Tecnologias utilizadas

- Python 3
- PyQt6
- pdfplumber
- openpyxl
- num2words
- PyInstaller

## Estrutura geral do funcionamento

O sistema funciona em quatro etapas principais:

1. O usuário seleciona o relatório PDF da TCFA/IBAMA.
2. O usuário seleciona a planilha base que será preenchida.
3. O sistema lê o PDF, identifica as tabelas e extrai os registros.
4. O sistema gera uma nova planilha preenchida com os dados extraídos.

## Dados extraídos do PDF

O sistema busca no PDF as informações referentes aos débitos da TCFA, normalmente organizadas por município.

Cada registro extraído corresponde a uma linha de débito do relatório, contendo informações como CNPJ, nome do contribuinte, categoria, porte, débito e valor.

O sistema também trata casos em que o PDF quebra o nome do contribuinte em mais de uma linha. Isso evita que o campo `CONTRIBUINTE` fique vazio ou incompleto na planilha final.

## Planilha de saída

A planilha gerada mantém a estrutura da planilha base e preenche os campos correspondentes aos dados extraídos.

Campos esperados na planilha:

- VALOR R$
- VALOR POR EXTENSO
- Nº DÉBITO IBAMA
- TRIMESTRE
- ANO DE REFÊRENCIA
- CATEGORIA
- PORTE
- CNPJ
- CONTRIBUINTE
- CIDADE

O sistema também reconhece variações no nome das colunas, como:

- `VALOR`
- `VALOR R$`
- `VALOR RS`
- `MUNICÍPIO`
- `CIDADE`
- `ANO DE REFERÊNCIA`
- `ANO DE REFÊRENCIA`

## Como instalar o projeto

Clone o repositório:

```bash
git clone URL_DO_REPOSITORIO
cd NOME_DO_REPOSITORIO
