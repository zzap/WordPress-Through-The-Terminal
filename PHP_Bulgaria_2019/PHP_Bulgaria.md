# PHP Bulgaria 2019

- Date: 09 November 2019
- URL: https://www.bgphp.org/
- Slides: https://docs.google.com/presentation/d/1kEn1VWgQaEJgcJEeqp1wStxFnTbh3KxAEO3n4Q0sVXo/edit?usp=sharing

## ToC

- [Commands](#commands)
  - [wp eval](#wp-eval)
  - [wp alias](#wp-alias)
  - [wp config](#wp-config)
  - [wp core](#wp-core)
  - [wp scaffold](#wp-scaffold)
  - [wp admin](#wp-admin)
  - [wp plugin](#wp-plugin)
  - [Global parameters](#global-parameters)
  - [Run script](#run-script)
- [Useful Links](#useful-links)
- [Further reading](#further-reading)
- [References](#references)

## Commands

### wp eval

Docs: https://developer.wordpress.org/cli/commands/eval/

```
wp @client eval 'echo wp_login_url() . "\n";'
```

### wp alias

WP-CLI config file needed: `~/.wp-cli/config.yml`.

Docs: https://developer.wordpress.org/cli/commands/alias/

```
wp cli alias add --help
wp cli alias add --prompt
```

### wp config

Docs: https://developer.wordpress.org/cli/commands/config/

```
wp @magic config create --dbname=magic --dbuser=root --prompt=dbpass < www/magic.loc/password.txt
```

### wp core

Docs: https://developer.wordpress.org/cli/commands/core/

```
wp @magic core install --url=http://magic.loc/ --title="WP-CLI at PHP Bulgaria" --admin_user=admin --prompt=admin_password < www/magic.loc/password.txt --admin_email=<email@example.com>
```

### wp scaffold

Docs: https://developer.wordpress.org/cli/commands/scaffold/

```
wp scaffold plugin phpbulgaria --activate
```

```
nano wp-content/plugins/phpbulgaria/phpbulgaria.php
```

```PHP
<?php
/**
 * Plugin Name:     PHP Bulgaria
 * Plugin URI:      PLUGIN SITE HERE
 * Description:     PLUGIN DESCRIPTION HERE
 * Author:          YOUR NAME HERE
 * Author URI:      YOUR SITE HERE
 * Text Domain:     phpbulgaria
 * Domain Path:     /languages
 * Version:         0.1.0
 *
 * @package         Phpbulgaria
 */

// Your code starts here.
function phpbulgaria( $content ) {
return '<h2>' . esc_html__( 'Made at PHP Bulgaria', 'phpbulgaria' ) . '</h2>' . $content;
}
add_filter( 'the_content', 'phpbulgaria' );
```

### wp admin

Docs: https://developer.wordpress.org/cli/commands/admin/

```
wp package install wp-cli/admin-command
```

```
wp admin
```

### wp plugin

Docs: https://developer.wordpress.org/cli/commands/plugin/

```
wp plugin list
```

```
wp plugin activate hello
```

### Global parameters

Docs: https://make.wordpress.org/cli/handbook/config/#global-parameters

```
wp --debug
```

### Run script

Make [wp-custom-install](wp-custom-install) script executable.

```
chmod +x wp-custom-install
```

Move it somewhere in your PATH (user directory `/bin/` is just fine). Check what's in your PATH with `echo $PATH`.

```
mv wp-custom-install ~/bin/wp-custom-install
```

Run it from anywhere.

```
wp-custom-install
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

## References

- "I don't want you to worry about that too much." - Tyler DeWitt, ["Ionization Energy and Atomic Radius"](https://youtu.be/Mmti4kKDcqA?t=14)
