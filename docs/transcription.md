# How the files were transcribed

This page is an extension of the description published in [Johnson, Babel, Fong, & Yiu (2020)](https://www.aclweb.org/anthology/2020.lrec-1.503/), and some of the text from the paper is reproduced verbatim.

⚠️ The page is under development, and some of the information is subject to change ⚠️

---

## Overview

Broadly, the transcription pipeline followed these steps:

1. Files segmented into short chunks, with breaks placed during silences/breaths
2. Initial transcripts produced with Google Cloud Speech-to-Text
3. Hand-correction of orthographic transcripts by bilingual research assistants
4. Force-aligned transcripts produced for segmental content

The tools used in the process were:

- [Praat: doing phonetics by computer](https://www.fon.hum.uva.nl/praat/)
- [Pydub: Manipulate audio with a simple and easy high level interface ](https://pydub.com/)
- Google Cloud Speech-to-Text [Synchronous speech recognition](https://cloud.google.com/speech-to-text/docs/sync-recognize)
- [ELAN](https://archive.mpi.nl/tla/elan)
- Transcription guidelines were loosely adapted from the [HLVC project](http://projects.chass.utoronto.ca/ngn/HLVC/0_0_home.php)
- [PyCantonese: Cantonese Linguistics and NLP in Python](https://pycantonese.org/)
- [Montreal Forced Aligner 2.0](https://montreal-forced-aligner.readthedocs.io/)


## Speech recognition

Google Cloud Speech-to-Text has inexpensive options for both Canadian English (`en-CA`) and Hong Kong Cantonese (`yue-Hant-HK`)&mdash;it was used to produce an initial transcript, with the aim of expediting the orthographic transcription process. As expected, it worked better for English than Cantonese. 

Of the available options, synchronous speech recognition with short audio files was desirable from an ethics perspective, as it allowed for the files remain in local storage, and were only be sent to the cloud for processing (and not logged by Google).

To use this option, the audio files were first segmented into short chunks. This was done in Praat, by extracting the participant channel (`Convert - Extract one channel...`), marking silences (`Annotate - To TextGrid (silences)`), and manually adding and correcting such that individual chunks were under 15 seconds in length. This was done to facilitate subsequent manual correction. No attention was paid to constituents at this point, unless they coincided with a silence, pause, or breath. 

Using the timestamps from the Praat textgrid (Praat's annotation file type), short audio files were then extracted and downsampled to 16,000 Hz with `pydub`, and then processed with the Cloud Speech-to-Text Python client. The function used closely resembled that in the Cloud Speech-to-Text documentation for "Transcribing short audio files", copied below for ease of reference. Of the synchronous speech recognition output, both transcription and confidence were retained, and imported into ELAN for manual checking. 

```python
def transcribe_file(speech_file):
    """Transcribe the given audio file."""
    from google.cloud import speech
    import io

    client = speech.SpeechClient()

    with io.open(speech_file, "rb") as audio_file:
        content = audio_file.read()

    audio = speech.RecognitionAudio(content=content)
    config = speech.RecognitionConfig(
        encoding=speech.RecognitionConfig.AudioEncoding.LINEAR16,
        sample_rate_hertz=16000,
        language_code="en-US",
    )

    response = client.recognize(config=config, audio=audio)

    # Each result is for a consecutive portion of the audio. Iterate through
    # them to get the transcripts for the entire audio file.
    for result in response.results:
        # The first alternative is the most likely one for this portion.
        print(u"Transcript: {}".format(result.alternatives[0].transcript))
```

## Orthographic hand correction

Hand correction was done for participant speech in each of the interview files using ELAN. Note that while audible, the interviewer's speech was never transcribed. Further, instances that were considered to directly identify participants were silenced from the audio, and marked with "xxx" in the transcription.

Some conventions apply to both lanugages:

- Transcriptions reflect exactly what was said, as it was said
- The placeholder "xxx" denotes unintelligible speech
- Fragments are transcribed using "&" followed by the fragment produced (e.g., "&s")
- The "?" symbol marks questions; other punctuation is not used

Cantonese-specific conventions were:

- Where possible, transcription is in traditional characters
- Words without a standard character are transcribed with Jyutping (e.g., *jyut6ping3*)
- Fully-lexicalized syllable fusion is transcribed with the typical smaller number of characters (e.g., 咩 *me1* is a fully fused version of 乜嘢 *mat1 ye5*, and intermediate version 咩嘢 *me1 ye5*&mdash;all translate to "what")
- Non-lexicalized (or ambiguous) cases of syllable fu-sion are transcribed with the full number of characters fused (e.g., 朝頭早, "morning," is fully pronounced as *ziu1 tau4 zou2*, but can be fused to【朝頭】早 *ziau14zou2*. Brackets indicate the fused syllables)
- Filled pauses are transcribed with the characte r㖡 (*e6*),or using Jyutping if different (e.g., *m6*)
- Words produced in Mandarin Chinese are transcribed in Mandarin characters with "@m" appended to each 
- A similar convention applied to other languages, such as "@j" for Japanese, and "@ml" for Malay 
- Code-switches to English were not tagged with the @ symbol, merely written in English
- Numbers are written out in characters, or jyutping
- Conventions for transcribing sentence final particles are summarized here: *PDF coming soon!*

English-specific conventions were:

- Standard spelling was used
- Proper nouns are capitalized and hyphenated if composed of multiple words, as with "British-Columbia"
- Filled pauses are transcribed with "um", "er", "uh", and other similar *non*-elongated forms
- Numbers are written out in word form (e.g., "one hundred")

## Forced alignment

Force-aligned transcripts were produced with the Montreal Forced Aligner 2.0, using the hand-corrected orthographic transcripts, and the `train` function, as pretrained models were not available for Cantonese at the time of the corpus' release, and existing pretrained English models were not necessarily representative of the language varieties represented in this corpus. 

For English, the pronunciation dictionary provided with the Montreal Forced Aligner was used, which (while not a perfect choice) broadly reflects North American English varieties. Check it out here: <https://raw.githubusercontent.com/MontrealCorpusTools/mfa-models/master/dictionary/english.dict>.

For Cantonese, a pronunciation dictionary with segmental content only (no tones) was generated by mapping characters to the segments in the Jyutping romanization with the fantastic `pycantonese` package, and supplementing it with manual entries (mostly for instances of syllable fusion). While the force aligned transcripts were inspected to ensure that the ouput looked approximately correct, this was a very coarse inspection, and involved no manual correction of the word or phone tiers.


## The end product

This transcription process led to the following output. For each audio recording, there is an accompanying Praat .`textgrid` transcript with the same base filename. The transcript includes four tiers:

- `task`: Marks the portion of the interview as Sentences, Storyboard, or Interview
- `utterance`: The utterance that served as input to forced alignment.
- `word`: English word or Cantonese character/fusion
- `phone`: The segment of English or Cantonese as identifed by forced alignment





