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

	<button onclick={generatePassword}>Generate Password</button>
	<button class="save" onclick={savePasswordToFile}>Save Password to File</button>

	<h4>your password is:</h4>
	<p class="center"><b>{password}</b></p>
</div>

<style>
	.wrapper {
		background-color: rgb(46, 46, 45);
		color: white;
		border: 3px solid #666;
		border-radius: 10px;
		padding: 2rem;

		.number {
			display: flex;
			align-items: center;
			justify-content: space-evenly;
		}

		.center {
			text-align: center;
		}

		label {
			display: block;
			margin-left: 1.1rem;
			margin-bottom: 0.5rem;
			letter-spacing: 2px;
			font-family: Verdana, Geneva, Tahoma, sans-serif;
			font-size: 1rem;
			display: flex;
			align-items: center;

			&:first-child {
				margin-bottom: -0.25rem;
				margin-left: 0;

				input {
					border-radius: 10px;
				}
			}

			&:nth-child(5) {
				margin-bottom: 1rem;
			}
		}

		b {
			font-size: clamp(1rem, 1.2vw, 1.3rem);
			font-weight: bold;
		}

		button {
			display: block;
			background-color: #028b04;
			color: white;
			border: none;
			border-radius: 5px;
			padding: 10px 24px;
			font-size: clamp(1rem, 1.25vw, 1.15rem);
			font-weight: 800;
			letter-spacing: 1px;
			cursor: pointer;
			text-align: center;
			margin-bottom: 0.5rem;

			&:hover {
				background: white;
				color: #028b04;
			}
		}

		.save {
			font-size: clamp(1rem, 1.25vw, 1.15rem);

			background-color: #0120d3;
			color: white;
		}

		.save:hover {
			background: white;
			color: #1020d3;
		}

		input[type='number'] {
			width: 50px;
			padding: 5px;
			font-size: 1rem;
			font-weight: 600;
			letter-spacing: 2px;
			text-align: center;
		}

		input[type='checkbox'] {
			appearance: none;
			-webkit-appearance: none;
			margin-right: 0.5rem;
			width: 1rem;
			height: 1rem;
			background-color: #ccc;
			cursor: pointer;
			border-radius: 5px;
			border: 2px solid #fff;
		}

		input[type='checkbox']:checked {
			background-color: #028b04;
			border: 2px solid #fff;
		}

		h4 {
			color: #666;
			letter-spacing: 3px;
			font-size: clamp(0.9rem, 1vw, 1.1rem);
			font-weight: 100;
			text-align: center;
			margin-bottom: -1rem;
		}

		p {
			font-family: Verdana, Geneva, Tahoma, sans-serif;
		}
	}
</style>
