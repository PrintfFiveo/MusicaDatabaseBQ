# MusicaDatabaseBQ

# Crie uma table para armazenar músicas.

```
CREATE TABLE IF NOT EXISTS musicas (
id UUID PRIMARY KEY NOT NULL,
nome_musica VARCHAR(55),
caminho_musica VARCHr(255) NOT NULL,
duracao TIMESTAMP NOT NULL,
data_lancamento DATE NOT NULL,
artista VARCHAR(100) NOT NULL REFERENCES musicos(id),
compositor VARCHAR(100) REFERENCES musicos(id),
poster BYTEA,
genero VARCHAR(45) NOT NULL,
)
```
# Crie uma tabela para armazenar os artistas e os compositores
```
CREATE TABLE IF NOT EXISTS musicos (
id UUID PRIMARY KEY NOT NULL,
é_compositor BOOLEAN NOT NULL,
nome VARCHAR(100) NOT NULL,
date_nascimento DATE NOT NULL,
date_morte DATE,
type VARCHAR(45) NOT NULL,
musica_mais_famosa UUID REFERENCES musicas(id),
biography TEXT,
)
```

# Crie uma tabela onde guardaremos os usuários
```
CREATE TABLE IF NOT EXISTS usuarios (
id UUID PRIMARY KEY NOT NULL,
email VARCHAR(100) NOT NULL UNIQUE,
senha VARCHAR(45) NOT NULL,
nome_completo VARCHAR(100) NOT NULL,
idade SERIAL NOT NULL,
genero_preferido VARCHAR(100),
data_criacao DATE NOT NULL,
ultimo_acesso TIMESTAMP NOT NULL,
telefone CHAR(13) NOT NULL,
plano VARCHAR(45) NOT NULL,
)
```

# Exercício 4

Já nas tabelas

# Exercício 5
## Músicas
```
INSERT INTO musicas (id, nome_musica, caminho_musica, duracao, data_lancamento, artista, compositor, genero)
VALUES 
    ('UUID1', 'Música1', '/caminho/para/musica1.mp3', '2024-04-03 03:30:00', '2024-01-01', 'Artista A', 'Compositor1', 'Gênero1'),
    ('UUID2', 'Música2', '/caminho/para/musica2.mp3', '2024-04-03 04:00:00', '2024-02-01', 'Artista B', NULL, 'Gênero 2'),
    ('UUID3', 'Música3', '/caminho/para/musica3.mp3', '2024-04-03 05:00:00', '2024-03-01', 'Artista C', 'Compositor 2', 'Gênero 3');
```
## Musicos
```
INSERT INTO musicos (id, é_compositor, nome, date_nascimento, date_morte, type, musica_mais_famosa, biography)
VALUES 
    ('UUID_A1', FALSE, 'Nome do Artista 1', '1990-01-01', NULL, 'Artista', NULL, 'Biografia do Artista 1'),
    ('UUID_A2', FALSE, 'Nome do Artista 2', '1985-05-15', NULL, 'Artista', NULL, 'Biografia do Artista 2'),
    ('UUID_C1', TRUE, 'Nome do Compositor 1', '1975-03-10', '2020-02-20', 'Compositor', 'UUID_M1', 'Biografia do Compositor 1'),
    ('UUID_C2', TRUE, 'Nome do Compositor 2', '1980-08-20', NULL, 'Compositor', 'UUID_M2', 'Biografia do Compositor 2'),
    ('UUID_C3', TRUE, 'Nome do Compositor 3', '1995-11-25', NULL, 'Compositor', 'UUID_M3', 'Biografia do Compositor 3');
```
## Usuários
```
INSERT INTO usuarios (id, email, senha, nome_completo, idade, genero_preferido, data_criacao, ultimo_acesso, telefone, plano)
VALUES 
    ('UUID_U1', 'usuario1@example.com', 'senha123', 'Usuário 1', 25, 'Rock', '2024-04-03', '2024-04-03 12:00:00', '+1234567890', 'Plano Básico'),
    ('UUID_U2', 'usuario2@example.com', 'senha456', 'Usuário 2', 30, 'Pop', '2024-04-03', '2024-04-03 14:00:00', '+9876543210', 'Plano Premium');
```
