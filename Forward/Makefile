# Makefile for Elmer
# ----------------------------------------
# Use external Geometry to create mesh
# Calculate Depth and Height for Paraview

EXECUTABLES = src/DistanceSolverRD 

NumProcs=100
NumProcx=10
NumProcy=10
NumProcz=1

InputSif=Forward.sif



.SUFFIXES: .f90

all: clean ini grid submit

grid:
	ElmerGrid 2 2 Mesh -metis 100 4  -autoclean

submit: ini

	mpirun -n 100 ElmerSolver_mpi

compile:  
#	elmerf90 src/AgeSolverRD.f90 -o src/AgeSolverRD
#	elmerf90 src/AgeSolver.f90 -o src/AgeSolver
#	elmerf90 src/DistanceSolveRD.f90 -o src/DistanceSolveRD
#	elmerf90 src/BedrockBump.f90 -o src/BedrockBump
#	elmerf90 src/GroundedMaskSolver.f90 -o src/GroundedMaskSolver
#	elmerf90 src/SeaLevel.f90 -o src/SeaLevel
#	elmerf90 src/USF_BMB.f90 -o src/USF_BMB; elmerf90 -o src/USF_Contact src/USF_Contact.f90 src/USF_Sliding.f90

clean:
	rm -fr results/*

ini:
	echo Forward.sif > ELMERSOLVER_STARTINFO

.f90:
	elmerf90  -o Forward.sif 10 10 1 100 Mistral $<
.c:
	gcc  -o Forward.sif 10 10 1 100 Mistral $< -lm
