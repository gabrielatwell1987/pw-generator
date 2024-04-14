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
		<b>Password Length</b>:
		<input type="number" bind:value={length} min="4" max="32" />
	</label>

	<br /><br />

	<label>
		<input type="checkbox" bind:checked={includeUppercase} />
		<em>Include Uppercase Letters</em>
	</label>

	<label>
		<input type="checkbox" bind:checked={includeLowercase} />
		<em>Include Lowercase Letters</em>
	</label>

	<label>
		<input type="checkbox" bind:checked={includeNumbers} />
		<em>Include Numbers</em>
	</label>

	<label>
		<input type="checkbox" bind:checked={includeSpecialChars} />
		<em>Include Special Characters</em>
	</label>

	<button on:click={generatePassword}>Generate Password</button>
	<button on:click={savePasswordToFile}>Save Password to File</button>

	<p><b>Your generated password:</b></p>
	<p class="center"><b>{password}</b></p>
</div>

<style>
	.wrapper {
		background-color: rgb(46, 46, 45);
		color: white;
		border: 3px solid #4caf50;
		border-radius: 10px;
		padding: 2rem;
	}

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
		margin-bottom: 0.5rem;
		letter-spacing: 2px;
		font-family: Verdana, Geneva, Tahoma, sans-serif;
		font-size: 1rem;
	}

	b {
		font-size: 1.5rem;
	}

	button {
		display: block;
		background-color: #4caf50;
		color: white;
		border: none;
		border-radius: 5px;
		padding: 10px 24px;
		font-size: 1.25rem;
		font-weight: 600;
		letter-spacing: 3px;
		cursor: pointer;
		margin: 1rem 0;
		text-align: center;
	}

	input[type='number'] {
		width: 50px;
		padding: 5px;
		font-size: 1rem;
		font-weight: 600;
		letter-spacing: 2px;
		text-align: center;
	}
</style>
