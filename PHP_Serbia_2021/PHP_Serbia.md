# PHP Serbia 2021

- Date: 28 August 2021
- URL: https://2020.phpsrbija.rs/
- Slides: https://docs.google.com/presentation/d/1fmucIDugL_n1ZFqlfXtcJp98ESOY_mFG4pQoGSFQwBU/edit?usp=sharing

## ToC

- [Commands](#commands)
  - [wp alias](#wp-alias)
  - [wp core](#wp-core)
  - [wp eval](#wp-eval)
  - [wp admin](#wp-admin)
  - [wp user](#wp-user)
  - [wp plugin](#wp-plugin)
  - [wp scaffold](#wp-scaffold)
  - [Global parameters](#global-parameters)
  - [Run script](#run-script)
- [Useful Links](#useful-links)
- [Further reading](#further-reading)

## Commands

### wp alias

WP-CLI config file needed: `~/.wp-cli/config.yml`.

Docs: https://developer.wordpress.org/cli/commands/alias/

```
wp cli alias list
```

### wp core

Docs: https://developer.wordpress.org/cli/commands/core/

```
wp @client core version
wp @client core update
```

### wp eval

Docs: https://developer.wordpress.org/cli/commands/eval/

```
wp @client eval 'echo wp_login_url() . "\n";'
```

### wp admin

Docs: https://developer.wordpress.org/cli/commands/admin/

This command needs to be installed first.

```
wp package install wp-cli/admin-command
```

```
wp admin
```

### wp user

Docs: https://developer.wordpress.org/cli/commands/user/
User roles and capabilities: https://wordpress.org/support/article/roles-and-capabilities/

```
wp user list
wp user create --prompt
wp user remove-role <ID|username|user email>
wp user add-cap <ID|username|user email> manage_categories
wp user add-cap <ID|username|user email> switch_themes
wp user add-cap <ID|username|user email> activate_plugins
wp user add-cap <ID|username|user email> edit_theme_options
```

### wp plugin

Docs: https://developer.wordpress.org/cli/commands/plugin/
Simple History plugin: https://wordpress.org/plugins/simple-history/

```
wp plugin install --activate simple-history
wp simple-history list
```

### wp scaffold

Docs: https://developer.wordpress.org/cli/commands/scaffold/

```
wp scaffold plugin --prompt
```

```
nano wp-content/plugins/phpserbia/phpserbia.php
```

```PHP
<?php
/**
 * Plugin Name:     PHPSerbia
 * Plugin URI:      PLUGIN SITE HERE
 * Description:     PLUGIN DESCRIPTION HERE
 * Author:          PHPUG
 * Author URI:      YOUR SITE HERE
 * Text Domain:     phpserbia
 * Domain Path:     /languages
 * Version:         0.1.0
 *
 * @package         Phpserbia
 */

// Your code starts here.
function phpserbia_the_title( $title ) {
  return esc_html__( 'PHP Serbia ', 'phpserbia' ) . $title;
}
add_filter( 'the_title', 'phpserbia_the_title' );
```

### Global parameters

Docs: https://make.wordpress.org/cli/handbook/config/#global-parameters

### Run script

Make [wp-install](wp-install) script executable.

```
chmod +x wp-install
```

Move it somewhere in your PATH (user directory `/bin/` is just fine). Check what's in your PATH with `echo $PATH`.

```
mv wp-install ~/bin/wp-install
```

Run it from anywhere.

```
wp-install
```

## Useful Links

- Install WP-CLI: https://make.wordpress.org/cli/handbook/installing/#recommended-installation
- Set tab completions: https://make.wordpress.org/cli/handbook/installing/#tab-completions
- WP-CLI Config: https://make.wordpress.org/cli/handbook/config/
- Running Commands Remotely: https://make.wordpress.org/cli/handbook/running-commands-remotely/

## Further reading

- WP-CLI Tools: https://make.wordpress.org/cli/handbook/tools/
- Shebang: https://bash.cyberciti.biz/guide/Shebang
- Bash Scripting Tutorial - http://landoflinux.com/linux_bash_scripting_tutorial.html
