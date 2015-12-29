# Github to SVG, WordPress Plugin Directory Deployment Script

Deploys a WordPress plugin from GitHub (git) to the WordPress Plugin Repostiory (svn).

## Credits

Well over 90% of this script was written by others:

 - **[Dean Clatworthy](https://twitter.com/deanclatworthy)** - [Original script](https://github.com/deanc/wordpress-plugin-git-svn)
 - **[Brent Shepherd](https://twitter.com/thenbrent)** - [Avoids permanent local SVN repo, avoids sending redundant stuff to WP repo](http://thereforei.am/2011/04/21/git-to-svn-automated-wordpress-plugin-deployment/)
 - **[Patrick Rauland](https://twitter.com/BFTrick)** - [Support for WP assets folder for plugin page banner and screenshots](https://github.com/BFTrick/jotform-integration/blob/master/deploy.sh)
 - **[Ben Balter](https://twitter.com/benbalter)** - [Submodules support and plugin slug prompt](https://github.com/benbalter/Github-to-WordPress-Plugin-Directory-Deployment-Script/)
 - **[Gary Jones](https://twitter.com/GaryJ)** - [Personalisation and commenting out bits not required when using git-flow](https://github.com/GaryJones/wordpress-plugin-git-flow-svn-deploy)

## What's different

- Removed git submodules support (we don't use them)
- Removed git-flow introduced by Gary Jones (we don't need it)
- Uncommmented some bits commented out by Gary Jones
- Added svn props for correct mime-types of static images
- Modified list of ignored files
- Replaced default svn username, obviously

## Process

 1. Prompts for plugin slug and other data.
 - Verifies plugin header version number matches readme stable version number or readme stable version is trunk
 - Pushes latest git commit and tags to GitHub.
 - Creates temporary checkout of SVN repo.
 - Ignores non-WordPress repo files from SVN.
 - Copies git export to SVN trunk.
 - Copies contents of assets directory in trunk to a directory parallel to trunk.
 - Commits SVN trunk, assets and tag.
 - Attempts to remove temporary SVN checkout.

## Install

1. In your terminal, `cd` into the directory which contains subdirectories for each of your plugins. i.e. on a local install of WordPress, this will probably be `wp-content/plugins` (`content/plugins` or `app/plugins` if you use Mark Jaquith's Skeleton or its derivatives, as I do). Then `git clone https://github.com/ihorvorotnov/wordpress-plugin-git-to-svn-deploy.git .` to clone the deploy script locally.
2. Ensure that the shell script is executable. In Mac / Unix, run `chmod +x deploy.sh`.
3. Run the script with `sh deploy.sh`. You can also double-click it in Finder / Explorer to start it.
4. You'll now be guided through a set of questions.
