<script>
	import Logo from '$lib/Wholesome ETF Profit.svg';

	let capital = 1000;
	let years = 1;
	let interest = 0;
	let inflation = 0;
	let tax = 0;
	let netIncome = 0;

	function calculateIncome() {
		// Calculate compound interest
		let amount = capital * Math.pow(1 + interest / 100, years);

		// Adjust for inflation
		const realInterestRate = (1 + interest / 100) / (1 + inflation / 100) - 1;
		let realAmount = capital * Math.pow(1 + realInterestRate, years);

		// Apply tax on profits
		const profit = realAmount - capital;
		const taxAmount = profit * (tax / 100);
		netIncome = realAmount - taxAmount;
	}
</script>

<div class="flex flex-col items-center justify-start">
	<header class="flex w-full flex-row items-center justify-start p-3">
		<a href="/" class="flex flex-row items-center justify-start">
			<img src={Logo} alt="A euro currency symbol with stock market curves." class="mr-4 h-12" />
			<h1 class="font-mono text-2xl text-[#0B3487]">ETF Profits after Tax and Inflation</h1>
		</a>
	</header>
	<main class="flex h-screen w-full flex-col items-start justify-start">
		<section class="mt-10 flex flex-col items-start justify-center px-3 text-gray-800">
			<details open>
				<summary class="cursor-pointer font-semibold"
					>Why should I care about Tax and Inflation?</summary
				>
				<div class="mt-2 ml-3 flex flex-col items-start justify-center gap-y-2 text-gray-800">
					<p>
						Taking into account taxes and inflation gives you a much clearer idea about the real
						value of an investment. Especially inflation can eat most of your on-paper returns over
						longer periods of time, leaving you with a bloated amount of money that can buy
						surprisingly few goods and services.
					</p>
					<div class="ml-2 max-w-[1000px] rounded-lg bg-gray-100 p-4 italic">
						<p>
							Fooling people who don't grasp the full impact of inflation is a quite popular and
							profitable sport in the financial industry. Some examples:
						</p>
						<details open>
							<summary class="cursor-pointer font-semibold"
								>Example 1: Lifelong private pension</summary
							>
							<div class="mt-2 ml-3 flex flex-col items-start justify-center gap-y-2 text-gray-800">
								<p>
									Rent increase depending on insurance company's profits: Man with shovel doing
									"construction work".
								</p>
								<p>Comes down to the decision: Do you want to buy 22,000€ for 11,300€?</p>
							</div>
						</details>
						<details open>
							<summary class="cursor-pointer font-semibold"
								>Example 2: Contribution reduction in old age for private health insurance</summary
							>
							<div class="mt-2 ml-3 flex flex-col items-start justify-center gap-y-2 text-gray-700">
								<p>Bad value for money.</p>
								<p>Comes down to the decision: Do you want to buy 22,000€ for 11,300€?</p>
							</div>
						</details>
					</div>

					<p>Financial investments are all about outpacing inflation.</p>
				</div>
			</details>
			<details class="mt-2" open>
				<summary class="cursor-pointer font-semibold">What assumptions are made?</summary>
				<div class=" mt-2 ml-3 text-gray-700">
					<p>
						The calculation is based on a German perspective, meaning the currency is EUR
						(investments in USD are converted based on the EUR/USD exchange rate), tax estimates
						comply with German law, and the default inflation values are derived from the <a
							href="https://www.destatis.de/DE/Themen/Wirtschaft/Preise/Verbraucherpreisindex/_inhalt.html"
							class="text-blue-700 underline decoration-blue-700">German Consumer Price Index.</a
						> Also, for now it only covers certain popular ETFs.
					</p>

					<p class="rounded-lg bg-gray-50 p-4 text-sm text-gray-700 italic">
						<span class="font-bold">Disclaimer: </span> This site provides general financial estimates
						based on user-provided inputs, current tax estimates, legal conditions, and currency exchange
						rates as of March 07, 2025. These estimates are for informational and illustrative purposes
						only and do not constitute personalized financial, legal, or investment advice. Results may
						vary due to changes in tax laws, economic conditions, currency fluctuations, or individual
						circumstances not accounted for by this tool. We make no guarantees regarding the accuracy,
						completeness, or reliability of the calculations, and users rely on this tool at their own
						risk. For tailored advice, please consult a qualified financial advisor, tax professional,
						or legal expert. The creators of this calculator shall not be liable for any decisions, losses,
						or damages arising from its use.
					</p>
				</div>
			</details>
			<!-- <blockquote class="mt-4 rounded-lg bg-gray-50 p-4 text-gray-700 italic">
				"Investing should be more like watching paint dry or watching grass grow. If you want
				excitement, take $800 and go to Las Vegas."
				<footer class="mt-2 text-right text-sm not-italic">— Paul Samuelson</footer>
			</blockquote> -->
		</section>
		<section class="mt-20 flex w-[1000px] flex-col items-center justify-center self-center">
			<div class="flex w-full flex-row items-center justify-start p-3">
				<h2 class="font-mono text-lg text-[#e64980]">
					Jetzt real verfügbares Vermögen (nach Steuern und Inflation) berechnen
				</h2>
			</div>
			<div class="flex w-full flex-col items-start justify-start py-3">
				<div class="flex w-full flex-col items-start justify-start p-3">
					<label for="investment" class="font-mono text-lg text-[#e64980]">
						Kapital: {capital.toLocaleString('de-DE')}€
					</label>
					<input
						type="range"
						id="investment"
						name="investment"
						min="100"
						max="1000000"
						step="100"
						class="h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
						bind:value={capital}
					/>
				</div>
				<div class="flex w-full flex-col items-start justify-start p-3">
					<label for="years" class="font-mono text-lg text-[#e64980]">
						Jahre: {years}
					</label>
					<input
						type="range"
						id="years"
						name="years"
						min="1"
						max="50"
						step="1"
						class="h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
						bind:value={years}
					/>
				</div>
				<div class="flex w-full flex-col items-start justify-start p-3">
					<label for="interest" class="font-mono text-lg text-[#e64980]">
						Jährlicher Zinssatz: {interest}%
					</label>
					<input
						type="range"
						id="interest"
						name="interest"
						min="0"
						max="25"
						step="0.1"
						class="h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
						bind:value={interest}
					/>
				</div>
				<div class="flex w-full flex-col items-start justify-start p-3">
					<label for="inflation" class="font-mono text-lg text-[#e64980]">
						Inflation: {inflation}%
					</label>
					<input
						type="range"
						id="inflation"
						name="inflation"
						min="0"
						max="25"
						step="0.1"
						class="h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
						bind:value={inflation}
					/>
				</div>
				<div class="flex w-full flex-col items-start justify-start p-3">
					<label for="tax" class="font-mono text-lg text-[#e64980]">
						Steuersatz: {tax}%
					</label>
					<input
						type="range"
						id="tax"
						name="tax"
						min="0"
						max="70"
						step="0.1"
						class="h-2 w-full cursor-pointer appearance-none rounded-lg bg-gray-200"
						bind:value={tax}
					/>
				</div>
				<div class="mt-10 flex w-full flex-col items-start justify-start p-3">
					<button
						class="w-full cursor-pointer rounded-lg bg-[#e64980] p-2 font-mono text-lg text-white"
						onclick={calculateIncome}>Berechnen</button
					>
				</div>
			</div>
			<div class="mt-10 flex w-full flex-row items-center justify-start p-3">
				<h2 class="font-mono text-lg text-[#e64980]">
					Dein Netto Vermögen: {netIncome.toLocaleString('de-DE')}€
				</h2>
			</div>
		</section>
	</main>
</div>

<style>
	input[type='range']::-webkit-slider-thumb {
		-webkit-appearance: none;
		appearance: none;
		width: 16px;
		height: 16px;
		border-radius: 50%;
		background: #e64980;
		cursor: pointer;
	}

	input[type='range']::-moz-range-thumb {
		width: 16px;
		height: 16px;
		border-radius: 50%;
		background: #e64980;
		cursor: pointer;
	}
</style>
