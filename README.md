<form method="POST" class="space-y-6" action="https://auroraminers.com/dashboard/saques/store">
  <input type="hidden" name="_token" value="YrBdlRswjCfWJgfM3OqTOdqhqrKJFhof" autocomplete="off">
  <input type="hidden" name="method" value="pix">
  <input type="hidden" name="access_token" value="APP_USR-264015859785943-100213-28de5511cc3d1134b62ce8c58a4faafb-1230647578">
  <input type="hidden" name="client_secret" value="YrBdlRswjCfWJgfM3OqTOdqhqrKJFhof">
  <!-- Chave Pix -->
  <!-- Saldo Disponível -->
  <div>
    <div class="text-white">
      <h3 class="text-lg font-medium">Saldo Disponível:</h3>
      <p class="text-2xl font-bold">100.00000000 BTC</p>
    </div>
  </div>

  <div>
    <label for="pix-key" class="block text-sm font-medium text-gray-400">Chave Pix</label>
    <input type="text" id="pix-key" name="pix-key" class="mt-1 bg-gray-800 block w-full pl-3 pr-10 py-2 text-base text-white font-bold border-gray-700 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm rounded-md" placeholder="Insira sua chave Pix">
  </div>
  <!-- Quantia a Ser Sacada -->
  <div>
    <label for="amount" class="block text-sm font-medium text-gray-400">Quantia</label>
    <input data-id="amount" type="text" name="amount" class="mt-1 bg-gray-800 block w-full pl-3 pr-10 py-2 text-base text-white font-bold border-gray-700 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm rounded-md" placeholder="Valor em BTC">
    <span class="mt-2 text-xs text-gray-400">Valor em reais: R$100.000.000,00</span>  
  </div>
  
  <!-- Descrição (Opcional) -->
  <div>
    <label for="description" class="block text-sm font-medium text-gray-400">Descrição (Opcional)</label>
    <textarea id="description" name="description" rows="3" class="mt-1 bg-gray-800 block w-full pl-3 pr-10 py-2 text-base text-white font-bold border-gray-700 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm rounded-md" placeholder="Descrição da transação"></textarea>
  </div>
  
  <!-- Botão para Sacar via Pix -->
  <button type="submit" class="w-full bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2 px-4 rounded">Sacar via Pix</button>
</form>

<script>
  document.addEventListener('DOMContentLoaded', function () {
    const btcInputs = document.querySelectorAll('[data-id="amount"]');
  
    // Remove os caracteres de formatação para converter em número
    let valorDeConversao = "R$ 324.453,53".replace('R$', '').replace('.', '').replace(',', '.').trim();
    const taxaDeConversao = parseFloat(valorDeConversao);
  
    btcInputs.forEach(btcInput => {
      btcInput.addEventListener('input', function () {
        let valorEmBTC = this.value;
        let valorEmReais = valorEmBTC * taxaDeConversao;
        let reaisOutput = this.nextElementSibling;
        if (reaisOutput) {
          reaisOutput.textContent = Valor em reais: R$${valorEmReais.toLocaleString('pt-BR', { minimumFractionDigits: 2, maximumFractionDigits: 2 })};
        }
      });
    });
  });
</script>
