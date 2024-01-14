<a name="readme-top"></a>

![Python Badge](https://img.shields.io/badge/Python-3.8.10-green)

<!-- PROJECT LOGO -->
# Fine-tuning GPT-J for quest story generation
This repository contains the code and datasets to fine-tune GPT-J 6B for generating MMORPG quest descriptions.

<!-- About -->
## Info

This repository contains all of the code and instructions for replicating my research into fine-tuning GPT-J 6B for generating MMORPG quest descriptions. 
This generation is based on a quest's objective as well as any additional context information that was collected from the original sources.

This was previously set up for [my thesis](http://essay.utwente.nl/97746/) where I compared the original quest descriptions with generated descriptions from these fine-tuned models.

Users can choose to generate new descriptions for existing quests by excluding some quests from the dataset and using these quests without their descriptions as input so that the model attempts to generate new descriptions.

Users can also write their own objectives and context information and have the model generate a fitting description, or have the model generate entirely new quests by leaving the input empty. Neither of these options have been tried and evaluated yet but could be interesting to try out.

This repository is provided as-is, and will not be updated for future versions of Python or any of the required libraries.

<!-- Usage -->
## Requirements and Usage

This code was set up in a Jupyter Labs environment with an Nvidia A10 GPU with 24GB of VRAM, as well as a 56 core CPU with 256GB of RAM. This was done in Python 3.8.10, with library requirements found in `requirements.txt` 

Two Jupyter notebook files are provided for fine-tuning with DeepSpeed on the GPU and inference on the CPU. The code documentation provides information on usage, or the libraries' documentation can be consulted for additional information. Some useful links have already been provided, although the official documentation is not very clear on the influence of certain parameters.


<!-- Datasets -->
## Datasets

Four datasets are included with this code. These datasets are quest collections from World of Warcraft, The Lord of the Rings Online, The Elder Scrolls Online, and Neverwinter. 
These datasets cannot be assumed to be fully complete and/or correct. Some entries were removed or edited for a better fit to the generation task.
These quest datasets have been collected from public resources and were adapted for research purposes under Fair Use copyright laws. I do not own this content. All rights reserved to the copyright owners.

These datasets contain quest titles, additional contextual information about the quest, objectives, and descriptions. Two types of `.csv` files have been provided per dataset: 
* `<name>_tabular.csv` is delimited with a caret (`^`) and can be used to open the dataset in software like Microsoft Excel for easier editing and selection of columns. However, this requires the user to recreate the tag structure themselves.
This can be done with the following Excel formula: `=Sheet1!A2&"<|property1|>"&Sheet1!B2&"<|property2|>"&Sheet1!C2` etc.

* `<name>_llm.csv` is set up as a single column and contains all of the entries with the information separated by tags.
These require the user to exclude some of the quests for which they want to evaluate the description generation quality but are otherwise ready to use as-is with the training code for fine-tuning.
The `<|startoftext|>` and `<|endoftext|>` tags to delineate entries are not in the dataset files but are added in code.

Please refer to the thesis for more detailed information on the methods used and the properties included per dataset, as well as certain particularities that should be taken into account during generation. Originally, some entries were excluded from the World of Warcraft dataset because of their writing style (lot of `...`, etc.), these are included in this version of the dataset.

<!-- LICENSE -->
## License

Distributed under the GNU GPLv3 License. See `LICENSE` for more information.

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* The training code was adapted from a now-deleted Github repository and adapted for research purposes.
* The World of Warcraft dataset was scraped from the [EvoWoW Wiki](https://wotlk.evowow.com/)
* The Lord of the Rings dataset was gathered from the [LOTRO Companion repository](https://github.com/LotroCompanion/lotro-companion)
* The Elder Scrolls Online dataset was gathered from the [Unofficial Elder Scrolls Pages](https://en.uesp.net/wiki/Main_Page)
* The Neverwinter dataset was gathered from the [Official Neverwinter Wiki](https://neverwinter.fandom.com/wiki/Neverwinter_Wiki)


<p align="right">(<a href="#readme-top">back to top</a>)</p>
