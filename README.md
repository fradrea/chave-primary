# chave-primary
Estrutura-banco-de-dados-Hospital
-- MySQL Workbench Forward Engineering

SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION';

-- -----------------------------------------------------
-- Schema Atividade_1MySQL
-- -----------------------------------------------------

-- -----------------------------------------------------
-- Schema Atividade_1MySQL
-- -----------------------------------------------------
CREATE SCHEMA IF NOT EXISTS `Atividade_1MySQL` DEFAULT CHARACTER SET utf8 ;
-- -----------------------------------------------------
-- Schema hospital
-- -----------------------------------------------------

-- -----------------------------------------------------
-- Schema hospital
-- -----------------------------------------------------
CREATE SCHEMA IF NOT EXISTS `hospital` DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci ;
USE `Atividade_1MySQL` ;

-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Medico`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Medico` (
  `idMedica` INT NOT NULL AUTO_INCREMENT,
  `CRM` INT NOT NULL,
  `idEspecialista` INT NOT NULL,
  `Nacionalidade` VARCHAR(20) NOT NULL,
  `Estado` VARCHAR(20) NOT NULL,
  `Endereco` VARCHAR(45) NOT NULL,
  `Nascimento` DATE NOT NULL,
  `Telefone` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`idMedica`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Especialidades`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Especialidades` (
  `idEspecialidades` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`idEspecialidades`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Convenios`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Convenios` (
  `idConvenios` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(45) NOT NULL,
  `CNPJ` INT NOT NULL,
  `numero_Carterinha` INT NOT NULL,
  `Carencia` DATE NOT NULL,
  PRIMARY KEY (`idConvenios`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Receitas`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Receitas` (
  `idReceitas` INT NOT NULL AUTO_INCREMENT,
  `Medicamentos` VARCHAR(45) NOT NULL,
  `Quantidade_Medicamento` INT NOT NULL,
  `bula_de_remedio` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`idReceitas`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Paciente`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Paciente` (
  `idPaciente` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(255) NOT NULL,
  `nascimento` DATE NOT NULL,
  `CPF` VARCHAR(11) NOT NULL,
  `RG` VARCHAR(45) NOT NULL,
  `telefone` VARCHAR(45) NOT NULL,
  `EMAIL` VARCHAR(255) NOT NULL,
  `Endereco` VARCHAR(255) NOT NULL,
  `Receitas` INT NOT NULL,
  `Convenio` INT NOT NULL,
  PRIMARY KEY (`idPaciente`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Colsultas`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Colsultas` (
  `idColsultas` INT NOT NULL AUTO_INCREMENT,
  `dataHora` DATETIME NOT NULL,
  `valor` INT NOT NULL,
  `idPaciente` INT NOT NULL,
  `idMedica` INT NOT NULL,
  `idConvenios` INT NOT NULL,
  `idEspecialidades` INT NOT NULL,
  PRIMARY KEY (`idColsultas`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Tipo_quarto`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Tipo_quarto` (
  `idTipo_quarto` INT NOT NULL AUTO_INCREMENT,
  `descricao` VARCHAR(45) NOT NULL,
  `Valor_diaria` DECIMAL(65) NOT NULL,
  PRIMARY KEY (`idTipo_quarto`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Quarto`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Quarto` (
  `idQuarto` INT NOT NULL AUTO_INCREMENT,
  `numero` INT NOT NULL,
  `tipo` VARCHAR(45) NOT NULL,
  `tipo_quarto_id_` INT NOT NULL,
  PRIMARY KEY (`idQuarto`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Internacao`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Internacao` (
  `idInternacao` INT NOT NULL AUTO_INCREMENT,
  `data_entrada` DATE NOT NULL,
  `data_prev_alta` DATE NOT NULL,
  `data_alta` DATE NOT NULL,
  `procedimento` VARCHAR(255) NOT NULL,
  `Medica_id` INT NOT NULL,
  `quarto_id` INT NOT NULL,
  PRIMARY KEY (`idInternacao`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Medico_Especialidades`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Medico_Especialidades` (
  `Especialidades_id` INT NOT NULL AUTO_INCREMENT,
  `idMedica_Especialidades` INT NOT NULL,
  `Medica_id` INT NOT NULL,
  PRIMARY KEY (`idMedica_Especialidades`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Enfermeiro`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Enfermeiro` (
  `idEnfermeiro` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(45) NOT NULL,
  `cpf` VARCHAR(11) NOT NULL,
  `cre` VARCHAR(10) NOT NULL,
  PRIMARY KEY (`idEnfermeiro`))
ENGINE = InnoDB;


-- -----------------------------------------------------
-- Table `Atividade_1MySQL`.`Internacao_Enfermeiro`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `Atividade_1MySQL`.`Internacao_Enfermeiro` (
  `idInternacao_Enfermeiro` INT NOT NULL AUTO_INCREMENT,
  `Infermeiro_id` INT NOT NULL,
  `Internacao_id` INT NOT NULL,
  PRIMARY KEY (`idInternacao_Enfermeiro`))
ENGINE = InnoDB;

USE `hospital` ;

-- -----------------------------------------------------
-- Table `hospital`.`consultas`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`consultas` (
  `idConsultas` INT NOT NULL AUTO_INCREMENT,
  `dataHora` DATETIME NULL DEFAULT NULL,
  `Valor` INT NULL DEFAULT NULL,
  `idPaciente` INT NULL DEFAULT NULL,
  `idMedica` INT NULL DEFAULT NULL,
  `idConvenios` INT NULL DEFAULT NULL,
  `idEspecialidades` INT NULL DEFAULT NULL,
  PRIMARY KEY (`idConsultas`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`convenios`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`convenios` (
  `idConvenios` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(45) NOT NULL,
  `cnpj` INT NOT NULL,
  `numero_carterinha` INT NOT NULL,
  `carencia` DATE NOT NULL,
  PRIMARY KEY (`idConvenios`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`enfermeiro`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`enfermeiro` (
  `idEnfermeiro` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(45) NOT NULL,
  `cpf` VARCHAR(11) NOT NULL,
  `crea` VARCHAR(10) NOT NULL,
  PRIMARY KEY (`idEnfermeiro`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`especialidades`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`especialidades` (
  `idEspecialidades` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`idEspecialidades`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`internacao`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`internacao` (
  `idInternacao` INT NOT NULL AUTO_INCREMENT,
  `data_entrada` DATE NOT NULL,
  `data_prev_alta` DATE NOT NULL,
  `data_alta` DATE NOT NULL,
  `procedimento` VARCHAR(200) NULL DEFAULT NULL,
  `medica_id` INT NOT NULL,
  `quarto_id` INT NOT NULL,
  PRIMARY KEY (`idInternacao`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`internacao_enfermeiro`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`internacao_enfermeiro` (
  `idInternacao_Enfermeiro` INT NOT NULL AUTO_INCREMENT,
  `enfermeiro_id` INT NOT NULL,
  `internacao_id` INT NOT NULL,
  PRIMARY KEY (`idInternacao_Enfermeiro`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`medico`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`medico` (
  `IdMedica` INT NOT NULL AUTO_INCREMENT,
  `CRM` INT NOT NULL,
  `IdEspecialista` INT NOT NULL,
  `Nacionalidade` VARCHAR(20) NOT NULL,
  `Estado` VARCHAR(20) NOT NULL,
  `Endereco` INT NOT NULL,
  `Nascimento` DATE NOT NULL,
  `Telefone` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`IdMedica`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`medico_especialidades`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`medico_especialidades` (
  `idMedica_Especialidades` INT NOT NULL AUTO_INCREMENT,
  `Medica_id` INT NOT NULL,
  PRIMARY KEY (`idMedica_Especialidades`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`paciente`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`paciente` (
  `idPaciente` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(255) NOT NULL,
  `nascimento` DATE NOT NULL,
  `cpf` VARCHAR(11) NOT NULL,
  `rg` VARCHAR(10) NOT NULL,
  `telefone` VARCHAR(20) NOT NULL,
  `email` VARCHAR(45) NOT NULL,
  `endereco` VARCHAR(200) NULL DEFAULT NULL,
  `receitas` INT NOT NULL,
  `convenios` INT NOT NULL,
  PRIMARY KEY (`idPaciente`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`quarto`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`quarto` (
  `idQuarto` INT NOT NULL AUTO_INCREMENT,
  `numero` INT NOT NULL,
  `tipo` VARCHAR(45) NOT NULL,
  `tipo_quarto_id` INT NOT NULL,
  PRIMARY KEY (`idQuarto`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`receitas`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`receitas` (
  `idReceitas` INT NOT NULL AUTO_INCREMENT,
  `medicamentos` VARCHAR(45) NOT NULL,
  `quantidade_medicamento` INT NOT NULL,
  `bula_de_remedio` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`idReceitas`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


-- -----------------------------------------------------
-- Table `hospital`.`tipo_quarto`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospital`.`tipo_quarto` (
  `idTipo_quarto` INT NOT NULL AUTO_INCREMENT,
  `descricao` VARCHAR(45) NOT NULL,
  `valor_diaria` DECIMAL(65,0) NOT NULL,
  PRIMARY KEY (`idTipo_quarto`))
ENGINE = InnoDB
DEFAULT CHARACTER SET = utf8mb4
COLLATE = utf8mb4_0900_ai_ci;


SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS
