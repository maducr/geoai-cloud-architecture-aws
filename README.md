# GeoAI Cloud Architecture: Pipeline de Processamento Geoespacial na AWS

## 📌 Sobre o Projeto
Este projeto é uma **Prova de Conceito (PoC)** desenvolvida para validar e aplicar de forma prática os princípios fundamentais de Cloud Computing. A arquitetura foca na escalabilidade e segurança de pipelines de **GeoAI**, garantindo que conceitos de alta disponibilidade e isolamento de rede sejam implementados seguindo os padrões de excelência da AWS.

---

## 🏗️ Diagrama da Arquitetura
![GeoAI Architecture Diagram](docs/geoai-cloud-architecture-aws.drawio.png)
*Diagrama desenvolvido no Diagrams.net seguindo os padrões oficiais da AWS.*

---

## 🛠️ Componentes e Definições

### 1. Ingestão e Armazenamento (Data Lake)
* **Amazon S3**: Utilizado como o ponto de entrada para imagens de satélite brutos e arquivos vetoriais (GeoJSON, Shapefiles) devido à sua alta durabilidade e baixo custo.

### 2. Processamento (Engine de GeoAI)
* **Amazon EC2 (Image Processor)**: Instância localizada em uma **Public Subnet** para permitir o download de dados externos. Aqui rodam scripts Python (bibliotecas como Rasterio, Geopandas e GDAL) para processamento e análise.

### 3. Persistência de Dados (Geospatial Database)
* **Amazon RDS (PostgreSQL/PostGIS)**: Banco de dados gerenciado localizado em uma **Private Subnet**. O uso do PostGIS permite consultas espaciais complexas e armazenamento seguro dos dados processados.

---

## 🔒 Segurança e Governança (Fundamentos aplicados)

* **VPC & Subnetting**: Implementação de uma VPC com isolamento total entre camadas públicas e privadas.
* **Alta Disponibilidade**: Distribuição dos recursos em múltiplas **Availability Zones (AZs)** para garantir a resiliência do sistema.
* **NAT Gateway**: Configurado para permitir que o banco de dados (privado) realize atualizações de segurança sem expor um IP público para a internet.
* **IAM (Identity and Access Management)**: Aplicação do princípio de privilégio mínimo para controle de acesso entre os serviços.

---

## 👤 Autora
**Maria Eduarda Rodrigues** - Analista de Dados | Geoprocessamento & Modelagem de Dados.
[LinkedIn](https://www.linkedin.com/in/maducr)