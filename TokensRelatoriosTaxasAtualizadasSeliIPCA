// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

// Contrato de Token com Relatório baseado em Indicadores de Taxas
contract TokenRelatorioTaxas is ERC20, Ownable {

    // Indicadores de Taxas
    uint256 public taxaSelic; // Taxa SELIC em pontos percentuais
    uint256 public taxaIPCA; // Taxa IPCA em pontos percentuais

    // Evento emitido quando as taxas são atualizadas
    event TaxasAtualizadas(uint256 novaTaxaSelic, uint256 novaTaxaIPCA);

    constructor(string memory nomeToken, string memory simboloToken) ERC20(nomeToken, simboloToken) {
        taxaSelic = 2; // Exemplo: Inicializa a Taxa SELIC com 2%
        taxaIPCA = 3;  // Exemplo: Inicializa a Taxa IPCA com 3%
    }

    // Função para atualizar as taxas SELIC e IPCA
    function atualizarTaxas(uint256 novaTaxaSelic, uint256 novaTaxaIPCA) external onlyOwner {
        taxaSelic = novaTaxaSelic;
        taxaIPCA = novaTaxaIPCA;

        emit TaxasAtualizadas(novaTaxaSelic, novaTaxaIPCA);
    }

    // Função para calcular o relatório com base nas taxas
    function gerarRelatorio() external view returns (uint256) {
        // Execute a lógica de cálculo do relatório aqui
        // Por exemplo, você pode usar as taxas para calcular um valor específico.

        // Exemplo: Cálculo básico, apenas para fins ilustrativos
        uint256 saldoTotal = totalSupply();
        uint256 valorRelatorio = (saldoTotal * taxaSelic) / 100 + (saldoTotal * taxaIPCA) / 100;

        return valorRelatorio;
    }
}
