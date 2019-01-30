# NILDB

_The New Ithkuilic Language Database_

This project aims to maintain a comprehensive database of all lexical, morphological, and phonological information for the New Ithkuilic Language. It may eventually expand to include morpho-phonology. Sources for this information can be found in PDFs posted by /u/zeuhl59 on the [Ithkuil subreddit](https://reddit.com/r/Ithkuil).

## Database progress

* [x] Phonology: 100%
* [ ] Roots: ~20%
    - [ ] Spatial
    - [x] Motion
    - [ ] Positionally-defined componential parts
    - [x] Personal reference root
    - [x] Copular root
    - [x] General demonstrative root
* [ ] VxCs affixes: 0%
* [ ] Morphology: 0%
* [ ] Morpho-phonology: 0%

## Additional TODOs

* [ ] Script to make markdown references
* [ ] Searchable dictionary, like [la sutysisku](https://la-lojban.github.io/sutysisku/en/) or [lathiel.fr's](http://www.laethiel.fr/ithkuil/dico.php)

## Format

### roots.hjson

```hjson
{

    templates: {
        <template_name>: {
            generic_root: <Cr> # most generic root using this template
            # anything else here will be "inherited" by roots using this template
        }
        ...
    }

    categories: {
        <category_id>: {
            <Cr>: {

                definition: <lowercased, human-readable definition>
                # This is the only required property of the root; all other may be omitted

                description: <any extra information about the root (can be multiline>

                vxcs: <Cs>
                # an associated VxCs affix, if there is one

                template: <template_name>
                # a template from which this root will inherit all properties below, if any

                designations: [IFL, FML]
                # a human-readable description of how IFL and FML designations affect the root's meaning; each can be null

                stems: [s1, s2, s3]
                # a human-readable description of how each stem affects the root's meaning; each can be null
                # each stem can optionally be a whole designation definition, making the 'designations' property unnecessary
                
                specifications: [basic, content, ..., prerequisitive]
                # a human-readable description of how each specification affects the root's meaning
                # each specification can optionally be a whole stem definition, making the 'stems' property unnecessary

                gloss: <human-readable short definition>
                # a short and very succinct human-readable description of the root (try to avoid abbrevations)

                gloss_fmt: <gloss format string>
                # A format string describing how to put together 'designation_gloss' and 'stem_gloss' into a gloss string
                # If null, this will be ignored and the 'gloss' property will be used instead

                designation_gloss: [IFL, FML]
                stem_gloss: [s1, s2, s3]
                specification_gloss: [basic, content, ..., prerequisitive]
                # similar to 'designations', 'stems', and 'specifications' respectively, but used for glossing instead of definition

                full_gloss: TODO
                # TODO explain this
            }
            ...
        }
        ...
    }

}
```

TODO: Explain how `gloss_fmt` and `full_gloss` work.
