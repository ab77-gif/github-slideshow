@@ -1,30 +1,22 @@
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">

<title>{% if post.title %}{{ post.title }} | {{ page.title }}{% else %}{{ site.title }}{% endif %}</title>

<meta name="author" content="{{ site.author }}">
<meta name="description" content="{{ site.description }}">

<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<link rel="stylesheet" href="{{ site.baseurl }}/node_modules/reveal.js/css/reveal.css">

<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<link rel="stylesheet" href="{{site.baseurl}}/node_modules/reveal.js/css/reset.css">
<link rel="stylesheet" href="{{site.baseurl}}/node_modules/reveal.js/css/reveal.css">
<link rel="stylesheet" href="{{site.baseurl}}/node_modules/reveal.js/css/theme/moon.css">

<link rel="stylesheet" href="{{ site.baseurl }}/assets/css/style.css">
<!-- jQuery -->
<script src="{{ site.baseurl }}/assets/js/jquery-1.11.1.min.js"></script>
<!-- Theme used for syntax highlighting of code -->
<link rel="stylesheet" href="{{site.baseurl}}/node_modules/reveal.js/lib/css/monokai.css">

<!-- If the query includes 'print-pdf', include the PDF print sheet -->
<!-- Printing and PDF exports -->
<script>
	if( window.location.search.match( /print-pdf/gi ) ) {
		var link = document.createElement( 'link' );
		link.rel = 'stylesheet';
		link.type = 'text/css';
		link.href = '{{ site.baseurl }}/reveal.js/css/print/pdf.css';
		document.getElementsByTagName( 'head' )[0].appendChild( link );
	}
</script>

<!--[if lt IE 9]>
<script src="{{ site.baseurl }}/reveal.js/lib/js/html5shiv.js"></script>
<![endif]-->
	var link = document.createElement( 'link' );
	link.rel = 'stylesheet';
	link.type = 'text/css';
	link.href = window.location.search.match( /print-pdf/gi ) ? 'css/print/pdf.css' : 'node_modules/reveal.js/css/print/paper.css';
	document.getElementsByTagName( 'head' )[0].appendChild( link );
</script> 
 73  _includes/script.html 
@@ -1,57 +1,16 @@
<script src="{{ site.baseurl }}/reveal.js/lib/js/head.min.js"></script>
<script src="{{ site.baseurl }}/reveal.js/js/reveal.js"></script>

<!-- reveal.js init -->
<script>
  var baseUrl = "{{ site.baseurl }}"
  // Full list of configuration options available here:
  // https://github.com/hakimel/reveal.js#configuration
  Reveal.initialize({
    {% if site.reveal %}
    {% for attr in site.reveal %}{{attr[0]}}: {% unless {attr[1]} == false or {attr[1]} == true or {attr[0]} == "width" or {attr[0]} == "height" %}'{{attr[1]}}',{% else %}{{attr[1]}},{% endunless %}
    {% endfor %}
    {% endif %}

    theme: Reveal.getQueryHash().theme, // available themes are in /css/theme
    transition: Reveal.getQueryHash().transition || {% if site.reveal.transition %}'{{ site.reveal.transition }}',{% else %}'default',{% endif %} // default/cube/page/concave/zoom/linear/fade/none

    // Optional libraries used to extend on reveal.js
    dependencies: [
      // Cross-browser shim that fully implements classList - https://github.com/eligrey/classList.js/
      { src: baseUrl + '/reveal.js/lib/js/classList.js', condition: function() { return !document.body.classList; } },

      // Zoom in and out with Alt+click
      { src: baseUrl + '/reveal.js/plugin/zoom-js/zoom.js', async: true },

      // Speaker notes
      { src: baseUrl + '/reveal.js/plugin/notes/notes.js', async: true },

      // Remote control your reveal.js presentation using a touch device
      //{ src: baseUrl + '/reveal.js/plugin/remotes/remotes.js', async: true, condition: function() { return !!document.body.classList; } }
    ]
  });

  {% if site.slideNumber.format and site.slideNumber.format != "none" %}
  // Shows the slide number using default formatting
  Reveal.configure({ slideNumber: true });
  Reveal.configure({ slideNumber: '{{ site.slideNumber.format }}' });
  {% endif %}
</script>
<!-- End reveal.js init -->

<!-- Fontawesome -->
<script type="text/javascript">
  $(document).ready(function() {
    //$("a[href*='youtube.com/']").prepend( $( "<i class='fa fa-youtube-play'>&nbsp;</i>" ) );
    //$("a[href*='vimeo.com/']").prepend( $( "<i class='fa fa-vimeo-square'>&nbsp;</i>" ) );
    //$("a[href$='/download']").prepend( $( "<i class='fa fa-cloud-download'>&nbsp;</i>" ) );
    //$("a.download").prepend( $( "<i class='fa fa-cloud-download'>&nbsp;</i>" ) );
    $("a.external").append( $( "<i class='fa fa-external-link'></i>" ) );
    $("a.twitter").append( $( "<i class='fa fa-twitter'></i>" ) );
    $("a.github").append( $( "<i class='fa fa-github'></i>" ) );
    $("blockquote").prepend( $( "<i class='fa fa-quote-left'></i>" ) );
    $("a.button.lighter").click( function() { $("html.dark").removeClass("dark").addClass("light"); });
    $("a.button.darker").click( function() { $("html.light").removeClass("light").addClass("dark"); });
  });
</script>
<!-- End Fontawesome -->
<script src="{{ site.baseurl }}/node_modules/reveal.js/js/reveal.js"></script>

		<script>
			// More info about config & dependencies:
			// - https://github.com/hakimel/reveal.js#configuration
			// - https://github.com/hakimel/reveal.js#dependencies
			Reveal.initialize({
				hash: true,
				dependencies: [
					{ src: 'node_modules/reveal.js/plugin/markdown/marked.js' },
					{ src: 'node_modules/reveal.js/plugin/markdown/markdown.js' },
					{ src: 'node_modules/reveal.js/plugin/highlight/highlight.js' },
					{ src: 'node_modules/reveal.js/plugin/notes/notes.js', async: true }
				]
			});
		</script>
