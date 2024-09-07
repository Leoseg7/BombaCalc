import React, { useState } from 'react';
import './App.css';


function App() {
  const [alcoolPreco, setAlcoolPreco] = useState('');
  const [gasolinaPreco, setGasolinaPreco] = useState('');
  const [MelhorOpcao, setMelhorOpcao] = useState('');

  const handleAlcoolPrecoChange = (event) => {
    setAlcoolPreco(event.target.value);
  }

  const handleGasolinaPrecoChange = (event) => {
    setGasolinaPreco(event.target.value);
  }

  const calculateMelhorOpcao = () => {
    const alcoolPrecoValor = parseFloat(alcoolPreco);
    const gasolinaPrecoValor = parseFloat(gasolinaPreco);

    if (alcoolPrecoValor && gasolinaPrecoValor) {
      const ratio = alcoolPrecoValor / gasolinaPrecoValor;
      if (ratio < 0.7) {
        setMelhorOpcao('Álcool');
      } else {
        setMelhorOpcao('Gasolina');
      }
    } else {
      setMelhorOpcao('Preencha todos os campos');
    }
  };

  return (
    <div className="container">
      <h1>Qual a melhor opção?</h1>
      <img src="./bomba.png" alt=" gasolina" />
      <div className="input-group">
        <label htmlFor="alcool-preco">Alcool (preço por litro):</label>
        <input
          type="number"
          id="alcool-preco"
          value={alcoolPreco}
          onChange={handleAlcoolPrecoChange}
        />
      </div>
      <div className="input-group">
        <label htmlFor="gasolina-preco">Gasolina (preço por litro):</label>
        <input
          type="number"
          id="gasolina-Preco"
          value={gasolinaPreco}
          onChange={handleGasolinaPrecoChange}
        />
      </div>
      <button onClick={calculateMelhorOpcao}>Calcular</button>
      <p>A melhor opção é: {MelhorOpcao}</p>
    </div>
  )
}

export default App;
