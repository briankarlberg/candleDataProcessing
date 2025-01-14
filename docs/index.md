---
layout: default
title: CoderData
---

<link rel="stylesheet" href="assets/css/style.css">

<!-- # Cancer Omics and Drug Experiment Response Data (`coderdata`) Python Package -->

### Introduction
CoderData is a cancer benchmark data package developed in Python and R. 
There are two aspects of this package, the backend build section and the user facing python package.
The build section is a github workflow that generates four cancer datasets in a format that is easy for users and algorithms to ingest. 
The python package allows users to easily download the data, load it into python and reformat it as desired.

### Installation
To install `coderdata`, simply run the following command in your terminal:

```bash
pip install coderdata
```

### Usage
##### Bash / Command line
To download datasets, simply run the following command in your terminal. Remove the prefix argument if you'd like to install all datasets.

```bash
coderdata download --prefix hcmi
```

##### Python
To download, load, and call datasets in python, simply run the following commands. 

<div class="code-box">
    <p>import coderdata</p>
    <p>coderdata.download_data_by_prefix('hcmi') # download all hcmi data to local directory.</p>
    <p>hcmi_data = coderdata.DatasetLoader('hcmi') # load hcmi data from local directory into the DatasetLoader object.</p>
    <p>hcmi_data.transcriptomics # call transcriptomics data from the DatasetLoader object.</p>
</div>


### Datasets

<div class="dataset-section">
    {% assign datasets = 'cell_line,cptac,hcmi,beataml' | split: ',' %}
    {% for dataset in datasets %}
        <div class="dataset-container">
            <a href="datasets/{{ dataset }}" class="dataset-link">{{ dataset | capitalize }}</a>
            <div class="dataset-blurb">
                {% case dataset %}
                    {% when 'cell_line' %}
                        <p>Cell Lines: {{ site.data.stats.cell_line.cell_lines }} </p>
                        <p>Genes: {{ site.data.stats.cell_line.genes }} </p>
                        <p>Drugs: {{ site.data.stats.cell_line.drugs }} </p>
                        <span class="dot dot_transcriptomics"></span> 
                        <span class="dot dot_proteomics"></span> 
                        <span class="dot dot_mutations"></span> 
                        <span class="dot dot_copy_number"></span> 
                    {% when 'cptac' %}
                        <p>Cancer Types: {{ site.data.stats.cptac.cancer_types }} </p>
                        <p>Genes: {{ site.data.stats.cptac.genes }} </p>
                        <p>Drugs: {{ site.data.stats.cptac.drugs }} </p>
                        <span class="dot dot_transcriptomics"></span> 
                        <span class="dot dot_proteomics"></span> 
                        <span class="dot dot_mutations"></span> 
                        <span class="dot dot_copy_number"></span> 
                    {% when 'hcmi' %}
                        <p>Cancer Types: {{ site.data.stats.hcmi.cancer_types }} </p>
                        <p>Genes: {{ site.data.stats.hcmi.genes }} </p>
                        <span class="dot dot_transcriptomics"></span> 
                        <span class="dot dot_proteomics"></span> 
                        <span class="dot dot_mutations"></span> 
                        <span class="dot dot_copy_number"></span> 
                    {% when 'beataml' %}
                        <p>Cancer Types: {{ site.data.stats.beataml.cancer_types }}</p>
                        <p>Genes: {{ site.data.stats.beataml.genes }}</p>
                        <p>Drugs: {{ site.data.stats.beataml.drugs }}</p>
                        <span class="dot dot_transcriptomics"></span> 
                        <span class="dot dot_proteomics"></span> 
                {% endcase %}
            </div>
        </div>
    {% endfor %}

</div>


<div class="legend">
    <p>Transcriptomics<span class="dot dot_transcriptomics"></span></p>
    <p>Proteomics<span class="dot dot_proteomics"></span></p>
    <p>Mutations<span class="dot dot_mutations"></span></p>
    <p>Copy Number<span class="dot dot_copy_number"></span></p>
</div>


### Data Overview

<div class="flex-container"> 
    <div class="flex-item">
        <embed src="{{ 'assets/stats/Fig0_Overview.pdf' | relative_url }}" type="application/pdf" />
    </div>
    <div class="flex-item">
        <embed src="{{ 'assets/stats/Fig5_Sample_Summary.pdf' | relative_url }}" type="application/pdf" />
    </div>
</div>
