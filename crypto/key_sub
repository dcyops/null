#!/bin/bash

# Check if ciphertext is provided
if [ -z "$1" ]; then
    echo "Usage: $0 <ciphertext>"
    exit 1
fi

ciphertext="$1"

# Function to decrypt using Caesar cipher with the given key
decrypt_caesar() {
    local text="$1"
    local shift="$2"
    echo "$text" | tr 'A-Za-z' "$(echo {A..Z} {A..Z} {a..z} {a..z} | tr -d ' ' | cut -c$((shift + 1))-$(($shift + 26)),$((shift + 27))-$(($shift + 52)))"
}

# Function to reverse Caesar cipher with the given key
decrypt_reverse_caesar() {
    local text="$1"
    local shift="$2"
    echo "$text" | tr 'A-Za-z' "$(echo {Z..A} {Z..A} {z..a} {z..a} | tr -d ' ' | cut -c$((shift + 1))-$(($shift + 26)),$((shift + 27))-$(($shift + 52)))"
}

# Loop through keys from 1 to 20 for normal Caesar cipher decryption
for key in {1..20}; do
    echo "Attempt with forward shift key size $key:"
    decrypt_caesar "$ciphertext" $key
    echo ""
done

# Loop through keys from 1 to 20 for reverse Caesar cipher decryption
for key in {1..20}; do
    echo "Attempt with reverse shift key size $key:"
    decrypt_reverse_caesar "$ciphertext" $key
    echo ""
done

