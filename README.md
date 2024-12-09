# MapasMunicipios
Seja bem-vindo à coleção de mapas políticos de Minas Gerais do **Centro de Gerenciamento e Análise de Dados** da Polícia Militar de Minas Gerais (PMMG). 

Este ambiente foi criado para compartilhar os mapas políticos dos municípios de Minas Gerais, cada mapa apresenta um município em destaque, basta pesquisar pelo nome. De modo a facilitar o uso das imagens em sistemas, foram suprimidos dos nomes dos municípios as conjunções ("do", "de, "da", etc), bem como acentos gráficos, e espaços entre palavras. Usando como base o nome do município, pode-se utilizar a seguinte função (typescript):

```
private formatarNomeMunicipio(nome: string): string {
  return nome
    .normalize('NFD')                              //Converte caracteres com acentos em suas formas decompostas (Água -> Agua + diacrítico)
    .replace(/[\u0300-\u036f]/g, '')               //Remove os diacríticos gerados pela decomposição na linha anterior (Água -> Agua)
    .split(' ')                                    //Divide o nome em um array de palavras, usando o espaço como delimitador (Juiz de Fora -> ["Juiz", "de", "Fora"]
    .filter((palavra) => /^[A-Z]/.test(palavra))   //Retira todas as palavras que não começam com letra maiúscula (["Juiz", "de", "Fora"] -> ["Juiz", "Fora"])
    .join('');                                     //une as palavras do array em uma única string, sem espaçamentos entre elas (["Juiz", "Fora"] -> ["JuizFora"])
}
```

## 🤝 Contribuições

Contribuições, correções e sugestões são sempre bem-vindas! Caso identifique melhorias ou tenha novas ideias, sinta-se à vontade para abrir uma *issue* ou enviar um *pull request*. Este repositório é um espaço colaborativo, e sua participação é fundamental para torná-lo ainda mais útil e eficiente para todos. 
### Licença

Este projeto está licenciado sob a licença MIT (X11) - veja o arquivo [LICENSE](LICENSE) para detalhes.
