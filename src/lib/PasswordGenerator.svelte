<script>
	let password = '';
	let length = 10;
	let includeUppercase = true;
	let includeLowercase = true;
	let includeNumbers = true;
	let includeSpecialChars = true;

	const generatePassword = () => {
		const uppercaseChars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
		const lowercaseChars = 'abcdefghijklmnopqrstuvwxyz';
		const numberChars = '0123456789';
		const specialChars = '!@#$%^&*()-_+=~';

		let chars = '';
		if (includeUppercase) chars += uppercaseChars;
		if (includeLowercase) chars += lowercaseChars;
		if (includeNumbers) chars += numberChars;
		if (includeSpecialChars) chars += specialChars;

		let generatedPassword = '';
		for (let i = 0; i < length; i++) {
			generatedPassword += chars.charAt(Math.floor(Math.random() * chars.length));
		}
		password = generatedPassword;
	};

	const savePasswordToFile = () => {
		const fileContent = `Generated Password: ${password}`;
		const blob = new Blob([fileContent], { type: 'text/plain' });
		const url = window.URL.createObjectURL(blob);
		const a = document.createElement('a');
		a.href = url;
		a.download = 'generated_password.txt';
		document.body.appendChild(a);
		a.click();
		window.URL.revokeObjectURL(url);
		document.body.removeChild(a);
	};
</script>

<div class="wrapper">
	<h1>Password Generator</h1>

	<hr />

	<label class="number">
		<h3>Password Length</h3>
		:
		<input type="number" bind:value={length} min="4" max="32" />
	</label>

	<label>
		<input type="checkbox" bind:checked={includeUppercase} />
		<em>Uppercase Letters</em>
	</label>

	<label>
		<input type="checkbox" bind:checked={includeLowercase} />
		<em>Lowercase Letters</em>
	</label>

	<label>
		<input type="checkbox" bind:checked={includeNumbers} />
		<em>Numbers</em>
	</label>

	<label>
		<input type="checkbox" bind:checked={includeSpecialChars} />
		<em>Special Characters</em>
	</label>

	<button class="gen" onclick={generatePassword}>Generate Password</button>

	<button class="save" onclick={savePasswordToFile}>Save Password to File</button>

	<h4>your password is:</h4>

	<p class="center"><b>{password}</b></p>
</div>

<style>
	.wrapper {
		background-color: rgb(100, 100, 100);
		color: white;
		border-radius: 10px;
		padding: 1rem;

		& h1 {
			text-align: center;
			font-family: Verdana, Geneva, Tahoma, sans-serif;
			color: #eee;
			font-size: clamp(1.5rem, 2vw, 2rem);
		}

		& hr {
			border: none;
			border-top: 2px solid #ccc;
			margin-inline: auto;
			width: 100%;
		}

		& .number {
			display: flex;
			align-items: center;
			justify-content: space-evenly;
		}

		& .center {
			text-align: center;
			color: white;
		}
		& label {
			display: flex;
			align-items: center;
			gap: 0.5rem;
			margin-left: 1.1rem;
			margin-bottom: 0.5rem;
			letter-spacing: 2px;
			font-family: Verdana, Geneva, Tahoma, sans-serif;
			font-size: 1rem;

			&:first-child {
				margin-bottom: -0.25rem;
				margin-left: 0;

				& input {
					border-radius: 10px;
				}
			}

			&:nth-child(5) {
				margin-bottom: 1rem;
			}
		}

		& b {
			font-size: clamp(1rem, 1.2vw, 1.3rem);
			font-weight: bold;
		}

		& button {
			display: block;
			color: rgb(201, 201, 201);
			border: none;
			border-radius: 5px;
			padding: 10px 24px;
			font-size: clamp(1rem, 1.25vw, 1.15rem);
			font-weight: 800;
			letter-spacing: 1px;
			cursor: pointer;
			text-align: center;
			margin-bottom: 0.5rem;

			&.gen {
				margin-top: 1.75rem;
				background-color: hsl(90, 98%, 23%);
				margin-inline: auto;

				&:hover {
					background: rgb(201, 201, 201);
					color: hsl(90, 98%, 25%);
				}
			}
		}

		& .save {
			font-size: clamp(1rem, 1.25vw, 1.15rem);
			margin-inline: auto;
			background-color: hsl(231, 95%, 29%);
			/* color: white; */

			&:hover {
				background: rgb(201, 201, 201);
				color: hsl(231, 95%, 34%);
			}
		}

		& input[type='number'] {
			width: fit-content;
			padding: 5px;
			font-size: clamp(1rem, 1vw, 1.3rem);
			font-weight: 600;
			letter-spacing: 2px;
			text-align: center;
		}
		& input[type='checkbox'] {
			margin-right: 0.5rem;
			width: clamp(1rem, 1vw, 1.5rem);
			height: clamp(1rem, 1vw, 1.5rem);
			cursor: pointer;
			border-radius: 5px;
		}

		& h4 {
			color: rgb(201, 201, 201);
			letter-spacing: 3px;
			font-family: Verdana, Geneva, Tahoma, sans-serif;

			font-size: clamp(0.9rem, 1vw, 1.1rem);
			font-weight: 100;
			text-align: center;
			margin-bottom: -1rem;
		}

		& p {
			font-family: Verdana, Geneva, Tahoma, sans-serif;
			color: #cac4c4;
		}
	}
</style>
