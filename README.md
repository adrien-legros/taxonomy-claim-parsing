```shell
ilab model download --repository docker://registry.redhat.io/rhelai1/granite-7b-starter --release latest
ilab model download --repository docker://registry.redhat.io/rhelai1/prometheus-8x7b-v2-0 --release latest
ilab model download --repository docker://registry.redhat.io/rhelai1/skills-adapter-v3 --release latest
ilab model download --repository docker://registry.redhat.io/rhelai1/knowledge-adapter-v3 --release latest
#ilab model download --repository docker://registry.redhat.io/rhelai1/granite-7b-redhat-lab --release latest
ilab model download --repository mistralai/Mistral-7B-Instruct-v0.2 --hf-token $HF_TOKEN
git clone https://github.com/adrien-legros/taxonomy-claim-parsing.git
ilab data generate --taxonomy-path ~/taxonomy-claim-parsing/ --model ~/.cache/instructlab/models/mistralai/Mistral-7B-Instruct-v0.2 --enable-serving-output --gpus 4
ilab model train --data-path ~/.local/share/instructlab/datasets/node_datasets_2024-09-27T12_37_40/compositional_skills_json_processing.jsonl --enable-serving-output --gpus 4
ilab model serve --model-path /var/home/instruct/.local/share/instructlab/checkpoints/hf_format/samples_976
ilab model chat --model /var/home/instruct/.local/share/instructlab/checkpoints/hf_format/samples_976
```