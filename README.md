# Grupo-Condet
Repositório para realização de trabalhos 


# BANCO DE DADOS OASISPARK

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




CREATE TABLE Cliente (
  	idCliente int AUTO_INCREMENT NOT NULL,
    CpfCliente char(11) NOT NULL,
    NomeCliente varchar(30) NOT NULL,
  	SobrenomeCliente varchar(50) NOT NULL,
    RgCliente char(9),
  	EnderecoCliente varchar(100),
  	idAtendente int NOT NULL,
  	TelefoneCliente varchar(11) NOT NULL,
    nomePlano varchar(20) NOT NULL,
    PRIMARY KEY (idCliente),
  	UNIQUE(idCliente),
    UNIQUE (CpfCliente),
  	FOREIGN KEY (idAtendente) REFERENCES Atendente(idAtendente)  	
);

alter table Cliente add column nomePlano varchar(20)
#drop table Cliente


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



CREATE TABLE Vaga (
  	idVaga int AUTO_INCREMENT NOT NULL,
    NumeroVaga char(2) NOT NULL,    
  	Situacao varchar(15) NOT NULL,
    PRIMARY KEY (idVaga),
  	UNIQUE(idVaga),
    UNIQUE (NumeroVaga)
);



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
  	Comprovante varchar(100),
    PRIMARY KEY (idVeiculo),
  	UNIQUE(idVeiculo),
    UNIQUE (Placa),
  	FOREIGN KEY (idCliente) REFERENCES Cliente(idCliente),
  	FOREIGN KEY (idVaga) REFERENCES Vaga(idVaga),
  	FOREIGN KEY (idAtendente) REFERENCES Atendente(idAtendente)
);




CREATE TABLE Ticket (
	idTicket int AUTO_INCREMENT NOT NULL,
  	idVeiculo int NOT NULL,
    Placa CHAR(7) NOT NULL,
    Cor varchar(15) NOT NULL,
  	Modelo varchar(20) NOT NULL,
    idCliente int,
  	idVaga int,
  	DataHora_Entrada datetime,
  	Valor decimal(10,2),
  	idAtendente int NOT NULL,
    PRIMARY KEY (idTicket),
	FOREIGN KEY (idVeiculo) REFERENCES Veiculo(idVeiculo),
  	FOREIGN KEY (idCliente) REFERENCES Cliente(idCliente),
  	FOREIGN KEY (idVaga) REFERENCES Vaga(idVaga),
  	FOREIGN KEY (idAtendente) REFERENCES Atendente(idAtendente)
);




CREATE TABLE Nota_Fiscal (
	idNotaFiscal int AUTO_INCREMENT NOT NULL,
	idTicket int NOT NULL,
  	idVeiculo int NOT NULL,
    Placa CHAR(7) NOT NULL,
    Cor varchar(15) NOT NULL,
  	Modelo varchar(20) NOT NULL,
    idCliente int,
  	idVaga int,
  	DataHora_Entrada datetime,
  	DataHora_Saida datetime,
  	Valor decimal(10,2),
  	idAtendente int NOT NULL,
    PRIMARY KEY (idNotaFiscal),
	FOREIGN KEY (idTicket) REFERENCES Ticket(idTicket),
	FOREIGN KEY (idVeiculo) REFERENCES Veiculo(idVeiculo),
  	FOREIGN KEY (idCliente) REFERENCES Cliente(idCliente),
  	FOREIGN KEY (idVaga) REFERENCES Vaga(idVaga),
  	FOREIGN KEY (idAtendente) REFERENCES Atendente(idAtendente)
);

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
