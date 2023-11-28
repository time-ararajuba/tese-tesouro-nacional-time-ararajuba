// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// Smart Contract do Título Tokenizado do Tesouro
contract TituloTokenizadoDoTesouro {

    // Estrutura de Dados para Armazenar Informações do Título
    struct TituloInfo {
        string programa;
        string portaria;
        string titulo;
        uint256 dataEmissao;
        uint256 dataVencimento;
        uint256 quantidade;
        uint256 preco;
        uint256 valorFinanceiro;
        uint256 aberturaContabil;
        bool liquidadoAntesDoPrazo;
        bool verificado;
    }

    // Mapeamento de Identificadores de Títulos para suas Informações
    mapping(uint256 => TituloInfo) public titulos;

    // Evento emitido quando um título é emitido
    event TituloEmitido(uint256 id, string programa, string portaria, string titulo);

    // Função para Emitir um Novo Título
    function emitirTitulo(
        uint256 id,
        string memory programa,
        string memory portaria,
        string memory titulo,
        uint256 dataEmissao,
        uint256 dataVencimento,
        uint256 quantidade,
        uint256 preco
    ) external {
        // Cria uma nova instância de Título
        TituloInfo storage novoTitulo = titulos[id];

        // Preenche as informações do Título
        novoTitulo.programa = programa;
        novoTitulo.portaria = portaria;
        novoTitulo.titulo = titulo;
        novoTitulo.dataEmissao = dataEmissao;
        novoTitulo.dataVencimento = dataVencimento;
        novoTitulo.quantidade = quantidade;
        novoTitulo.preco = preco;
        novoTitulo.valorFinanceiro = quantidade * preco;
        novoTitulo.aberturaContabil = block.timestamp; // Pode ser substituído pelo método correto.
        novoTitulo.liquidadoAntesDoPrazo = false;
        novoTitulo.verificado = false;

        // Emite o evento de emissão
        emit TituloEmitido(id, programa, portaria, titulo);
    }

    // Função para Liquidar um Título Antes do Prazo
    function liquidarAntesDoPrazo(uint256 id) external {
        require(!titulos[id].liquidadoAntesDoPrazo, "Título já liquidado antes do prazo");
        titulos[id].liquidadoAntesDoPrazo = true;
    }

    // Função para Verificar o Título (Será chamada pelo Token de Verificação)
    function verificarTitulo(uint256 id) external {
        titulos[id].verificado = true;
    }
}
