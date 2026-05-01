# Dendritic Neural Networks with Equilibrium Propagation

This repository contains the official implementation of the paper:

**"Dendritic Neural Networks with Equilibrium Propagation"**  
Yoshimasa Kubo, Lakehead University

---

## 🧠 Overview

Equilibrium Propagation (EP) is a biologically plausible alternative to backpropagation, but its performance can degrade in deeper and more complex learning settings.

In this work, we integrate **dendritic neural network architectures** with EP, introducing structured processing of feedforward (basal) and feedback (apical) signals.

Our contributions include:
- Combining dendritic neurons with EP (DEP)
- Demonstrating improved performance on challenging datasets
- Providing insight into internal dynamics via hidden-state trajectory analysis

---

## 📊 Results Summary

- Comparable performance to standard EP on MNIST
- Significant improvements on:
  - KMNIST
  - Fashion-MNIST (FMNIST)
- Competitive with dendritic networks trained using BPTT

We also show that DEP produces:
- Higher activation magnitudes
- More distributed hidden-state representations

---

## Standard EP
python main_dendritic.py --model DMLP --task MNIST --archi 784 256 10 \
--basal-branches 8 --apical-branches 2 --branch-sparsity 0.5 --apical-scale 0.2 \
--alg EP --thirdphase --save --betas 0.0 0.1 --T1 60 --T2 12 --mbs 64 --epochs 20 \
--act hard_sigmoid --optim sgd --lrs 0.4 0.02 --mmt 0.9 --seed 1

## Dendritic EP (DEP)
python main_dendritic.py --model MLP --task MNIST --archi 784 256 10 \
--alg EP --thirdphase --save --betas 0.0 0.1 --T1 60 --T2 12 --mbs 64 \
--epochs 20 --act hard_sigmoid --optim sgd --lrs 0.4 0.02 --mmt 0.9 --seed 1 

## Dendritic BPTT (DBPTT)
python main_dendritic.py --model DMLP --task MNIST --archi 784 256 10 \
  --basal-branches 8 --apical-branches 2 --branch-sparsity 0.5 --apical-scale 0.2 \
  --alg BPTT --thirdphase --save --betas 0.0 0.1 --T1 60 --T2 12 --mbs 64 --epochs 20 \
  --act hard_sigmoid --optim sgd --lrs 0.4 0.02 --mmt 0.9 --seed 1

