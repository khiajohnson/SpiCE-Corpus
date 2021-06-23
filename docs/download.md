# Get the SpiCE corpus 

## Download

SpiCE is available through the UBC Research Data Collection via Scholars Portal Dataverse. You can access SpiCE from the button below. 

SpiCE is freely available under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/). That means you can use, copy, share, and adapt it, as long as you don't release your adaptation with additional restrictions, *and* you cite the corpus. We'd love to hear about what you're doing with the corpus, and [feature you on the research page](research.md)!!

<div align="center"><button class="button" onclick="window.location.href='https://doi.org/10.5683/SP2/MJOXP3';">Download SpiCE</button></div>
<br>

## Citation

As stated on the [home page](index.md), we prefer that you cite the corpus directly:

```text
@data{johnson_spice_2021,
    author = {Johnson, Khia A.},
    publisher = {Scholars Portal Dataverse},
    title = {{SpiCE: Speech in Cantonese and English}},
    UNF = {UNF:6:c6HNIwwpBuQOA349cyCu7w==},
    year = {2021},
    version = {V1},
    doi = {10.5683/SP2/MJOXP3},
    url = {https://doi.org/10.5683/SP2/MJOXP3}
}
```

But if you can't do that, then you can also cite the following paper:

```text
@inproceedings{johnson_lrec_2020,
    title = {SpiCE: A new open-access corpus of conversational bilingual speech in Cantonese and English},
    author = {Johnson, Khia A. and Babel, Molly and Fong, Ivan and Yiu, Nancy},
    booktitle = {Proceedings of the 12th Language Resources and Evaluation Conference},
    month = may,
    year = {2020},
    address = {Marseille, France},
    publisher = {European Language Resources Association},
    url = {https://www.aclweb.org/anthology/2020.lrec-1.503},
    pages = {4089--4095},
    language = {English},
    ISBN = {979-10-95546-34-4},
}
```

## What's in the download?

The download comes with:

- A ``README.md` file (this will give the full rundown)
- Tabular language background information
- PDF copy of the language background questionnaire
- Files used in and produced by the forced alignment process
- A copy of this documentation (as it was on the release date)
- 2 languages x 34 talkers = 68 `.wav` files (stereo, 16-bit, 44.1 kHz)
- 2 languages x 34 talkers = 68 `.TextGrid` files (each with 4 tiers: task, utterance, word, phone)

The `.wav` and `.TextGrid` files have a consitent format. For example, `VF21A_Cantonese2_20200131` would correspond to the following:

| Text                | What it means    | Other categories |
| :------------------ | :--------------- | :--------------- |
| `VF`                | Female           | `VF` = Male      |
| `21`                | Age              | varies `19`-`34` |
| `Cantonese`         | Language         | `English`        |
| `2`                 | Interview order  | `1`              |
| `20200231`          | Date in YYYYMMDD | varies           |

<br>
Unique participant IDs are made up of the first five characters. In this example, that would be `VF21A`. This ID is used in the language background summary. 

## Ethics

The corpus was developed in accordance with the [University of British Columbia Behavioural Research Ethics Board](https://ethics.research.ubc.ca/behavioural-research-ethics) (H18-02017). 

## Funding

SpiCE was funded by University of British Columbia [Public Scholars Initiative](https://www.grad.ubc.ca/psi) and Arts Graduate Research Awards to Khia A. Johnson, and by a [Social Sciences and Humanities Research Council of Canada (SSHRC)](https://www.sshrc-crsh.gc.ca/) Insight Grant to Molly Babel. 

