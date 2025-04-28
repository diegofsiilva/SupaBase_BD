```
CREATE TABLE alunos(
  id serial primary key,
  nome varchar(50) not null,
  curso varchar(50) not null,
  matricula DATE default current_date
);

CREATE TABLE cursos(
  id serial primary key,
  nome TEXT not null,
  duracao_anos INT
);

CREATE TABLE matriculas (
  id SERIAL PRIMARY KEY,
  nome INT REFERENCES alunos(id) ON DELETE CASCADE,
  curso INT REFERENCES cursos(id) ON DELETE CASCADE,
  data_matricula DATE DEFAULT CURRENT_DATE
);

INSERT INTO alunos(nome, curso, matricula)
VALUES ('Thulio', 'Ciência da Computação', '2025-01-20'),
       ('Antônio', 'Ciência da Computação', '2025-02-22'),
       ('Messias', 'Ciência da Computação', '2025-01-02'),
       ('Gabriel', 'Ciência da Computação', '2025-01-27'),
       ('Hugo', 'ADM Tech', '2025-02-24'),
       ('Max', 'Engenharia da Computação', '2025-01-21'),
       ('Edu soninho', 'Engenharia da Computação', '2025-01-14'),
       ('Livia', 'Sistemas de Informação', '2025-01-23'),
       ('Arielly', 'Engenharia de software', '2025-02-20'),
       ('Rafael', 'Engenharia da Computação', '2025-01-19');

INSERT INTO cursos(nome, duracao_anos)
VALUES ('Adm Tech', '4'),
       ('Sistemas de Informação', '4'),
       ('Engenharia da Computação', '4'),
       ('Ciência da Computação', '4'),
       ('Engenharia da Computação', '4');


SELECT a.nome AS aluno, c.nome AS curso, m.data_matricula
FROM matriculas m
JOIN alunos a ON m.aluno_id = a.id
JOIN cursos c ON m.curso_id = c.id;
```
