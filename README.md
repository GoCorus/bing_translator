# BingTranslator  

[![Build Status](http://img.shields.io/travis/ikeikeikeike/bing_translator.svg?style=flat-square)](http://travis-ci.org/ikeikeikeike/bing_translator)
[![Hex version](https://img.shields.io/hexpm/v/bing_translator.svg "Hex version")](https://hex.pm/packages/bing_translator)
[![Hex downloads](https://img.shields.io/hexpm/dt/bing_translator.svg "Hex downloads")](https://hex.pm/packages/bing_translator)

[](
[![Release](http://img.shields.io/github/release/ikeikeikeike/bing_translator.svg?style=flat-square)](https://github.com/ikeikeikeike/bing_translator/releases/latest)\
[![Code Climate](http://img.shields.io/badge/code_climate-Erlang_17.4-brightgreen.svg?style=flat-square)](https://travis-ci.org/ikeikeikeike/bing_translator)\
)

A simple Ruby interface to Bing's translation API

## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed as:

### Add bing_translator to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [{:bing_translator, "~> 0.1.5"}]
end
```

### Ensure bing_translator is started before your application:

```elixir
def application do
  [applications: [:bing_translator]]
end
```

#### Getting a Client ID and Secret


To sign up for the free tier (as of this writing), do the following:

1. Go [here](http://go.microsoft.com/?linkid=9782667)
2. Sign in with valid MSN credentials.
3. On the right side, click 'SIGN UP', under the $0.00 option.
4. Read and accept the terms and conditions and click the big 'SIGN UP'
   button.
5. [Create a new application](https://datamarket.azure.com/developer/applications).
   Fill in a unique client ID, give it a valid name, give it a valid redirect
   URI (not actually used by the Bing Translator API, so it can be anything)
   and hit 'CREATE'.
6. Click on the name of your application to see the info again. You'll need
   the 'Client ID' and 'Client secret' fields.


### Usage

```elixir
# Specify all arguments
BingTranslator.configure("YOUR_CLIENT_ID", "YOUR_CLIENT_SECRET", false)

# Or... Specify only required arguments
BingTranslator.configure("YOUR_CLIENT_ID", "YOUR_CLIENT_SECRET")

spanish = BingTranslator.translate("Hello. This will be translated!", [from: "en", to: "es"])

# without :from for auto language detection
spanish = BingTranslator.translate("Hello. This will be translated!", to: "es")

locale = BingTranslator.detect("Hello. This will be translated!") # => "en"
languages = BingTranslator.supported_language_codes # => ["ar", "bs-Latn", "bg", "ca", "zh-CHS",,,,,]

# The speak method calls a text-to-speech interface in the supplied language.
# It does not translate the text. Format can be 'audio/mp3' or 'audio/wav'

audio = BingTranslator.speak("Hello. This will be spoken!", language: :en, format: "audio/mp3", options: "MaxQuality")
```

### Documentation

[API Reference](http://hexdocs.pm/bing_translator/api-reference.html).

### Thanks

This gem is inspired from Codeblock/bing_translator-gem and roomorama/bing_translator

- [bing_translator ](https://github.com/roomorama/bing_translator )
- [bing_translator-gem](https://github.com/Codeblock/bing_translator-gem)
