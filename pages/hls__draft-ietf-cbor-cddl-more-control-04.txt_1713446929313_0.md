file:: [draft-ietf-cbor-cddl-more-control-04.txt_1713446929313_0.pdf](../assets/draft-ietf-cbor-cddl-more-control-04.txt_1713446929313_0.pdf)
file-path:: ../assets/draft-ietf-cbor-cddl-more-control-04.txt_1713446929313_0.pdf

- Table 1: New control operators in this document
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 66212031-7344-4bed-a2c7-4f8f44f7868f
- This specification uses terminology from [RFC8610].
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 66212041-7290-445f-91d9-ee9ae008523b
- In particular, with respect to control operators, "target" refers to the left-hand side operand
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 6621204f-6a2a-4304-afc5-78664e2d6bfa
- "controller" to the right-hand side operand."Tool" refers to tools along the lines of that described in Appendix F of [RFC8610]
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 66212059-6048-4cf4-a6b0-f06e92233863
- Byte Strings: Base16 (Hex), Base32, Base45, Base64
  ls-type:: annotation
  hl-page:: 3
  hl-color:: blue
  id:: 66212077-2c64-4b09-921c-d38abbef356e
- The control operators generally are of a form that could be used like this: signature-for-json = text .b64u signature signature = bytes .cbor COSE_Sign1
  ls-type:: annotation
  hl-page:: 4
  hl-color:: blue
  id:: 66212093-fe61-4d67-9c76-e7de9af7985e
- Table 2: Control Operators for Text Conversion of byte strings
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 662120a2-5e98-4e95-bd75-8173d6f7b828
- Note that this specification is somewhat opinionated here: It does not provide base64url, base32 or base32hex encoding with padding, or base64 classic without padding.
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 662120ee-c4f5-469f-a289-f90b0b1a6728
- The additional designation "sloppy" indicates that the text string is not validated for any additional bits being zero, in variance to what is specified in the paragraph behind table 1 in Section 4 of[RFC4648].
  ls-type:: annotation
  hl-page:: 5
  hl-color:: blue
  id:: 662120fb-61a6-46cf-9114-048d914c4cf5
- 2.3. Printf-style Formatting
  ls-type:: annotation
  hl-page:: 6
  hl-color:: blue
  id:: 662127b7-918a-42f8-ac9e-d6f888feda75
- The controller (right-hand side) of the .printf control is an array of one Printf-style format string and zero or more data items that fit the individual conversion specifications in the format string. The construct matches a text string representing the textual output of an equivalent C-language printf function call that is given the format string and the data items following it in the array.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: blue
  id:: 662127c3-40ae-46a0-b88d-8d521ac403be
- From the printf specification in the C language, length modifiers(paragraph 7) are not used and MUST NOT be included in the format string.
  ls-type:: annotation
  hl-page:: 6
  hl-color:: blue
  id:: 662127d0-3837-497b-9264-8ad7a175b81e
- ls-type:: annotation
  hl-page:: 7
  hl-color:: blue
  id:: 662127f9-901d-4736-90b6-e063e157c1ec
  3. Text Processing
- 3.1. Join
  ls-type:: annotation
  hl-page:: 7
  hl-color:: blue
  id:: 66212803-f3c5-447e-ad66-62af915e8be0
- In general, this control operator is hard to validate as it would require full parser functionality. It is therefore recommended to only use it in simple cases, and leave full parsing to ABNF (see Section 3 of [RFC9165]) or similar.
  ls-type:: annotation
  hl-page:: 7
  hl-color:: blue
  id:: 66212810-5344-4b81-b062-53d21f536cda