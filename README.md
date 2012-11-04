# gnip-rule [![Build Status](https://secure.travis-ci.org/eriwen/gnip-rule.png)](http://travis-ci.org/eriwen/gnip-rule) [![Code Climate](https://codeclimate.com/badge.png)](https://codeclimate.com/github/eriwen/gnip-rule)
This gem simplifies the effort to add/delete/list rules using the [Gnip Rules API](http://support.gnip.com/customer/portal/articles/477713-rules-methods-documentation). It handles HTTP request/response and helps your rules conform to Gnip's restrictions.

## Installation
`gem install gnip-rule` or add the following to your `Gemfile`:

```ruby
gem 'gnip-rule', '~> 0.3'
```

## Usage

```ruby
require 'gnip-rule'

rules = GnipRule::Client.new(API_URL, USERNAME, PASSWORD)

# Add as a String, Rule, or Array of either
rules.add('foo')
rules.add('bar', 'tag')
rules.add(['foo', 'bar', 'baz'], 'tag')
rules.add(GnipRule::Rule.new('value', 'tag'))
rules.add([GnipRule::Rule.new('foo', 'bar'), GnipRule::Rule.new('baz', 'tag2')])

# Same with delete
rules.delete('baz', 'tag')
rules.delete(['foo', 'bar'])
rules.delete(GnipRule::Rule.new('value', 'tag'))

# Get all rules
rules_list = rules.list()
rules_list.each { |rule| rule.valid? }
jsonified = rules_list.map { |rule| rule.as_json `}
```

## License
Licenced under the [MIT License](http://www.opensource.org/licenses/mit-license.php)

I provide this software free of charge. If you find it helpful, please endorse me on coderwall: [![endorse](http://api.coderwall.com/eriwen/endorsecount.png)](http://coderwall.com/eriwen)