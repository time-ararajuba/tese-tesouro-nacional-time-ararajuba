// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

// Contrato de Token Relatório
contract TokenRelatorio is ERC20, Ownable {

    // Endereço do TokenConfirmacao
    address public contratoTokenConfirmacao;

    // Evento emitido quando um log de venda é registrado
    event LogVendaRegistrada(uint256 numeroRegistro, uint256 quantidadeTokens, uint256 valorLiquidado, uint256 dataLiquidacao);

    // Evento emitido quando os tokens são queimados
    event TokensQueimados(uint256 quantidadeTokens, string motivo);

    modifier apenasTokenConfirmacao() {
        require(msg.sender == contratoTokenConfirmacao, "Somente TokenConfirmacao pode chamar esta função");
        _;
    }

    constructor(address _contratoTokenConfirmacao) ERC20("TokenRelatorio", "REL") {
        contratoTokenConfirmacao = _contratoTokenConfirmacao;
    }

    // Função para registrar uma venda e emitir o relatório
    function registrarVenda(uint256 numeroRegistro, uint256 quantidadeTokens, uint256 valorLiquidado, uint256 dataLiquidacao) external apenasTokenConfirmacao {
        // Execute a lógica de processamento da venda aqui
        // Por exemplo, você pode emitir um evento de venda e atualizar os registros.

        // Exemplo: Emitir evento de venda registrada
        emit LogVendaRegistrada(numeroRegistro, quantidadeTokens, valorLiquidado, dataLiquidacao);

        // Atualizar o relatório
        _atualizarRelatorio(quantidadeTokens, valorLiquidado);
    }

    // Função para queimar tokens no vencimento ou antecipadamente
    function queimarTokens(uint256 quantidadeTokens, string memory motivo) external onlyOwner {
        // Execute a lógica de queima de tokens aqui
        // Por exemplo, você pode emitir um evento de tokens queimados e destruir os tokens.

        // Exemplo: Emitir evento de tokens queimados
        emit TokensQueimados(quantidadeTokens, motivo);

        // Destruir os tokens
        _burn(owner(), quantidadeTokens);
    }

    // Função interna para atualizar o relatório
    function _atualizarRelatorio(uint256 quantidadeTokens, uint256 valorLiquidado) internal {
        // Execute a lógica de atualização do relatório aqui
        // Por exemplo, você pode armazenar as informações em uma estrutura de dados.

        // Implementação de exemplo: apenas emitir um log interno
        emit LogRelatorioAtualizado(quantidadeTokens, valorLiquidado);
    }

    // Função interna para emitir um log interno
    event LogRelatorioAtualizado(uint256 quantidadeTokens, uint256 valorLiquidado);
}
