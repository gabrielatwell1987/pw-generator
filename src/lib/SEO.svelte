<script>
	import { page } from '$app/stores';

	/** @type {{title: string, description: string, keywords: string, image?: string, imageAlt?: string, type?: string}} */
	let {
		keywords,
		description,
		title,
		image = '/social-image.png', // Default to social media image, fallback to logo
		imageAlt = 'PassCraft Password Generator Logo',
		type = 'website'
	} = $props();

	let url = $derived($page.url.href);
	let siteName = 'PassCraft - Password Generator';
	let baseUrl = $derived($page.url.origin);
	let canonicalUrl = $derived($page.url.origin + $page.url.pathname);
	// Fallback to SVG logo if social image doesn't exist
	let defaultImage = image === '/social-image.png' ? '/logos/passcraft.svg' : image;
	let fullImageUrl = $derived(
		defaultImage.startsWith('http') ? defaultImage : `${baseUrl}${defaultImage}`
	);
</script>

<svelte:head>
	<title>{title}</title>

	<!-- Canonical URL -->
	<link rel="canonical" href={canonicalUrl} />

	<!-- Basic Meta Tags -->
	<meta name="description" content={description} />
	<meta name="keywords" content={keywords} />
	<meta name="author" content="PassCraft" />

	<!-- Robots and Indexing -->
	<meta name="robots" content="index, follow" />
	<meta name="googlebot" content="index, follow" />

	<!-- Open Graph / Facebook -->
	<meta property="og:locale" content="en_US" />
	<meta property="og:type" content={type} />
	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />
	<meta property="og:url" content={canonicalUrl} />
	<meta property="og:site_name" content={siteName} />
	<meta property="og:image" content={fullImageUrl} />
	<meta property="og:image:alt" content={imageAlt} />
	<meta property="og:image:width" content="1200" />
	<meta property="og:image:height" content="630" />
	<meta property="og:image:type" content="image/svg+xml" />

	<!-- Twitter -->
	<meta name="twitter:card" content="summary_large_image" />
	<meta name="twitter:title" content={title} />
	<meta name="twitter:description" content={description} />
	<meta name="twitter:image" content={fullImageUrl} />
	<meta name="twitter:image:alt" content={imageAlt} />

	<!-- Additional Meta Tags -->
	<meta name="theme-color" content="#000000" />
	<meta name="msapplication-TileColor" content="#000000" />

	<!-- JSON-LD Structured Data -->
	<script type="application/ld+json">
        {JSON.stringify({
            "@context": "https://schema.org",
            "@type": "WebApplication",
            "name": siteName,
            "description": description,
            "url": canonicalUrl,
            "applicationCategory": "UtilityApplication",
            "operatingSystem": "Web Browser",
            "offers": {
                "@type": "Offer",
                "price": "0",
                "priceCurrency": "USD"
            },
            "creator": {
                "@type": "Organization",
                "name": "PassCraft"
            }
        })}
	</script>
</svelte:head>
