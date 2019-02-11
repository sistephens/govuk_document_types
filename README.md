# GOV.UK document types

This gem contains the "document supertypes" for GOV.UK. Supertypes are groupings
of document types.

https://docs.publishing.service.gov.uk/document-types.html

## Usage


Find the supertypes for a document type:

```rb
supertypes = GovukDocumentTypes.supertypes(document_type: "detailed_guide")
supertypes["content_purpose_subgroup"]
=> "guidance"
```

Find the document types for a supertype:

```rb
GovukDocumentTypes.supergroup_document_types("policy_and_engagement")
=> ["case_study", "closed_consultation", "consultation_outcome", "impact_assessment", "open_consultation", "policy_paper"]
```

## How to add or update a supertype

1. Add it to [data/supertypes.yml](data/supertypes.yml) in this gem and release a new version
2. Bump the gem version across GOV.UK apps using [Dependabot](https://app.dependabot.com/)
3. Run the `rummager:update_supertypes` Rake task in Rummager to update the elasticsearch indices _after_ bumping the gem version in Rummager

## Running the test suite

```
bundle exec rake
```

## License

[MIT License](LICENSE.txt)
