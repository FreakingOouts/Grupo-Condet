# Grupo-Condet
Repositório para realização de trabalhos 


BANCO DE DADOS

CRIANDO TABELA ATENDENTE------------------------

CREATE TABLE Atendente (
  	idAtendente int AUTO_INCREMENT Not NULL,
    CpfAtendente char(11) NOT NULL,
    NomeAtendente varchar(30) NOT NULL,
  	SobrenomeAtendente varchar(50) NOT NULL,
    RgAtendente char(9),
  	EnderecoAtendente varchar(100),
  	SalarioAtendente decimal(10,2) NOT NULL,
  	TelefoneAtendente varchar(11) NOT NULL,
    PRIMARY KEY (idAtendente),
  	UNIQUE (idAtendente),
    UNIQUE (CpfAtendente)
);

CRIANDO TABELA PLANOS------------------------------------

CREATE TABLE Plano (
  	idPlano int AUTO_INCREMENT NOT NULL,
    nomePlano VARCHAR(25) NOT NULL,
    PRIMARY KEY (idPlano),
  	UNIQUE(idPlano)
);


CRIANDO TABELA CLIENTE -------------------------------

CREATE TABLE Cliente (
  	idCliente int AUTO_INCREMENT NOT NULL,
    CpfCliente char(11) NOT NULL,
    NomeCliente varchar(30) NOT NULL,
  	SobrenomeCliente varchar(50) NOT NULL,
    RgCliente char(9),
	idPlano int NOT NULL,
  	EnderecoCliente varchar(100),
  	idAtendente int NOT NULL,
  	TelefoneCliente varchar(11) NOT NULL,
    PRIMARY KEY (idCliente),
  	UNIQUE(idCliente),
    UNIQUE (CpfCliente),
  	FOREIGN KEY (idAtendente) REFERENCES Atendente(idAtendente),
	FOREIGN KEY (idPlano) REFERENCES Plano(idPlano) 
);

ALTER TABLE Cliente
ADD FOREIGN KEY (idPlano) REFERENCES Plano(idPlano);

CRIANDO TABELA MANOBRISTA------------------------------

CREATE TABLE Manobrista (
  	idManobrista int AUTO_INCREMENT NOT NULL,
    CnhManobrista CHAR(11) NOT NULL,
    NomeManobrista varchar(30) NOT NULL,
  	SobrenomeManobrista varchar(50) NOT NULL,
    RgManobrista CHAR(9),
  	EnderecoManobrista varchar(100),
  	SalarioManobrista decimal(10,2) NOT NULL,
  	TelefoneManobrista VARCHAR(11) NOT NULL,
    PRIMARY KEY (idManobrista),
  	UNIQUE(idManobrista),
    UNIQUE (CnhManobrista)
);

CRIANDO TABELA DE VAGA----------------------------------

CREATE TABLE Vaga (
  	idVaga int AUTO_INCREMENT NOT NULL,
    NumeroVaga char(2) NOT NULL,    
  	Situacao varchar(15) NOT NULL,
    PRIMARY KEY (idVaga),
  	UNIQUE(idVaga),
    UNIQUE (NumeroVaga)
);

CRIANDO TABELA VEICULO------------------------------------

CREATE TABLE Veiculo (
  	idVeiculo int AUTO_INCREMENT NOT NULL,
    Placa CHAR(7) NOT NULL,
    Cor varchar(15) NOT NULL,
  	Modelo varchar(20) NOT NULL,
    idCliente int,
  	idVaga int,
  	DataHora_Entrada datetime,
  	DataHora_Saida datetime,
  	Valor decimal(10,2),
  	idAtendente int NOT NULL,
  	idPlano int,
    PRIMARY KEY (idVeiculo),
  	UNIQUE(idVeiculo),
    UNIQUE (Placa),
  	FOREIGN KEY (idCliente) REFERENCES Cliente(idCliente),
  	FOREIGN KEY (idVaga) REFERENCES Vaga(idVaga),
  	FOREIGN KEY (idAtendente) REFERENCES Atendente(idAtendente),
	FOREIGN KEY (idPlano) REFERENCES Cliente(idPlano)
);

CRIANDO TABELA USUARIOS------------------------------------

CREATE TABLE Usuarios (
  	idUser int AUTO_INCREMENT NOT NULL,
	Usuario varchar(20) NOT NULL,    
  	Senha varchar(20) NOT NULL,
	Nome varchar(50) NOT NULL,
    Email varchar(50) NULL,
	Telefone varchar(20) NULL,
	PRIMARY KEY (idUser),
  	UNIQUE(idUser),
    UNIQUE (Usuario)
);
