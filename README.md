# Slides for BOSH 2.0 talk

### Description

The presentation consists of two parts: Keynotes slides and slides that are based on Concourse pipelines. All necessary assets to work with concourse-pipelined slides are stored in `concourse-slides` folder. Concourse-pipelined slides are generated from `slides.yml` file and every slide is a separate pipeline. Concourse-pipelined slides can be switched with scripts from `concourse-slides/bin` folder.

### How to run concourse-pipelined slides

After you have running concourse installation you'll need install `fly` concourse cli and target this installation. After that you'll just need to execute `next-slide` and `previous-slide` from `concourse-slides/bin` folder. This will create `slide-number` file with number of current version.

### Personal Notes

* I use `FastScript` to run scripts with a shortcuts, run following commands before the presentation from this folder:

```bash
slide_direction=( next previous )
for direction in "${slide_direction[@]}"; do
   cat << EOF > $HOME/Library/Scripts/presentation/$direction-slide
#!/usr/bin/env bash
$PWD/concourse-slides/bin/$direction-slide
EOF
done

sudo chmod +x $HOME/Library/Scripts/presentation/*-slide
```
