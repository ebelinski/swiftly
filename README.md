# Swiftly

[Swiftly](https://swiftly.dev/) is a [Swift](https://swift.org/) language reference website for Swift developers of all levels. It is built with [Jekyll](https://jekyllrb.com/).

The guide pages are found in the [_guides](_guides) directory. These pages are written in Markdown, although many pages also contain HTML, and use the line `{::options parse_block_html="true" /}` to render the HTML.

## Setup

1. Install Ruby 2.7.0, preferrably through [rbenv](https://github.com/rbenv/rbenv).
2. Install Jekyll with the instructions [here](https://jekyllrb.com/docs/).
3. Run `bundle exec jekyll serve` in the root folder to start the Jekyll server, and visit [http://localhost:4000](http://localhost:4000).

### Tips

* I have found that editing with Sublime Text using the Markdown Extended syntax works best. It ensures that the Swift code inside the Markdown files are highlighted in the editor.