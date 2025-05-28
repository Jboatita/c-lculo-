CREATE TABLE usuarios (
  id SERIAL PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  senha_hash TEXT NOT NULL
);

CREATE TABLE obras (
  id SERIAL PRIMARY KEY,
  usuario_id INTEGER REFERENCES usuarios(id),
  tipo VARCHAR(100),
  area_m2 NUMERIC,
  cidade VARCHAR(100),
  estado CHAR(2),
  data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE materiais (
  id SERIAL PRIMARY KEY,
  nome VARCHAR(100),
  unidade VARCHAR(10),
  consumo_m2 NUMERIC
);

CREATE TABLE precos_materiais (
  id SERIAL PRIMARY KEY,
  material_id INTEGER REFERENCES materiais(id),
  cidade VARCHAR(100),
  estado CHAR(2),
  preco_unitario NUMERIC
);

CREATE TABLE mao_obra (
  id SERIAL PRIMARY KEY,
  funcao VARCHAR(100),
  cidade VARCHAR(100),
  estado CHAR(2),
  preco_m2 NUMERIC
);
