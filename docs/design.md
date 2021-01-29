# Design Overview

This section covers general information about SpiCE, including how the corpus was collected, and how the transcriptions were developed. Much of this is covered in the [open-access paper describing the corpus](https://www.aclweb.org/anthology/2020.lrec-1.503/).

## SpiCE is a phonological corpus

What's that? A phonological corpus for spoken language has audio recordings, linguistic annotations at the level of the word and phone, as well as metadata. A phonological corpus should also be representative of the selected population, big enough, and collected for a purpose. SpiCE is a phonological corpus, albeit one with *force-aligned phones*. A future release might include hand-corrected phones, but that's a big ❓ at the moment!

## File naming conventions

Each filename corresponding to a participant is named with a consistent format, such as `VF21A_Cantonese2_20200131`. This corresponds to the following:

| Text                | What it means    | Other categories |
| :------------------ | :--------------- | :--------------- |
| `VF`                | Female           | `VF` = Male      |
| `21`                | Age              | varies  			|
| `Cantonese`         | Language         | `English`        |
| `2`                 | Interview order  | `1` 				|
| `20200231`          | Date in YYYYMMDD | varies 			|

Unique participant IDs are made up of the first five characters. In this example, `VF21A`.
