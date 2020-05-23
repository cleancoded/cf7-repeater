=== CF7-Repeater Field ===

Contributors: cleancoded

Requires at least: 4.6

Tested up to: 5.4

Requires PHP: 5.3

Adds repeatable groups of fields to Contact Form 7.

== Description ==

This plugin adds repeatable groups of fields to Contact Form 7.

== Usage ==

= Form tab =

Wrap the desired fields with `[field_group your_group_id_here][/field_group]`. The shortcode accepts additional parameters, in WP shortcode format and in CF7 fields parameters format as well.

Example:
~~~~
[field_group emails id="emails-groups" tabindex:1]
	<label>Your Email (required)[email* your-email]</label>
	[radio your-radio use_label_element default:1 "radio 1" "radio 2" "radio 3"]
	[select* your-menu include_blank "option1" "option 2"]
	[checkbox* your-checkbox "check 1" "check 2"]
[/field_group]
~~~~

= Mail tab =

In the mail settings, wrap the fields with your group id. You can use the `[group_index]` tag to print the group index and an additional `__<NUMBER>` to print a field at a specific index.

Example:
~~~~
The second email entered by the user was: [your-email__2]

These were the groups:
[emails]
GROUP #[group_index]
	Checkbox: [your-checkbox]
	E-mail: [your-email]
	Radio: [your-radio]
	Select: [your-menu]
[/emails]
~~~~

== Customizing the add and remove buttons ==

You can [add filters](https://developer.wordpress.org/reference/functions/add_filter/) to your theme to customize the add and remove buttons.

Example
~~~
// In your theme's functions.php
function customize_add_button_atts( $attributes ) {
  return array_merge( $attributes, array(
    'text' => 'Add Entry',
  ) );
}
add_filter( 'wpcf7_field_group_add_button_atts', 'customize_add_button_atts' );
~~~



== Changelog ==

= 1.1 =

Intial Release