Running AWS files on ChimeraTE using tmux.

This code can run without using sandbox in Apptainer:
1. Using the container:

```
apptainer shell --writable-tmpfs --pwd /home/ec2-user/ChimeraTE --bind ~/repos/neondisco-teas/data:/home/ec2-user/ChimeraTE/projects/data chimerate_1.3.sif
```

How to run the example data for mode 1:
```
python3 chimTE_mode1.py --genome projects/data/ref/GRCh38.primary_assembly.genome.fa --input projects/data/metadata/B_input_379T.tsv --project data/output/mode1_test1 --te projects/data/input/hg38_TEs.gtf --gene projects/data/input/gencode.v49.primary_assembly.annotation.gtf --strand rf-stranded
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
  --bind ~/repos/neondisco-teas/data/output/index:/home/ec2-user/ChimeraTE/index \
  --bind ~/repos/neondisco-teas/data/output/tmp:/tmp \
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