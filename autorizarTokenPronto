// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/access/Ownable.sol";

// Contrato de Token Portaria de Emissão de Títulos
contract TokenPortariaEmissaoTitulos is Ownable {

    // Endereço do TokenConfirmacao
    address public contratoTokenConfirmacao;

    // Evento emitido quando um registro é recebido
    event RegistroRecebido(uint256 numeroRegistro, string nomeComprador, string endereco, string email, string documentos);

    modifier apenasTokenConfirmacao() {
        require(msg.sender == contratoTokenConfirmacao, "Somente TokenConfirmacao pode chamar esta função");
        _;
    }

    constructor(address _contratoTokenConfirmacao) {
        contratoTokenConfirmacao = _contratoTokenConfirmacao;
    }

    // Função para autorizar a execução da função tokenPronto no TokenConfirmacao
    function autorizarTokenPronto() external onlyOwner {
        TokenConfirmacao contratoToken = TokenConfirmacao(contratoTokenConfirmacao);
        contratoToken.tokenPronto();
    }

    // Função para receber registros da wallet do custodiante
    function receberRegistro(uint256 numeroRegistro, string memory nomeComprador, string memory endereco, string memory email, string memory documentos) external apenasTokenConfirmacao {
        // Execute a lógica de processamento dos registros aqui
        // Por exemplo, você pode armazenar os registros em uma estrutura de dados ou emiti-los como eventos.

        // Exemplo: armazenar em uma estrutura de dados
        // registros[numeroRegistro] = Registro(nomeComprador, endereco, email, documentos);

        // Emitir o evento de registro recebido
        emit RegistroRecebido(numeroRegistro, nomeComprador, endereco, email, documentos);
    }
}
