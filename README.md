# wpaddons-io-sdk

wpAddons is a new arena where you can promote extensions and addons built for WordPress plugins.

## Initializing the SDK

Copy the code below and paste it into the top of your main plugin's PHP file:

```php
/**
 * Addons Class
 *
 * A general class for addons page.
 *
 * @since 1.0
 */
function give_addons() {

	// Set addon parameters
	$plugin_data = array(
		'parant_plugin_slug'     => '',
		'parant_admin_page_slug' => '',
		'admin_page_slug'        => '',
		'admin_page_title'       => '',
		'menu_title'             => '',
		'menu_title_color'       => '',
		'view'                   => '',
		'debug_mode'             => '',
	);

	// Load wpAddons SDK
	require_once plugin_dir_path( __FILE__ ) . '/wpaddons-io-sdk/wpaddons-io-sdk.php';

	// Initiate addons
	if ( class_exists( 'wpAddons' ) ) {
		new wpAddons( $plugin_data );
	}

}
add_action( 'plugins_loaded', 'give_addons' );
```
### Arguments

* parant_plugin_slug - 
* parant_admin_page_slug - 
* admin_page_slug - 
* admin_page_title - 
* menu_title - 
* menu_title_color - 
* view - 
* debug_mode - 

## Usage example

Addons page for [GiveWP](https://GiveWP.com) :

```php
/**
 * Addons Class
 *
 * A general class for addons page.
 *
 * @since 1.0
 */
function give_addons() {

	// Set addon parameters
	$plugin_data = array(
		'parant_plugin_slug'     => 'give',
		'parant_admin_page_slug' => 'edit.php?post_type=give_forms',
		'admin_page_slug'        => 'give_custom_addons',
		'admin_page_title'       => esc_html__( 'Give Add-ons', 'text_domain' ),
		'menu_title'             => esc_html__( 'Add-ons', 'text_domain' ),
		'view'                   => plugin_dir_path( __FILE__ ) . 'wpaddons-io-sdk/view/cover-grid-quarter.php',
	);

	// Load wpAddons SDK
	require_once plugin_dir_path( __FILE__ ) . '/wpaddons-io-sdk/wpaddons-io-sdk.php';

	// Initiate addons
	if ( class_exists( 'wpAddons' ) ) {
		new wpAddons( $plugin_data );
	}

}
add_action( 'plugins_loaded', 'give_addons' );

function give_before_addons() {
	printf(
		'<p>%s</p>',
		esc_html__( 'The following Add-ons extend the functionality of Give.', 'text_domain' )
	);
}
add_action( 'give_below_title', 'give_before_addons' );
```

Addons page for [Timeline Express](http://www.wp-timelineexpress.com/) :

```php
/**
 * Addons Class
 *
 * A general class for addons page.
 *
 * @since 1.0
 */
function timeline_express_addons() {

	// Set addon parameters
	$plugin_data = array(
		'parant_plugin_slug'     => 'timeline-express',
		'parant_admin_page_slug' => 'edit.php?post_type=te_announcements',
		'admin_page_slug'        => 'te_addons',
		'admin_page_title'       => esc_html__( 'Timeline Express Add-Ons', 'text_domain' ),
		'menu_title'             => esc_html__( 'Add-Ons', 'text_domain' ),
		'menu_title_color'       => '#F7A933',
		'view'                   => plugin_dir_path( __FILE__ ) . 'wpaddons-io-sdk/view/icon-grid-half.php',
	);

	// Load wpAddons SDK
	require_once plugin_dir_path( __FILE__ ) . '/wpaddons-io-sdk/wpaddons-io-sdk.php';

	// Initiate addons
	if ( class_exists( 'wpAddons' ) ) {
		new wpAddons( $plugin_data );
	}

}
add_action( 'plugins_loaded', 'timeline_express_addons' );

function timeline_express_before_addons() {
	printf(
		'<p>%s</p>',
		esc_html__( 'Extend the base Timeline Express functionality with our powerful add-ons. We\'re constantly looking to build out additional add-ons. If you have a great idea for a new add-on, get in contact with us!', 'text_domain' )
	);
}
add_action( 'timeline-express_below_title', 'timeline_express_before_addons' );
```

Addons page for [WP Job Manager](https://wpjobmanager.com/) :

```php
/**
 * Addons Class
 *
 * A general class for addons page.
 *
 * @since 1.0
 */
function wp_job_manager_addons() {

	// Set addon parameters
	$plugin_data = array(
		'parant_plugin_slug'     => 'wp-job-manager',
		'parant_admin_page_slug' => 'edit.php?post_type=job_listing',
		'admin_page_slug'        => 'wp-job-manager-addons',
		'admin_page_title'       => esc_html__( 'WP Job Manager Add-ons', 'text_domain' ),
		'menu_title'             => esc_html__( 'Add-ons', 'text_domain' ),
		'view'                   => plugin_dir_path( __FILE__ ) . 'wpaddons-io-sdk/view/cover-grid-quarter.php',
	);

	// Load wpAddons SDK
	require_once plugin_dir_path( __FILE__ ) . '/wpaddons-io-sdk/wpaddons-io-sdk.php';

	// Initiate addons
	if ( class_exists( 'wpAddons' ) ) {
		new wpAddons( $plugin_data );
	}

}
add_action( 'plugins_loaded', 'wp_job_manager_addons' );

function wp_job_manager_before_addons() {
	?>
	<div id="job-manager-addons-banner" class="wp-filter">
		<p style="text-align: right;">
			<strong style="float: left; padding-top: 0.5em;"><?php esc_html_e( 'Do you need multiple add-ons?', 'text_domain' ); ?></strong> 
			<a href="https://wpjobmanager.com/add-ons/bundle/" class="button"><?php esc_html_e( 'Check out the core add-on bundle →', 'text_domain' ); ?></a>
		</p>
	</div>
	<?php
}
add_action( 'wp-job-manager_below_title', 'wp_job_manager_before_addons' );
```
