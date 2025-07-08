<script>
	let {
		keywords,
		description,
		title,
		image = '/social-image.png',
		imageAlt = 'PassCraft Password Generator Logo',
		type = 'website'
	} = $props();
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="description" content={description} />
	<meta name="keywords" content={keywords} />
	<meta name="author" content="PassCraft" />

	<!-- SEO Essentials -->
	<meta name="robots" content="index, follow" />
	<link rel="canonical" href="http://localhost:5174/" />

	<!-- Open Graph / Facebook -->
	<meta property="og:locale" content="en_US" />
	<meta property="og:type" content={type} />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />
	<meta property="og:site_name" content="PassCraft - Password Generator" />
	<meta
		property="og:image"
		content={image.startsWith('http') ? image : `http://localhost:5174${image}`}
	/>
	<meta property="og:image:alt" content={imageAlt} />
	<meta property="og:image:width" content="1200" />
	<meta property="og:image:height" content="630" />
	<meta property="og:image:type" content="image/png" />

	<!-- Twitter -->
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content={title} />
	<meta name="twitter:description" content={description} />
	<meta
		name="twitter:image"
		content={image.startsWith('http') ? image : `http://localhost:5174${image}`}
	/>
	<meta name="twitter:image:alt" content={imageAlt} />

	<!-- Additional Meta Tags -->
	<meta name="theme-color" content="#000000" />
	<meta name="msapplication-TileColor" content="#000000" />
</svelte:head>
