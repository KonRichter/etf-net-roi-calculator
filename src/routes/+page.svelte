<script>
	import Logo from '$lib/EFF Net.svg';

	let capital = 1000;
	let years = 1;
	let interest = 0;
	let inflation = 0;
	let tax = 0;
	let netIncome = 0;
	let showResult = false;

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
		showResult = true;
	}
</script>

<div
	class="flex min-h-screen flex-col items-center justify-start bg-gradient-to-b from-gray-50 to-gray-100"
>
	<header
		class="sticky top-0 z-10 flex w-full flex-row items-center justify-between bg-white p-4 shadow-md"
	>
		<a href="/" class="flex flex-row items-center justify-start">
			<img src={Logo} alt="A euro currency symbol with stock market curves." class="mr-4 h-14" />
			<h1 class="font-mono text-2xl font-bold tracking-wide text-gray-800">
				ETF Profits 
				<span class="text-lg font-medium">after Tax and Inflation</span>
			</h1>
		</a>
		<div class="hidden space-x-6 md:flex">
			<a href="#calculator" class="font-medium text-gray-700 transition-colors hover:text-[#e64980]"
				>Calculator</a
			>
			<a href="#about" class="font-medium text-gray-700 transition-colors hover:text-[#e64980]"
				>About</a
			>
		</div>
	</header>
	<main class="flex w-full max-w-6xl flex-col items-start justify-start px-4 py-8 md:px-8">
		<section
			id="about"
			class="mt-4 flex w-full flex-col items-start justify-center rounded-xl bg-white p-6 text-gray-800 shadow-sm"
		>
			<h2 class="mb-6 text-2xl font-bold text-gray-800">
				Understanding Your Real Investment Returns
			</h2>
			<details
				class="group mb-4 rounded-lg border border-gray-200 transition-all hover:border-[#e64980]/30"
			>
				<summary
					class="cursor-pointer rounded-lg bg-gray-50 p-4 font-semibold text-gray-800 transition-colors hover:bg-[#e64980]/5"
					>Why should I care about Tax and Inflation?</summary
				>
				<div class="mt-2 ml-3 flex flex-col items-start justify-center gap-y-2 text-gray-800">
					<p>
						Taking into account taxes and inflation gives you a much clearer idea about the real
						value of an investment. Especially inflation can eat most of your on-paper returns over
						longer periods of time, leaving you with a bloated amount of money that can buy
						surprisingly few goods and services.
					</p>
					<div class="w-full rounded-lg border-l-4 border-[#e64980] bg-[#e64980]/5 p-5 italic">
						<p>
							Fooling people who don't grasp the full impact of inflation is a quite popular and
							profitable sport in the financial industry. Some examples:
						</p>
						<details
							class="group mt-3 rounded-lg border border-gray-200 transition-all hover:border-[#e64980]/30"
						>
							<summary
								class="cursor-pointer rounded-lg bg-white p-3 font-semibold text-gray-800 transition-colors hover:bg-[#e64980]/5"
								>Example 1: Lifelong private pension</summary
							>
							<div class="flex flex-col items-start justify-center gap-y-2 p-3 text-gray-700">
								<p>
									Rent increase depending on insurance company's profits: Man with shovel doing
									"construction work".
								</p>
								<p>Comes down to the decision: Do you want to buy 11,300€ for 22,000€?</p>
							</div>
						</details>
						<details
							class="group mt-3 rounded-lg border border-gray-200 transition-all hover:border-[#e64980]/30"
						>
							<summary
								class="cursor-pointer rounded-lg bg-white p-3 font-semibold text-gray-800 transition-colors hover:bg-[#e64980]/5"
								>Example 2: Contribution reduction in old age for private health insurance</summary
							>
							<div class="flex flex-col items-start justify-center gap-y-2 p-3 text-gray-700">
								<p>Bad value for money.</p>
								<p>Comes down to the decision: Do you want to buy 11,300€ for 22,000€?</p>
							</div>
						</details>
					</div>

					<p>Financial investments are all about outpacing inflation.</p>
				</div>
			</details>
			<details
				class="group mt-4 rounded-lg border border-gray-200 transition-all hover:border-[#e64980]/30"
			>
				<summary
					class="cursor-pointer rounded-lg bg-gray-50 p-4 font-semibold text-gray-800 transition-colors hover:bg-[#e64980]/5"
					>How does inflation impact financial instruments?</summary
				>
				<div
					class="flex flex-col items-start justify-center gap-y-3 p-4 leading-relaxed text-gray-700"
				>
					<p>
						Inflation erodes the purchasing power of money over time, affecting various financial
						instruments differently:
					</p>
					<ul class="mt-2 grid grid-cols-1 gap-4 md:grid-cols-2">
						<li
							class="rounded-lg border border-gray-200 bg-white p-3 shadow-sm transition-all hover:border-[#e64980]/30"
						>
							<span class="mb-1 block font-semibold text-[#e64980]">Cash and Savings Accounts</span>
							<span
								>Usually the hardest hit by inflation, as interest rates rarely keep pace with
								inflation rates, resulting in negative real returns.</span
							>
						</li>
						<li
							class="rounded-lg border border-gray-200 bg-white p-3 shadow-sm transition-all hover:border-[#e64980]/30"
						>
							<span class="mb-1 block font-semibold text-[#e64980]">Bonds and Fixed Income</span>
							<span
								>Generally vulnerable to inflation as their fixed interest payments become less
								valuable in real terms. Inflation can also lead to higher interest rates, causing
								bond prices to fall.</span
							>
						</li>
						<li
							class="rounded-lg border border-gray-200 bg-white p-3 shadow-sm transition-all hover:border-[#e64980]/30"
						>
							<span class="mb-1 block font-semibold text-[#e64980]">Stocks and Equities</span>
							<span
								>Often considered a partial inflation hedge, as companies can sometimes raise prices
								to offset increased costs, though this varies by industry and economic conditions.</span
							>
						</li>
						<li
							class="rounded-lg border border-gray-200 bg-white p-3 shadow-sm transition-all hover:border-[#e64980]/30"
						>
							<span class="mb-1 block font-semibold text-[#e64980]">Real Estate</span>
							<span
								>Typically performs well during inflationary periods as property values and rental
								income tend to rise with inflation.</span
							>
						</li>
						<li
							class="rounded-lg border border-gray-200 bg-white p-3 shadow-sm transition-all hover:border-[#e64980]/30"
						>
							<span class="mb-1 block font-semibold text-[#e64980]">Commodities</span>
							<span
								>Often move in tandem with inflation, as rising prices for goods and services
								reflect directly in commodity prices.</span
							>
						</li>
					</ul>
					<div class="mt-4 rounded-lg border-l-4 border-[#e64980] bg-gray-50 p-4">
						<p class="text-gray-800">
							<span class="font-bold">Key Insight:</span> When evaluating investment returns, the
							<span class="font-semibold">real rate of return</span> (nominal return minus inflation
							rate) provides a more accurate picture of your actual purchasing power gains or losses.
						</p>
					</div>
				</div>
			</details>
			<details
				class="group mt-4 rounded-lg border border-gray-200 transition-all hover:border-[#e64980]/30"
			>
				<summary
					class="cursor-pointer rounded-lg bg-gray-50 p-4 font-semibold text-gray-800 transition-colors hover:bg-[#e64980]/5"
					>What assumptions are made?</summary
				>
				<div
					class="flex flex-col items-start justify-center gap-y-3 p-4 leading-relaxed text-gray-700"
				>
					<p>
						The calculation is based on a German perspective, meaning the currency is EUR
						(investments in USD are converted based on the EUR/USD exchange rate), tax estimates
						comply with German law, and the default inflation values are derived from the <a
							href="https://www.destatis.de/DE/Themen/Wirtschaft/Preise/Verbraucherpreisindex/_inhalt.html"
							class="text-blue-700 underline decoration-blue-700">German Consumer Price Index.</a
						> Also, for now it only covers certain popular ETFs.
					</p>

					<p
						class="mt-2 rounded-lg border border-gray-200 bg-gray-50 p-4 text-sm text-gray-700 italic"
					>
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
		<section
			id="calculator"
			class="mt-12 flex w-full max-w-4xl flex-col items-center justify-center self-center rounded-xl bg-white p-6 shadow-sm"
		>
			<div class="mb-6 flex w-full flex-row items-center justify-start">
				<h2 class="text-2xl font-bold text-gray-800">
					<span class="text-[#e64980]">Berechnen</span> Sie Ihr reales Vermögen nach Steuern und Inflation
				</h2>
			</div>
			<div class="flex w-full flex-col items-start justify-start space-y-2 py-3">
				<div
					class="flex w-full flex-col items-start justify-start rounded-lg border border-gray-100 bg-gray-50 p-4 transition-all hover:border-[#e64980]/30"
				>
					<div class="mb-2 flex w-full items-center justify-between">
						<label for="investment" class="font-medium text-gray-800"> Kapital </label>
						<span class="font-bold text-[#e64980]">{capital.toLocaleString('de-DE')}€</span>
					</div>
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
				<div
					class="flex w-full flex-col items-start justify-start rounded-lg border border-gray-100 bg-gray-50 p-4 transition-all hover:border-[#e64980]/30"
				>
					<div class="mb-2 flex w-full items-center justify-between">
						<label for="years" class="font-medium text-gray-800"> Jahre </label>
						<span class="font-bold text-[#e64980]">{years}</span>
					</div>
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
				<div
					class="flex w-full flex-col items-start justify-start rounded-lg border border-gray-100 bg-gray-50 p-4 transition-all hover:border-[#e64980]/30"
				>
					<div class="mb-2 flex w-full items-center justify-between">
						<label for="interest" class="font-medium text-gray-800"> Jährlicher Zinssatz </label>
						<span class="font-bold text-[#e64980]">{interest}%</span>
					</div>
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
				<div
					class="flex w-full flex-col items-start justify-start rounded-lg border border-gray-100 bg-gray-50 p-4 transition-all hover:border-[#e64980]/30"
				>
					<div class="mb-2 flex w-full items-center justify-between">
						<label for="inflation" class="font-medium text-gray-800"> Inflation </label>
						<span class="font-bold text-[#e64980]">{inflation}%</span>
					</div>
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
				<div
					class="flex w-full flex-col items-start justify-start rounded-lg border border-gray-100 bg-gray-50 p-4 transition-all hover:border-[#e64980]/30"
				>
					<div class="mb-2 flex w-full items-center justify-between">
						<label for="tax" class="font-medium text-gray-800"> Steuersatz </label>
						<span class="font-bold text-[#e64980]">{tax}%</span>
					</div>
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
				<div class="mt-6 flex w-full flex-col items-start justify-start p-3">
					<button
						class="focus:ring-opacity-50 w-full cursor-pointer rounded-lg bg-[#e64980] p-3 text-lg font-medium text-white shadow-sm transition-colors hover:bg-[#d43871] focus:ring-2 focus:ring-[#e64980] focus:outline-none"
						onclick={calculateIncome}>Berechnen</button
					>
				</div>
			</div>
			{#if showResult}
				<div class="mt-8 w-full rounded-xl border-l-4 border-[#e64980] bg-gray-50 p-6 shadow-sm">
					<h3 class="mb-2 text-xl font-bold text-gray-800">Ihr Ergebnis</h3>
					<div class="flex flex-col gap-2 md:flex-row md:items-baseline">
						<span class="text-gray-700">Netto Vermögen nach {years} Jahren:</span>
						<span class="text-2xl font-bold text-[#e64980]"
							>{netIncome.toLocaleString('de-DE')}€</span
						>
					</div>
					<p class="mt-3 text-sm text-gray-600">
						Dieser Betrag berücksichtigt bereits die Auswirkungen von Inflation ({inflation}%) und
						Steuern ({tax}%).
					</p>
				</div>
			{/if}
		</section>
	</main>
</div>

<style>
	input[type='range']::-webkit-slider-thumb {
		-webkit-appearance: none;
		appearance: none;
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background: #e64980;
		cursor: pointer;
		border: 2px solid white;
		box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
		transition: all 0.2s ease;
	}

	input[type='range']::-webkit-slider-thumb:hover {
		background: #d43871;
		transform: scale(1.1);
	}

	input[type='range']::-moz-range-thumb {
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background: #e64980;
		cursor: pointer;
		border: 2px solid white;
		box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
		transition: all 0.2s ease;
	}

	input[type='range']::-moz-range-thumb:hover {
		background: #d43871;
		transform: scale(1.1);
	}

	input[type='range'] {
		height: 8px;
		background: linear-gradient(to right, #e6498050, #e64980);
		border-radius: 8px;
	}
</style>
