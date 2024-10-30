<script>
	let list_square_css = [
		"w-#size",
		"p-#size",
		"m-#size",
		"p-#size",
		"bg-#color",
		"text-#color",
		{
			class: "flex",
			subclass: [
				"flex-col"
			]
		},
		{
			class: "border-$sides#size border-#color",
			subclass: [
				"rounded-$modelsize",
			]
		}
	];

	const sizes = ["1", "2", "4", "8", "16"];
	const colors = ["red-500", "blue-500", "green-500", "yellow-500"];
	const modelsizes = ["md", "xl"];
	const sides = ["x-", "y-", ""];

	const randomElement = (arr) => arr[Math.floor(Math.random() * arr.length)];

	const random_square = () => {
		let outString = "";
		const modifiers = [];

		list_square_css.sort(() => Math.random() - 0.5).slice(0, 3).forEach((css_element) => {
			let cssString = "";

			if (typeof css_element === "string") {
				cssString = css_element
					.replace("#size", () => {
						const size = randomElement(sizes);
						modifiers.push(`#size: ${size}`);
						return size;
					})
					.replace("#color", () => {
						const color = randomElement(colors);
						modifiers.push(`#color: ${color}`);
						return color;
					});
			} else if (typeof css_element === "object") {
				cssString = css_element.class
					.replace("#size", () => {
						const size = randomElement(sizes);
						modifiers.push(`#size: ${size}`);
						return size;
					})
					.replace("#color", () => {
						const color = randomElement(colors);
						modifiers.push(`#color: ${color}`);
						return color;
					})
					.replace("$sides", () => {
						const side = randomElement(sides);
						modifiers.push(`$sides: ${side}`);
						return side;
					});

				if (css_element.subclass) {
					cssString += " " + css_element.subclass.map(subclass =>
						subclass.replace("$modelsize", () => {
							const modelsize = randomElement(modelsizes);
							modifiers.push(`$modelsize: ${modelsize}`);
							return modelsize;
						})
					).join(" ");
				}
			}
			outString += cssString + " ";
		});

		console.log("CSS:", outString.trim());
		console.log("Modifiers:", modifiers);

		return {CSS: outString.trim(),Modifiers: modifiers};
	};

	let square = random_square();

	let card = 'w-[100%] h-[50%] bg-gray-200 border-2 border-current rounded-md flex justify-center items-center';
</script>

<span class="flex w-[100%] h-[90%] gap-1 p-1">
	<span class="flex flex-col w-[50%] h-[100%] gap-1">
			<span class={card}>

				<span class={square.CSS}>
					<p>text 1</p>
					<p>text 2</p>
				</span>

				<span class={square.CSS}>
					<p>text 1</p>
					<p>text 2</p>
				</span>

				<span class={square.CSS}>
					text 1
					text 2
				</span>

			</span>
			<span class={card}>



			</span>
	</span>

	<span class="flex flex-col w-[50%] h-[100%] gap-1">
			<span class={card}>

			</span>
			<span class={card}>

			</span>
	</span>
</span>
