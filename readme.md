# GraphQL APIs<br /> with eZ Platform<br />Symfony CMS

<center><small>eZ Meetup Oslo<br />February 22nd 2018 - Jani Tarvainen</small></center>

---

## Agenda

 - GraphQL introduction
 - GraphQL with eZ Platform
 - GraphQL caveats
 - Headless site example using Next.js

---

# GraphQL introduction

--

## GraphQL introduction

- Under the <a href="http://graphql.org">GraphQL</a> umbrella:
  - A communications protocol
  - A Query Language
  - Server implementations
  - Client implementations
- Timeline:
  - Used at Facebook since 2012
  - Public release in 2015
  - Gaining momentum in 2017
- Notable <a href="http://graphql.org/users/">adopters</a>: GitHub, Pinterest, Neo4j,<br /> Shopify, New York Times, Sky, Twitter, Yelp…

--

## GraphQL introduction

- An alternative to RESTful APIs
  - GraphQL independent of protocol,<br />
    Not using on HTTP verbs (POST, GET…)
  - REST is an architectural pattern<br />
  GraphQL is a specification
- GraphQL APIs are strongly typed
- Self-documenting
  - You WILL need to write descriptions ;)

--

## GraphQL with PHP &amp; Symfony

- Reference implementation in JavaScript
- Two mature PHP implementations:
  - <a href="https://github.com/webonyx/graphql-php">WebOnyx GraphQL library</a>
  - <a href="https://github.com/Youshido/GraphQL">Youshido GraphQL library</a>
- Both solid and feature complete
- Symfony integrations:
   - <a href="https://github.com/overblog/GraphQLBundle">OverBlog GraphQL Bundle</a>
   - <a href="https://github.com/Youshido/GraphQLBundle">Youshido GraphQL Bundle</a>
- More: <a href="https://symfony.fi/entry/state-of-graphql-php-libraries-and-symfony-integrations-in-2017">GraphQL, PHP and Symfony</a>

--

## GraphQL client libraries

 - You can use raw HTTP
 - Libs provide
   - Convenience
   - Client side caching
   - Security (Phear the dreaded GraphQL Injection)
 - Notable browser / Node.js libraries     
   - <img src="/img/urql-logo.png" alt="Urql" style="max-height:150px; display:inline-block;float:right;" /> <a href="https://code.facebook.com/posts/1362748677097871/relay-modern-simpler-faster-more-extensible/">Relay Modern</a>
   - <a href="https://www.apollographql.com">Apollo</a>
   - <a href="https://github.com/FormidableLabs/urql">Urql</a>



---

# GraphQL with<br />eZ Platform

--

## GraphQL for CMS

- CMS has a lot of complexity (content types, permissions, relations, content rendering…)
- A generic protocol, not CMS specific
- Queries are application specific
- Developer friendly for queries (reads)
- Colocation of <a href="https://twitter.com/velmu/status/911839955718213632">queries and template</a> 😱

--

## GraphQL and eZ Platform

 - eZ Platform does not ship with GraphQL support
 - That won't stop you:
   - Use the eZ Platform GraphQL Bundle
   - Integrate using a Symfony GraphQL bundle
   - Roll your own GraphQL server (please don't!)

--

## eZ Platform GraphQL Bundle

- An experimental bundle from October 2016
- Not maintained, but it's mostly glue code ¯\\_(ツ)_/¯
- I <a href="https://github.com/janit/ezplatform-graphql-bundle">forked it</a> to run with <a href="https://ezplatform.com/Blog/eZ-Platform-2.0-and-1.13-have-arrived">eZ Platform v2</a>
- Integrates the OverBlog GraphQL Bundle to repo
- A decent feature list:
  - Query content, location and users
  - Search content, list location children…
- <a href="https://master-7rqtwti-dyxa6s2xeqt7y.eu.platform.sh/graphiql">GraphiQL shell</a>

--

## A simple example query

- eZ Platform specific example
```
{
  locationChildren(id: 2) {
    content {
      name
    }
  }
}
```
- Gets location children's name property for location 2

--

## Integrate using<br />a Symfony GraphQL bundle

- Install a generic GraphQL Bundle
- Both OverBlog and Youshido are solid
  - OverBlog focusing on Symfony 4 + Flex now
  - Similar functionality and lingo
- You will need to:
  - Configure schema (with types)
  - Create resolver (to resolve queries from content repo)
- <a href="https://symfony.fi/entry/adding-a-graphql-api-to-your-symfony-flex-app">Adding GraphQL API to your Symfony Flex app</a>

--

## My recommendations

- For tinkering:
  - Use the eZ Platform GraphQL Bundle
  - It works great, but there might be issues
  - You can <a href="https://janit.iki.fi/ez-rest-graphql/#/5">extend it with your queries</a>
- For production:
  - Create your own GraphQL Bundle integration
  - Exact control of what you expose
  - A generic framework to expose QueryTypes?

--

## GraphQL Caveats

- You're exposing an generic for users to query
  - Users may find things that they shouldn't
  - Users could cause load by <a href="http://graphql-ruby.org/queries/complexity_and_depth.html">complex or deep queries</a>
- HTTP caching not trivial
  - Everything's a POST in most client libraries
  - Even GETs can be very different
- Vulnerable to "GraphQL injections"
  - Client libraries sanitize input
- It's just one tool - There's a time and place for it

---

# Headless site example using Next.js

--

- A sample decoupled site built with the<br />universal JavaScript framework <a href="https://react-etc.net/entry/next-js-is-the-universal-react-framework-you-ve-been-looking-for">Next.js</a>:

 - https://react.nu/
 - https://github.com/janit/decoupled-cms-nextjs-graphql
 - https://v1-11-hbgl5gq-oiiukjqgkij7e.eu.platform.sh/graphiql
 - https://janit.iki.fi/cms-graphql-nextjs/
 - https://www.youtube.com/watch?v=efoeIz9xTDs

---

# Thank you

- Questions?