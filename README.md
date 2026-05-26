# AdvMal-TF
We present a dataset of adversarial malware samples derived from the public [RawMal-TF](https://github.com/CS-and-AI/RawMal-TF) collection of real-world malware binaries. Using a suite of adversarial malware generators, we construct two sets of adversarial PE files: 44,347 family-labelled samples and 33,596 type-labelled samples, achieving evasion rates of 98.35% and 92.20% against the EMBER classifier, respectively. Each adversarial binary is accompanied by detailed metadata, including EMBER scores and VirusTotal classifications. We further demonstrate the susceptibility of malware classification pipelines to data poisoning attacks through a series of training experiments. Injecting fully mislabelled adversarial samples representing only 0.5% of the training data in the family-labelled dataset increases the evasion rate against the re-trained classifier from 26.1% to 92.8%. The dataset is publicly released to facilitate future research on adversarial malware, poisoning attacks, and the robustness of machine-learning-based malware detection systems. 

## Download

| Dataset | Size (compressed) | Size (uncompressed) | # Samples |
| ------- | ----------------- | ------------------- | --------- |
| Family-labelled | 30 GB | 61 GB | 44,347 |
| Type-labelled   | 45 GB | 82 GB | 33,596 |

The dataset with raw binary files and JSON metadata is available for download from [Google Drive](https://drive.google.com/drive/folders/1nlBkE72J3oQmOQrMoF2GzNotYraltWE4?usp=sharing).


## Metadata format
| Field | Type | Description |
|---|---|---|
| `source_sha256` | string | SHA-256 hash of the original binary |
| `sample_sha256` | string | SHA-256 hash of the adversarial binary |
| `source_path` | string | Path of the source binary, relative to the dataset root |
| `label` | string | Family/type label of the source sample |
| `generator` | string | Display name of the adversarial generator that produced the chosen variant |
| `sample_path` | string | Path of the chosen adversarial variant, relative to its generator's output root |
| `source_file_size_bytes` | int | Size of the source binary in bytes |
| `adversarial_file_size_bytes` | int | Size of the chosen adversarial binary in bytes |
| `ember2018_orig_score` | float | EMBER score for the source binary |
| `ember2018_orig_is_malicious` | bool | Source verdict under EMBER |
| `ember2018_adv_score` | float | EMBER score for the adversarial binary |
| `ember2018_adv_is_malicious` | bool | Adversarial verdict under EMBER |
| `ember2024_orig_score` | float | EMBER2024 score for the source binary |
| `ember2024_orig_is_malicious` | bool | Source verdict under EMBER2024 |
| `ember2024_adv_score` | float | EMBER2024 score for the adversarial binary |
| `ember2024_adv_is_malicious` | bool | Adversarial verdict under EMBER2024 |
| `vt_orig_detections` | string | VirusTotal detection ratio for the source binary, formatted as `M/T` where M is the number of engines flagging the file as malicious and T = M + suspicious + undetected + harmless (excludes failed verdicts) |
| `vt_adv_detections` | string | Same as above, computed for the adversarial binary |
| `vt_orig_top10` | object | Per-engine verdicts for selected ten top antivirus products (anonymised). Each value is `"malicious"`, `"benign"`, or `null` if the engine returned no verdict |
| `vt_adv_top10` | object | Same shape as above, evaluated on the adversarial binary |

## Citing

If you use this dataset in your research, please cite our [paper](https://arxiv.org/abs/2605.25937).

```bibtex
@misc{kostal2026buildingadversarialmalwaredataset,
    title={Building an Adversarial Malware Dataset by Family and Type: Generation, Evasion, and Poisoning Evaluation}, 
    author={David Košťál and Martin Jureček},
    year={2026},
    eprint={2605.25937},
    archivePrefix={arXiv},
    primaryClass={cs.CR},
    url={https://arxiv.org/abs/2605.25937}, 
}
```