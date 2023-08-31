import numpy as np
import pandas as pd
# from keras.models import Sequential
# from keras.layers import Dense
# from keras.layers import Dropout
# from keras.layers import LSTM
# from keras.utils import np_utils

text = '"A natural image usually conveys rich semantic content and can be viewed from different angles. Existing image description methods are largely restricted by small sets of biased visual paragraph annotations"'
text=text.lower()

characters = sorted(list(set(text)))
n_to_char = {n:char for n, char in enumerate(characters)}
char_to_n = {char:n for n, char in enumerate(characters)}

X = []
Y = []
length = len(text)
seq_length = 100
for i in range(0, length-seq_length, 1):
   sequence = text[i:i + seq_length]
   label =text[i + seq_length]
   X.append([char_to_n[char] for char in sequence])
   Y.append(char_to_n[label])
print("Test Data - ",Y)
