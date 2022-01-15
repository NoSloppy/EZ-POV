OUTPUT ?= $(wildcard *.png)
ALL: image.h image_pgm.h preview.png

# Full-Color images
image.h: pnmtorle pnmwindshieldwiper *.png
	pngtopnm $(basename $(OUTPUT)).png | ./pnmwindshieldwiper | pnmscale -height 144 | ./pnmtorle > $(basename $(OUTPUT))_FC_POV_data.h

#Single-Color images
image_pgm.h: pgmtorle pnmwindshieldwiper *.png
	pngtopnm $(basename $(OUTPUT)).png | ./pnmwindshieldwiper | pnmscale -height 144 | ./pgmtorle > $(basename $(OUTPUT))_SC_POV_data.h

preview.png: pnmwindshieldwiper *.png
	pngtopnm $(basename $(OUTPUT)).png | ./pnmwindshieldwiper | pnmscale -height 144 | pnmtopng > $(basename $(OUTPUT))_preview.png

pnmtorle: pnmtorle.cc
	g++ -O2 pnmtorle.cc -o pnmtorle -g -lm

pgmtorle: pgmtorle.cc
	g++ -O2 pgmtorle.cc -o pgmtorle -g -lm

pnmwindshieldwiper: pnmwindshieldwiper.cc
	g++ -O2 pnmwindshieldwiper.cc -o pnmwindshieldwiper -g -lm

pnmtoblc: pnmtoblc.cc
	g++ -O2 pnmtoblc.cc -o pnmtoblc -g -lm

