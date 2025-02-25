# Shadow Terms
Contributors: happyprime, jeremyfelt, slocker, philcable, wpgirl369
Tags: terms, related, content
Requires at least: 5.9
Tested up to: 6.6
Stable tag: 1.2.1
License: GPLv2 or later
Requires PHP: 7.4

Use terms from generated taxonomies to associate related content.

## Description

Shadow Terms registers custom (shadow) taxonomies for supported post types. These taxonomies can be used to associate related content from a variety of post types.

When a new post of a supported post type is created, a term mirroring that post is also created. When editing another post type that supports this taxonomy, this term can be assigned to associate the posts.

Shadow Terms does not register support for itself on any post types by default. Custom code must be added to a plugin or theme.

Support can be added to a custom post type with code like:

	<?php
	// Register the organization post type normally.
	register_post_type( 'organization', $args );

	// Add support for Shadow Terms to the organization post type.
	add_post_type_support(
		'organization',
		'shadow-terms',
		array(
			// Add post types that support the organization_connect taxonomy.
			'person',
			'press-release',
		)
	);

With the example above, whenever an `organization` is created, a term with the same name will be created under the `organization_connect` taxonomy. When a person or press release is edited, that term will be available for assignment through standard WordPress taxonomy interfaces.

Code can then be written to query and display all people or press releases related to an organization.

## Changelog

### 1.2.1

* No functional changes.
* Exclude phpstan config from distribution.
* Update development dependencies.
* Confirm WordPress 6.6 support.

### 1.2.0

* Do not show "Add New" term option for shadow taxonomies, which are automatically managed. Thanks [@s3rgiosan](https://profiles.wordpress.org/s3rgiosan/)!
* Do not show shadow terms in REST API to unauthenticated users if their original post type is not publicly available via REST endpoint.

### 1.1.0

* Add filtering to shadow taxonomy taxonomy arguments.
* Update development tooling.

### 1.0.1

* Fix: Ensure term and post slugs sync properly on post update.

### 1.0.0

Initial release.
