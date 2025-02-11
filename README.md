#!/bin/sh
mcr(){ while read -r i; do eval "$( printf "%s" "$i" | awk "$1" ; )" ; done ; } &&
mcrsh(){ while read -r i; do eval "$i"; done ; }
edtrnlp(){ while : ; do edtrnlp_file="/dev/shm/edtrnlp_output_$$" && "$1" "$3" && cat "$3" | mcrsh > "$edtrnlp_file" && "$1" "$edtrnlp_file" && rm "$edtrnlp_file" ; done ; } &&
vimcrsh(){ edtrnlp vi mcrsh "$1" ; } &&
vimcrsh "$1"
