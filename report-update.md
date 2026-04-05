Running AWS files on ChimeraTE using tmux.

This code can run without using sandbox:
1. Using the container:

```
apptainer shell --writable-tmpfs --pwd /home/ec2-user/ChimeraTE --bind ~/repos/data/output:/home/ec2-user/ChimeraTE/projects/test_out chimerate_1.3.sif
```

How to run the example data:
```
python3 chimTE_mode1.py --genome example_data/mode1/dmel_genome_sample.fa --input example_data/mode1/input_mode1.tsv --project test_out --te example_data/mode1/dmel_TEs_sample.gtf --gene example_data/mode1/dmel_genes_sample.gtf --strand rf-stranded
```

2. A. Using our own data from AWS (VERY EASY TO UNDERSTAND PATHWAYS):
```
apptainer shell --writable-tmpfs \
  --pwd /home/ec2-user/ChimeraTE \
  --bind ~/repos/neondisco-teas/data/output:/home/ec2-user/ChimeraTE/projects/test_out \
  --bind ~/repos/neondisco-teas/data/input:/home/ec2-user/ChimeraTE/projects/input_data \
  --bind ~/repos/neondisco-teas/data/metadata:/home/ec2-user/ChimeraTE/projects/metadata \
  chimerate_1.3.sif
  ```

How to run the AWS data:
```
python3 chimTE_mode2.py \
  --input projects/metadata/A_input_379T.tsv \
  --project test_out \
  --transcripts projects/input_data/human_transcripts_chimeraTE.fa \
  --te projects/input_data/hg38_TE_sequences.fa \
  --ref_TEs human \
  --strand rf-stranded \
  --threads 8 \
  --ram 16 \
  --assembly
```

3. Convenient apptainer shell:
```
apptainer shell --writable-tmpfs \
  --pwd /home/ec2-user/ChimeraTE \
  --bind ~/repos/neondisco-teas/data:/home/ec2-user/ChimeraTE/projects/data \
  chimerate_1.3.sif
  ```

```
python3 chimTE_mode2.py \
  --input projects/data/metadata/B_input_379T.tsv \
  --project data/output \
  --transcripts projects/data/input/human_transcripts_chimeraTE.fa \
  --te projects/data/input/hg38_TE_sequences.fa \
  --ref_TEs human \
  --strand rf-stranded \
  --threads 8 \
  --ram 16 \
  --assembly
```