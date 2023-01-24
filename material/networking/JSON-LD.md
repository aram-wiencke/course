# JSON-LD
JSON-LD (JavaScript Object Notation for Linked Data) is a lightweight, JSON-based format for representing and linking data on the web. 
It is designed to be easily integrated into existing web pages and applications, and to make it simple to express the relationships between different pieces of data. 
JSON-LD is based on the popular JSON format, but includes additional features such as context, which allows for unambiguous interpretation of the data, and links, which allow for connecting data from different sources. 
JSON-LD is also designed to be easy to understand and use, making it a popular choice for developers looking to work with linked data on the web.

```json
{
    "@context": {
        "name": "http://schema.org/name",
        "author": "http://schema.org/author",
        "book": "http://schema.org/Book"
    },
    "@type": "book",
    "name": "The Great Gatsby",
    "author": {
        "@type": "Person",
        "name": "F. Scott Fitzgerald"
    }
}
```

In this example, the JSON-LD context is used to define a set of terms that are used in the data, such as "name" and "author". These terms are associated with specific URLs, which allow the data to be connected to other data on the web. In this case, the "name" and "author" properties are linked to the schema.org vocabulary, which provides a common set of terms for describing books and people.
The @type property is used to specify the type of resource that this JSON-LD represents, in this case a book. The name and author properties are then used to provide specific information about the book, such as its title and the name of its author. The author property is also another JSON-LD object, which can be used to provide more information about the author, such as the type of person.
This way, the JSON-LD can easily link the book's information with the author's information, and also link it to the schema.org vocabulary, providing a semantic meaning to the data and allowing it to connect with other data that uses the same vocabulary.

## Another example
Here is an example of json that holds the context of on person.

```
{
  "@context": "https://json-ld.org/contexts/person.jsonld",
  "@id": "http://dbpedia.org/resource/John_Lennon",
  "name": "John Lennon",
  "born": "1940-10-09",
  "spouse": "http://dbpedia.org/resource/Cynthia_Lennon"
}
```
Following the URL of that context leads to it's schema.

```
{
   "@context":
   {
      "Person": "http://xmlns.com/foaf/0.1/Person",
      "xsd": "http://www.w3.org/2001/XMLSchema#",
      "name": "http://xmlns.com/foaf/0.1/name",
      "nickname": "http://xmlns.com/foaf/0.1/nick",
      "affiliation": "http://schema.org/affiliation",
      "depiction":
      {
         "@id": "http://xmlns.com/foaf/0.1/depiction",
         "@type": "@id"
      },
      "image":
      {
         "@id": "http://xmlns.com/foaf/0.1/img",
         "@type": "@id"
      },
      "born":
      {
         "@id": "http://schema.org/birthDate",
         "@type": "xsd:date"
      },
      "child":
      {
         "@id": "http://schema.org/children",
         "@type": "@id"
      },
      "colleague":
      {
         "@id": "http://schema.org/colleagues",
         "@type": "@id"
      },
      "knows":
      {
         "@id": "http://xmlns.com/foaf/0.1/knows",
         "@type": "@id"
      },
      "died":
      {
         "@id": "http://schema.org/deathDate",
         "@type": "xsd:date"
      },
      "email":
      {
         "@id": "http://xmlns.com/foaf/0.1/mbox",
         "@type": "@id"
      },
      "familyName": "http://xmlns.com/foaf/0.1/familyName",
      "givenName": "http://xmlns.com/foaf/0.1/givenName",
      "gender": "http://schema.org/gender",
      "homepage":
      {
         "@id": "http://xmlns.com/foaf/0.1/homepage",
         "@type": "@id"
      },
      "honorificPrefix": "http://schema.org/honorificPrefix",
      "honorificSuffix": "http://schema.org/honorificSuffix",
      "jobTitle": "http://xmlns.com/foaf/0.1/title",
      "nationality": "http://schema.org/nationality",
      "parent":
      {
         "@id": "http://schema.org/parent",
         "@type": "@id"
      },
      "sibling":
      {
         "@id": "http://schema.org/sibling",
         "@type": "@id"
      },
      "spouse":
      {
         "@id": "http://schema.org/spouse",
         "@type": "@id"
      },
      "telephone": "http://schema.org/telephone",
      "Address": "http://www.w3.org/2006/vcard/ns#Address",
      "address": "http://www.w3.org/2006/vcard/ns#address",
      "street": "http://www.w3.org/2006/vcard/ns#street-address",
      "locality": "http://www.w3.org/2006/vcard/ns#locality",
      "region": "http://www.w3.org/2006/vcard/ns#region",
      "country": "http://www.w3.org/2006/vcard/ns#country",
      "postalCode": "http://www.w3.org/2006/vcard/ns#postal-code"
   }
}
```
It's worth noting that the URLs used in the `@id` property are usually controlled by the developer or organization that created the JSON-LD file, and may require a specific setup to return the correct JSON-LD representation. Also, it's possible that the URLs might return a non-JSON-LD representation, such as HTML, if the server is not configured to handle requests for JSON-LD.
