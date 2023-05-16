#!/bin/bash

# This script prompts the user for a search term and a directory to search in,
# then performs a case-insensitive search for files and directories with names
# that match the search term. The script prints the last modification time and
# file path for each file found, sorted by modification time from newest to oldest.
#
# Usage:
# 1. Run the script.
# 2. Enter the search term when prompted (use regex if desired).
# 3. Enter the directory to search in when prompted (leave blank to search the entire filesystem).
#
# Example:
# $ ./megasearch.sh
# Search term: *.txt
# Directory to search in: /home/user/documents
#
# The above example searches for all .txt files in the /home/user/documents directory
# and prints the last modification time and file path for each file found, sorted by
# modification time from newest to oldest.

read -p "Search term: " searchTerm
read -p "Directory to search in: " searchDir

if [ -z "$searchDir" ]; then
    searchDir="/"
fi

find $searchDir -iname $searchTerm -print0 2>/dev/null | \
	xargs -0 ls -lt --time-style=long-iso | awk '{print $6,$7,$8,$9}'

