# WordCamp Skopje 2019

- Date: 05 October 2019
- URL: https://2019.skopje.wordcamp.org/
- Slides: https://docs.google.com/presentation/d/1fWPZSjvZw6s3U95OwjGWK0cAqSPW28kG4PX_dCwN7Ks/edit?usp=sharing

## ToC

- [Commands](#commands)
  - [wp eval](#wp-eval)
  - [wp db](#wp-db)
  - [wp core](#wp-core)
  - [wp config](#wp-config)
  - [wp admin](#wp-admin)
  - [wp post](#wp-post)
  - [wp user](#wp-user)
  - [wp plugin](#wp-plugin)
  - [wp scaffold](#wp-scaffold)
  - [Global parameters](#global-parameters)
  - [Run script](#run-script)
- [Useful Links](#useful-links)
- [Further reading](#further-reading)
- [References](#references)

## Commands

### wp eval

Docs: https://developer.wordpress.org/cli/commands/eval/

```
wp eval 'echo wp_login_url() . "\n";'
```

```
echo "Login URL is: <url>" | mail -s "Website's Login URL" "<client_email>"
```

### wp db

Docs: https://developer.wordpress.org/cli/commands/db/

```
wp db export
```

### wp core

Docs: https://developer.wordpress.org/cli/commands/core/

```
wp core download
```

```
wp core install
```

### wp config

Docs: https://developer.wordpress.org/cli/commands/config/

```
wp config create --dbname=wpcli --dbuser=root --prompt=dbpass < password.txt
```

### wp admin

Docs: https://developer.wordpress.org/cli/commands/admin/

```
wp package install wp-cli/admin-command
```

```
wp admin
```

### wp post

Docs: https://developer.wordpress.org/cli/commands/post/

```
wp post list
```

```
wp post delete 1
```

```
wp post generate --count=5
```

### wp user

Docs: https://developer.wordpress.org/cli/commands/user/

```
wp user create --prompt
```

```
wp user remove-role 1
```

```
wp user add-cap 2 activate_plugins
```

### wp plugin

Docs: https://developer.wordpress.org/cli/commands/plugin/

```
wp plugin install --activate simple-history
```

```
wp plugin list
```

```
wp plugin activate hello
```

### wp scaffold

Docs: https://developer.wordpress.org/cli/commands/scaffold/

```
wp scaffold plugin wcskopje --activate
```

```
nano wp-content/plugins/wcskopje/wcskopje.php
```

```PHP
/**
 * Plugin Name:     WordCamp Skopje
 * Plugin URI:      PLUGIN SITE HERE
 * Description:     PLUGIN DESCRIPTION HERE
 * Author:          YOUR NAME HERE
 * Author URI:      YOUR SITE HERE
 * Text Domain:     wcskopje
 * Domain Path:     /languages
 * Version:         0.1.0
 *
 * @package         Wcskopje
 */

function wcskopje( $content ) {
    return '<h2>' . esc_html__( 'Made at WordCamp Skopje', 'wcskopje' ) . '</h2>' . $content;
}
add_filter( 'the_content', 'wcskopje' );
```

### Global parameters

Docs: https://make.wordpress.org/cli/handbook/config/#global-parameters

```
wp --debug
```

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

## References

- "I don't want you to worry about that too much." - Tyler DeWitt, ["Ionization Energy and Atomic Radius"](https://youtu.be/Mmti4kKDcqA?t=14)
