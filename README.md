# SimpleRequirements

SimpleRequirements makes it even easier to combine CSS and JavaScript files with SilverStripe.

## Install

Copy the SimpleRequirements Module to your project root. All paths are relative to the current theme and the sub-folder `css/js` for each file type.

You can change the folder name by adding this to your `_config.php`

	SimpleRequirements::$folder_name_css = 'css-folder';
	SimpleRequirements::$folder_name_javascript = 'javascript-folder';

If you want to add a file that doesn't exist in your theme directory just add trailing slash at the beginning of the path and it is relative to the root directory.

	SimpleRequirement::css(array(
		'/sapphire/thirdparty/jquery/jquery.js'
	));

### Note

Like the build-in requirements they are combined only in `Director::set_environment_type('live');`.

## Variables

	$folder_name_css = 'css';
	$folder_name_javascript = 'js';

	$default_css = array();
	$default_javascript = array();

	$minify_css_on_flush = true;


## Examples

### Base 

If you want to add files on any page, you can define them in your `_config.php` and add to `Page_Controller.php`.

The following example will combine the default files to `base.min.css` and `base.min.js`

**_config.php**

	SimpleRequirements::$default_css = array(
		'reset.css',
		'base.css'
		…
	);

	SimpleRequirements::$default_javascript = array(
		'jquery.js',
		'base.js'
		…
	);

**Page_Controller.php**

	function init() {
		SimpleRequirements::css('default', 'base');
		SimpleRequirements::javascript('default', 'base');

		parent::init();
	}

### Module

Once you created a new module, in this case a video page, you can add the files as follows to create `video.min.css` and `video.min.js`:

**VideoPage_Controller.php**

	function init() {
		SimpleRequirements::css(array(
			'video-page.css',
			'video-player.css'
		), 'video');

		SimpleRequirements::css(array(
			'video-page.js',
			'video-player.js'
		), 'video');
		ma
		parent::init();
	}

## Have fun!