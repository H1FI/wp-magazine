# wp-magazine
Template for WordPress Magazines.

## Filters

There are filters to modify the labels and arguments for both the article post type and the issue taxonomy. The recommended naming convention (and filter usage) is this:

    add_filter( 'wpm_article_args', 'my_article_args' );
    function my_article_args($args) {
        $args['rewrite'] = array( 'slug' => 'new-magazine-name/article' );
        return $args;
    }

    add_filter( 'wpm_issue_args', 'my_issue_args' );
    function my_issue_args($args) {
        $args['rewrite'] = array( 'slug' => 'new-magazine-name' );
        return $args;
    }

Remember to flush the permalinks after changing the slugs!

See the documentation for <a href="https://developer.wordpress.org/reference/functions/register_post_type/">register_post_type</a> and <a href="https://developer.wordpress.org/reference/functions/register_taxonomy/">register_taxonomy</a> for all the supported options. There are also separate filters for `wpm_issue_labels` and `wpm_article_labels`. 

If using pretty permalinks (which you should use), the URL's will be formed as follows:

| URL                              | Location                  |
| -------------------------------- | ------------------------- |
| /new-magazine-name/              | (Main) Issue Archive      |
| /new-magazine-name/article-name/ | (Single) Magazine Article |
| /new-magazine-name/2015/         | (Year) Issue Archive      |
| /new-magazine-name/2015-01/       | (Number) Issue Archive    |
