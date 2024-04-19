file:: [draft-ietf-cbor-cddl-modules-02.txt_1713534588876_0.pdf](../assets/draft-ietf-cbor-cddl-modules-02.txt_1713534588876_0.pdf)
file-path:: ../assets/draft-ietf-cbor-cddl-modules-02.txt_1713534588876_0.pdf

- As CDDL is being used in larger projects, the need for features has become known that cannot be easily mapped into this single extension point.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 66227ab9-1d38-4381-b60c-20fce45dab35
- defines a backward- and forward-compatible way to add a module structure to CDDL.
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 66227ac3-151a-4e03-8957-0021ee6ebfa6
- The functionality of the present document is considered a core part of what has colloquially been called CDDL 2.0, and is intended to be used with (and orthogonal to) other recent specifications such as a small set of CDDL grammar updates [I-D.ietf-cbor-update-8610-grammar]
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 66227add-5242-4074-acf3-b1f78c0ab940
  hl-stamp:: 1713535711038
- CDDL as documented in [RFC8610] (_basic CDDL_) has been designed with a crude form of composition: Concatenating a number of CDDL snippets creates a valid CDDL data model unless there is a name collision
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 66227b02-9522-4eda-b809-0128073b23ce
- Potential further work is outlined in Sections 4 and A.2 of [I-D.bormann-cbor-cddl-2-draft].
  ls-type:: annotation
  hl-page:: 4
  hl-color:: blue
  id:: 66227b2c-f75d-429f-8866-de1bbde15953
- To achieve the module structure in a way that is friendly to existing environments that operate with CDDL and basic CDDL implementations, we add a super-syntax (similar to the way pragmas are often added to a language), by carrying them in _directives_. Directives are parsed as comments in basic CDDL, so that each module source file can at the same time be basic CDDL on its own.
  ls-type:: annotation
  hl-page:: 4
  hl-color:: blue
  id:: 66227ea2-341d-453e-8c33-7c42ba4a2747
- This specification introduces _directives_ into CDDL. A single CDDL file becomes a _module_ by processing the (zero or more) directives in it. The semantics of the module are independent of the module(s) using it, however, importing a module may involve transforming its rule names into a new namespace (Section 2.2).
  ls-type:: annotation
  hl-page:: 4
  hl-color:: blue
  id:: 66227ebf-7040-45ba-b198-d55ddeec545b
- (Future versions might augment this with Web extractors and/or ways to extract CDDL modules from sites such as github and from InternetDrafts; see Appendix A.2 of [I-D.bormann-cbor-cddl-2-draft] for some design considerations.)
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 66227ef0-9ced-4e49-943c-4b825bd1b495
- .:
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 66227f14-cd47-4fda-a818-f398aa4b473f
- include, which includes all the rules from a module (which includes the ones imported/included there, transitively), or specific explicitly selected rules (clause ending in "from");
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 66227f4a-278a-4fa2-ada5-e1277bf78831
- import, which is similar to include but includes only those rules from the module that are referenced from the importing module, implicitly or explicitly (clause ending in "from"), including the rules that are referenced from these rules, transitively.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 66227f51-b83a-4b99-bc3b-523ad51faaaf
- However, if it is not acceptable that the library can pollute the namespace of the importing module, the import directive can specify a namespace prefix ("as" clause)
  ls-type:: annotation
  hl-page:: 6
  hl-color:: blue
  id:: 66227f74-dffb-440e-abdf-20c22abc0184
- An import however also draws in the transitive closure of the rules referenced
  ls-type:: annotation
  hl-page:: 7
  hl-color:: blue
  id:: 66228015-7278-4e57-be2a-63e336b6ec5e
- Tools may provide a convenient way to initiate the processing of directives from the command line.
  ls-type:: annotation
  hl-page:: 8
  hl-color:: blue
  id:: 6622805f-894c-4e19-a707-ee568109f9d4
- cddlc -2tcddl -icose=rfc9052 -scose.COSE_Key
  ls-type:: annotation
  hl-page:: 8
  hl-color:: blue
  id:: 66228069-02a6-4f0b-bee4-a26a47d61c3e
- A tool may provide a way to specify a root for the module tree from the command line:
  ls-type:: annotation
  hl-page:: 8
  hl-color:: blue
  id:: 66228075-5c4c-4368-af80-6db36c7cc1ad
- The module structure specified in this document is not believed to create additional security considerations beyond the general security considerations in Section 5 of [RFC8610].
  ls-type:: annotation
  hl-page:: 9
  hl-color:: blue
  id:: 662280bf-6625-4a2b-8282-01875f1f6ea3
- Implementations that employ the module structure defined in this document need to ascertain the provenance of the modules they combine into the CDDL models they employ operationally.
  ls-type:: annotation
  hl-page:: 9
  hl-color:: blue
  id:: 662280d3-ff0d-4a9b-bbbb-e0d72d908687
- implementations that rely on model-based input validation for enforcing certain properties of the data structure ingested (which, if not validated, could lead to malfunctions such as crashes and remote code execution) need to be particularly careful about the data models they apply, including their provenance and potential changes of these properties that upgrades to the referenced modules may (inadvertently or as part of an attack) cause. More generally speaking, implementations should strive to be robust against limitations of the model-based input validation mechanisms and their implementations that they employ.
  ls-type:: annotation
  hl-page:: 9
  hl-color:: blue
  id:: 662280ea-51dd-4e6b-a2ff-8920ef02637d