# Get Token

This is a simple Ruby script to generate API tokens from the Brightbox Cloud API using your credentials.

Details about the Brightbox Cloud (currently in Beta) are available here: http://beta.brightbox.com/

The Brightbox API uses OAuth2 (Draft 10) token based authentication for all of it's requests. So if you find yourself making requests from curl getting valid tokens becomes a pain.

Whilst useful at a low level, you might find using the Brightbox CLI tools (https://github.com/brightbox/brightbox-cli) or the Fog library (https://github.com/geemus/fog) more use.

## Setup

The script uses your existing Fog credentials to access the Brightbox URL, client ID and secret and perform an API call to request a token.

Fog supports multiple sets of credentials, each can be setup separately.

````yaml
:default:
  :brightbox_client_id:   cli-named
  :brightbox_secret:      zsp3mk48hwhklt
:additional:
  :brightbox_auth_url:    "https://api.gb2.brightbox.com"
  :brightbox_api_url:     "https://api.gb2.brightbox.com"
  :brightbox_client_id:   cli-kklds
  :brightbox_secret:      3hht333qjfDsa17
````

(These are fake values before you think I wasn't paying attention!)

## Usage

Given it's goal, it is pretty minimal.

Run the script without arguments and it will use your default credentials.

    $ get_token
    a03979ca5c296ae78996305d6e52117354bd4ee7

Run the script with the name of another set of credentials it uses them instead

    $ get_token additional
    67d5cb32c0ea874adf59b9600325dcd4764e7176
    $ curl https://api.gb1.brightbox.com/1.0/account -H "Authorization: OAuth `get_token`"
    ... Lots of JSON ...

## Future development

This is a pretty simple tool that _might_ be useful to someone else. No real additional work on this script.

A replacement tool is planned.

* Delivered as a gem
* Will also check Brightbox CLI credentials for possible matches

