# Dionysos Content Field
> This component is a part of the **Olympus Dionysos fields** for **WordPress**.

```sh
composer require getolympus/olympus-dionysos-field-content
```

---

[![Olympus Component][olympus-image]][olympus-url]
[![CodeFactor Grade][codefactor-image]][codefactor-url]
[![Packagist Version][packagist-image]][packagist-url]
[![MIT][license-image]][license-blob]

---

<p align="center">
    <img src="https://github.com/GetOlympus/olympus-dionysos-field-content/blob/master/assets/field-content-64.png" />
</p>

---

## Field initialization

Use the following lines to add a `content field` in your **WordPress** admin pages or custom post type's meta fields:  
_Note the `$identifier` (first `::build()` parameter) is set to `false` because no value is stored in database._

```php
return \GetOlympus\Dionysos\Field\Content::build(false, [
    'title'   => 'The Dark Knight',
    'content' => '',
    'debug'   => false,
    'file'    => 'im_the_batman.php',
    'vars'    => [
        'question' => 'Who\'s the Batman?',
        'answers'  => [
            'the-joker'    => 'The Joker',
            'harley-quinn' => 'Harley Quinn',
            'bruce-wayne'  => 'Bruce Wayne, don\'t tell anybody!',
            'gotham-city'  => 'Gotham City',
        ],
    ],
]);
```

## Variables definitions

| Variable      | Type    | Default value if not set | Accepted values |
| ------------- | ------- | ------------------------ | --------------- |
| `title`       | String  | `'File contents'` | *empty* |
| `content`     | String  | *empty* | *empty* |
| `debug`       | Bookean | *empty* | *empty* |
| `file`        | String  | `false` | `true` or `false` |
| `vars`        | Array   | *empty* | *empty* |

Notes:
* Set `content` to display HTML tags. It can be used as a fallback if file doesn't exist
* Set `debug` to `true` to enable the debug mode in case file inclusion fail
* Set `file` to define the PHP file path to include as `include_once` PHP function

## Vars usage

In the included file (`im_the_batman.php` in this example), you can use the `$v` variable as an array:

```php
// Display question
echo '<h2>'.stripslashes($v['question']).'</h2>';
echo '<ul>';

// Display answers choices with radio button
foreach ($v['answers'] as $k => $answer) {
    echo '<li class="'.$k.' is-the-batman">'.stripslashes($answer).'</li>';
}

echo '</ul>';
```

## Content display priority

The component will display, by priority:

1. included `file` path
2. everything in `content`

Note: do not forget to set `debug` to `true` to display an error in the case the `file` does not exist or is not readable.

## Release History

0.0.12
- Remove useless description

0.0.11
- New Olympus components compatibility
- Change repository to be a part of Dionysos fields

0.0.10
- FIX: content raw display on twig file

## Contributing

1. Fork it (<https://github.com/GetOlympus/olympus-dionysos-field-content/fork>)
2. Create your feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request

---

**Built with ♥ by [Achraf Chouk](https://github.com/crewstyle "Achraf Chouk") ~ (c) since a long time.**

<!-- links & imgs dfn's -->
[olympus-image]: https://img.shields.io/badge/for-Olympus-44cc11.svg?style=flat-square
[olympus-url]: https://github.com/GetOlympus
[codefactor-image]: https://www.codefactor.io/repository/github/GetOlympus/olympus-dionysos-field-content/badge?style=flat-square
[codefactor-url]: https://www.codefactor.io/repository/github/getolympus/olympus-dionysos-field-content
[license-blob]: https://github.com/GetOlympus/olympus-dionysos-field-content/blob/master/LICENSE
[license-image]: https://img.shields.io/badge/license-MIT_License-blue.svg?style=flat-square
[packagist-image]: https://img.shields.io/packagist/v/getolympus/olympus-dionysos-field-content.svg?style=flat-square
[packagist-url]: https://packagist.org/packages/getolympus/olympus-dionysos-field-content