<script>
	import { page } from '$app/stores';

	/** @type {{title: string, description: string, keywords: string}} */
	let { keywords, description, title } = $props();
	let url = $derived($page.url.href);
	let siteName = 'Password Generator';
	let baseUrl = $derived($page.url.origin);
</script>

<svelte:head>
	<title>{title}</title>

	<meta name="description" content={description} />
	<meta name="keywords" content={keywords} />

	<meta name="robots" content="index, follow" />
	<meta property="og:locale" content="en_US" />

	<meta property="og:title" content={title} />
	<meta property="og:description" content={description} />
	<meta property="og:url" content={url} />
	<meta property="og:type" content="website" />
	<meta property="og:site_name" content={siteName} />
	<meta property="og:image" content="{baseUrl}/logos/pw-generator.svg" />

	<meta name="twitter:card" content="summary" />
	<meta name="twitter:title" content={title} />
	<meta name="twitter:description" content={description} />
	<meta name="twitter:image" content="{baseUrl}/logos/pw-generator.svg" />

	<script type="application/ld+json">
        {JSON.stringify({
            "@context": "http://schema.org",
            "@type": "WebSite",
            "name": "Password Generator",
            "description": "Generate strong passwords with our easy-to-use password generator.",
            "url": url,
            "potentialAction": {
                "@type": "SearchAction",
                "target": {
                    "@type": "EntryPoint",
                    "urlTemplate": `${url}/posts?q={search_term_string}`
                },
                "query-input": "required name=search_term_string"
            }
        })}
	</script>
</svelte:head>
