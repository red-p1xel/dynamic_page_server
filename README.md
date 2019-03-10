Dynamic Page API (Server)
=========================

**Dynamic Page Building API** &mdash; Skeleton with server-side implementation for build single page applications
using **Symfony4 Framework (Flex Edition)** and **Docker compose** CLI tool for building containers instances with 
isolated filesystems for containers and filesystem with user installed OS.


## Install and Configure

(https://symfony.com/doc/current/doctrine.html)[]

### Use PHP Package Manager *Composer*

Install packages (dependencies) with `composer` *(PHP Package Manager)*
```bash
$ composer install
```

Update packages with `composer`
```bash
$ composer update
```

Install packages or bundles with `composer`
```bash
$ composer req vendor/package-name
```

### Symfony CLI

#### 1. Configure the database connection

After complete full installation of project dependencies using by `Composer`.
You must configure the framework database connection in `.env` configuration file in project root directory 
and find next line with this environment variable `DATABASE_URL` and change values for `db_user`, `db_password`,
hostname or host ip-addr and port number `127.0.0.1:3306` for mysql service. See configuration settings in section `db`
contained into `docker-compose.yml`

#### Display list all available commands *Symfony (CLI)*

Just run next command into commandline execution for `php` container instance.
```bash
$ ./bin/console
```

### Docker compose combo-commands

List of useful commands working with Docker compose

1. Stop & Remove containers build
    ```bash
    $ docker-compose stop; docker-compose rm
    ```

1. Build. Up and execute shell for container instance on system background
    ```bash
    $ docker-compose build; docker-compose up -d; docker exec -it -u dev php bash
    ```

## Case: Implementation the Structured Data

All data on the page and in each separate section must **strictly** meet the criteria set for **structured data**
specifications and recommendations.


### Documentation about "Structured Data"

Links to related **documentation** , **guidelines**, **recipes** related by ***"Structured Data"***

1. [Structured Data Schema](https://schema.org/docs/schemas.html)
1. [Full list of types, shown on one page](https://schema.org/docs/full.html)
1. [Structured Data Schema Recipe](https://schema.org/Recipe)
1. [Google Structured Data Recipe Guidelines](https://developers.google.com/search/docs/data-types/recipe#guidelines)
1. [Structures Data on Google Developers CodeLabs](https://codelabs.developers.google.com/codelabs/structured-data/index.html#0)
1. [Google Developers - Build, Test, and Release Your Structured Data](https://developers.google.com/search/docs/guides/prototype)

### Structured Data Testing Tool

Use this ***"Structured Data"*** [Testing Tool](https://search.google.com/structured-data/testing-tool) for validate 
data on rendered page.

### Structured Data Example

Default format for structured data is `JSON-LD` all other format only for example

#### JSON-LD

```metadata json
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "MusicPlaylist",
  "name": "Classic Rock Playlist",
  "numTracks": "5",
  "track": [
    {
      "@type": "MusicRecording",
      "byArtist": "Lynard Skynard",
      "duration": "PT4M45S",
      "inAlbum": "Second Helping",
      "name": "Sweet Home Alabama",
      "url": "sweet-home-alabama"
    },
    {
      "@type": "MusicRecording",
      "byArtist": "AC/DC",
      "duration": "PT3M32S",
      "inAlbum": "Back In Black",
      "name": "Shook you all Night Long",
      "url": "shook-you-all-night-long"
    },
    {
      "@type": "MusicRecording",
      "byArtist": "ZZ Top",
      "duration": "PT4M13S",
      "inAlbum": "Eliminator",
      "name": "Sharp Dressed Man",
      "url": "sharp-dressed-man"
    },
    {
      "@type": "MusicRecording",
      "byArtist": "Bob Seger",
      "duration": "PT3M12S",
      "inAlbum": "Stranger In Town",
      "name": "Old Time Rock and Roll",
      "url": "old-time-rock-and-roll"
    },
    {
      "@type": "MusicRecording",
      "byArtist": "John Cougar",
      "duration": "PT3M39S",
      "inAlbum": "American Fool",
      "name": "Hurt So Good",
      "url": "hurt-so-good"
    }
  ]
}
</script>
```

#### Without Markup Example
```text
Classic Rock Playlist
1.Sweet Home Alabama - Lynard Skynard
2.Shook you all Night Long - AC/DC
3.Sharp Dressed Man - ZZ Top
4.Old Time Rock and Roll - Bob Seger
5.Hurt So Good - John Cougar
```

#### Microdata
```html
<div itemscope itemtype="http://schema.org/MusicPlaylist">
  <span itemprop="name">Classic Rock Playlist</span>
  <meta itemprop="numTracks" content="5"/>
  <div itemprop="track" itemscope itemtype="http://schema.org/MusicRecording">
    1.<span itemprop="name">Sweet Home Alabama</span> -
    <span itemprop="byArtist">Lynard Skynard</span>
    <link href="sweet-home-alabama" itemprop="url" />
    <meta content="PT4M45S" itemprop="duration" />
    <meta content="Second Helping" itemprop="inAlbum" />
   </div>
  <div itemprop="track" itemscope itemtype="http://schema.org/MusicRecording">
    2.<span itemprop="name">Shook you all Night Long</span> -
    <span itemprop="byArtist">AC/DC</span>
  <link href="shook-you-all-night-long" itemprop="url" />
    <meta content="PT3M32S" itemprop="duration" />
    <meta content="Back In Black" itemprop="inAlbum" />
  </div>
  <div itemprop="track" itemscope itemtype="http://schema.org/MusicRecording">
    3.<span itemprop="name">Sharp Dressed Man</span> -
    <span itemprop="byArtist">ZZ Top</span>
    <link href="sharp-dressed-man" itemprop="url" />
    <meta content="PT4M13S" itemprop="duration" />
    <meta content="Eliminator" itemprop="inAlbum" />
 </div>
  <div itemprop="track" itemscope itemtype="http://schema.org/MusicRecording">
    4.<span itemprop="name">Old Time Rock and Roll</span> -
    <span itemprop="byArtist">Bob Seger</span>
    <link href="old-time-rock-and-roll" itemprop="url" />
    <meta content="PT3M12S" itemprop="duration" />
    <meta content="Stranger In Town" itemprop="inAlbum" />
  </div>
  <div itemprop="track" itemscope itemtype="http://schema.org/MusicRecording">
    5.<span itemprop="name">Hurt So Good</span> -
    <span itemprop="byArtist">John Cougar</span>
    <link href="hurt-so-good" itemprop="url" />
    <meta content="PT3M39S" itemprop="duration" />
    <meta content="American Fool" itemprop="inAlbum" />
  </div>
</div>
```

#### RDFa
```html
<div vocab="http://schema.org/" typeof="MusicPlaylist">
  <span property="name">Classic Rock Playlist</span>
  <meta property="numTracks" content="5"/>
  <div property="track" typeof="MusicRecording">
    1.<span property="name">Sweet Home Alabama</span> -
    <span property="byArtist">Lynard Skynard</span>
    <meta content="sweet-home-alabama" property="url" />
    <meta content="PT4M45S" property="duration" />
    <meta content="Second Helping" property="inAlbum" />
   </div>
  <div property="track" typeof="MusicRecording">
    2.<span property="name">Shook you all Night Long</span> -
    <span property="byArtist">AC/DC</span>
    <meta content="shook-you-all-night-long" property="url" />
    <meta content="PT3M32S" property="duration" />
    <meta content="Back In Black" property="inAlbum" />
  </div>
  <div property="track" typeof="MusicRecording">
    3.<span property="name">Sharp Dressed Man</span> -
    <span property="byArtist">ZZ Top</span>
    <meta content="sharp-dressed-man" property="url" />
    <meta content="PT4M13S" property="duration" />
    <meta content="Eliminator" property="inAlbum" />
 </div>
  <div property="track" typeof="MusicRecording">
    4.<span property="name">Old Time Rock and Roll</span> -
    <span property="byArtist">Bob Seger</span>
    <meta content="old-time-rock-and-roll" property="url" />
    <meta content="PT3M12S" property="duration" />
    <meta content="Stranger In Town" property="inAlbum" />
  </div>
  <div property="track" typeof="MusicRecording">
    5.<span property="name">Hurt So Good</span> -
    <span property="byArtist">John Cougar</span>
    <meta content="hurt-so-good" property="url" />
    <meta content="PT3M39S" property="duration" />
    <meta content="American Fool" property="inAlbum" />
  </div>
</div>
```