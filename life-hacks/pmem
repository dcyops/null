#!/bin/bash

read -sp "Enter your password: " password
echo

# Define the initial chunk size
chunk_size=4
length=${#password}

# Function to quiz the user on chunks of a specified size
quiz_user() {
    local chunk_size=$1
    echo "Now, you need to remember the password in chunks of $chunk_size characters."

    for (( i=0; i<$length; i+=$chunk_size )); do
        chunk="${password:$i:$chunk_size}"
        echo -e "${chunk}\nClearing in 5s..."
        sleep 5
        clear
        while true; do
            read -p "Enter the next $chunk_size-character chunk: " user_input
            if [[ "$user_input" == "$chunk" ]]; then
                echo "Correct!"
                break
            else
                echo "Not correct, try again."
            fi
        done
    done
}

# Start with the initial chunk size and increase the chunk size after each round
current_chunk_size=$chunk_size

while [[ $current_chunk_size -le $length ]]; do
    quiz_user $current_chunk_size
    current_chunk_size=$((current_chunk_size + chunk_size))
done

echo "Congratulations! You remembered the entire password in increasingly larger chunks."

