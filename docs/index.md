---
layout: home
---

# [**Download**](https://huggingface.co/datasets/Skylion007/openwebtext)

**Summary:**

Today we're announcing the release of a beta version of Open WebText -- an open source effort to reproduce OpenAI's WebText dataset, as detailed [here](https://d4mucfpksywv.cloudfront.net/better-language-models/language-models.pdf). This distribution was created by Aaron Gokaslan and Vanya Cohen of Brown University. The following post outlines the steps taken to reproduce the dataset, and provides information for those seeking to contribute to its further development.

**Open WebText:**

We started by extracting all Reddit post urls from the [Reddit submissions dataset](https://files.pushshift.io/reddit/submissions/). These links were deduplicated, filtered to exclude non-html content, and then shuffled randomly. The links were then distributed to several machines in parallel for download, and all web pages were extracted using the newspaper python package. Using Facebook [FastText](https://github.com/facebookresearch/fastText), non-English web pages were filtered out.

Subsequently, near-duplicate documents were identified using [local-sensitivity hashing](https://en.wikipedia.org/wiki/Locality-sensitive_hashing#Applications) (LSH). Documents were hashed into sets of 5-grams and all documents that had a similarity threshold of greater than 0.5 were removed. The the remaining documents were tokenized, and documents with fewer than 128 tokens were removed. This left 38GB of text data (40GB using SI units) from 8,013,769 documents.

**Next Steps:**

Given OpenAI's limited release of information around WebText and GPT-2, we acknowledge there may be further room for improvement of the dataset. As such we welcome contributions and suggestions for improvements. We hope that the availability of this dataset encourages further work into reproducing GPT-2 and proves useful for other projects beyond. We will release more code on the master branch soon.

**Citation**
~~~~
@misc{Gokaslan2019OpenWeb,  
	title={OpenWebText Corpus},
	author={Aaron Gokaslan and Vanya Cohen},
	howpublished={\url{http://Skylion007.github.io/OpenWebTextCorpus}}, 
	year={2019}
}
~~~~

**Licensing:**

These data are released under this licensing scheme:

We do not own any of the text from which these data has been extracted.

We license the actual packaging of these parallel data under the [Creative Commons CC0 license ("no rights reserved")](https://creativecommons.org/share-your-work/public-domain/cc0/)

Notice and take down policy:

**Notice:** Should you consider that our data contains material that is owned by you and should therefore not be reproduced here, please:

Clearly identify yourself, with detailed contact data such as an address, telephone number or email address at which you can be contacted.

Clearly identify the copyrighted work claimed to be infringed.

Clearly identify the material that is claimed to be infringing and information reasonably sufficient to allow us to locate the material.

And contact us at the following email address: openwebtext at gmail.com

**Take down:** We will comply to legitimate requests by removing the affected sources from the next release of the corpus.
