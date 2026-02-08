A tool for shell scripts. Leverage the power of Bubbles and Lip Gloss in your scripts and aliases without writing any Go or Shell code!


# Customization

You can customize `bash-utils` options and styles with --flags. See `bash-utils` <command> --help for a full view of each command's customization and configuration options.

```bash 
gum input --prompt.foreground "212" \
          --placeholder "What's up?" \
          --prompt "* " \
          --width 80 \
          --value "Not much, hby?"
```

---

# Input 

---

Prompt for input with a simple command.

```bash
./bash-utils input > answer.txt 
./bash-utils input --password > password.txt
```

---

# Write

---

Prompt for some multi-line text (ctrl+d to complete text entry).

```bash 
./bash-utils write > story.txt
```

--- 

# Filter

---

Filter a list of values with fuzzy matching:

```bash 
echo Strawberry >> flavors.txt
echo Banana >> flavors.txt
echo Cherry >> flavors.txt
./bash-utils filter < flavors.txt > selection.txt 
```

Select multiple options with the `--limit` flag or `--no-limit` flag. Use `tab` or `ctrl+space` to select, enter to confirm.

```bash 
cat flavors.txt | ./bash-utils filter --limit 2
cat flavors.txt | ./bash-utils filter --no-limit
```

---

# Choose

---

Choose an option from a list of choices.

```bash 
echo "Pick a card, any card..."
CARD=$(./bash-utils choose --height 15 {{A,K,Q,J},{10..2}}" "{♠,♥,♣,♦})
echo "Was your card the ${CARD:?}?"
```

You can also select multiple items with the --limit or --no-limit flag, which determines the maximum of items that can be chosen.

```bash
cat songs.txt | ./bash-utils choose --limit 5
cat foods.txt | ./bash-utils choose --no-limit --header "Grocery Shopping"
```

---

# Confirm

---

Confirm whether to perform an action. Exits with code 0 (affirmative) or 1 (negative) depending on selection.

```bash 
./bash-utils confirm && rm file.txt || echo "File not removed"
```

---

# File

---

Prompt the user to select a file from the file tree.

```bash 
${EDITOR:-nano} $(gum file "${HOME:?}")
```

> [!TIP] Tip 
> Or, so much better!
>
> ```bash
> ./bash-utils file \
>     --header.title.foreground=7 \
>     --header.border.foreground=212 \
>     --header.title.background=212 \
>     --header.text="%{PATH}%" \
>     --padding="1 0" \
>     --header.title.transmit-color="title to preffix" \
>     --header.text.background="" \
>     --header.text.foreground=7 \
>     --path.foreground=7 \
>     --all 
> # Parameter --all if u wanna se hidden files.
> ```

---

# Pager

---

Scroll through a long document with line numbers and a fully customizable viewport.

```bash 
./bash-utils pager < README.md 
```

---

# Spin

---

Display a spinner while running a script or command. The spinner will automatically stop after the given command exits.

To view or pipe the command's output, use the --show-output flag.

```bash 
./bash-utils spin --spinner dot --title "Buying Bubble Gum..." -- sleep 5
```

---

Available spinner types include: `dot`,`line`,`minidot`,`jump`,`pulse`,`points`,`globe`,`moon`,`monkey`,`meter`,`hamburger`,`standard`,`bar`,`process`.

# Table

---

Select a row from some tabular data.

```bash 
./bash-utils table < flavors.csv | cut -d ',' -f 1 
# Or using files 
ls -lh | awk '{print $9 "," $2}' | ./bash-utils table --columns "Permisos,Propietario" --border-foreground=212 
```

---

# Style

---

Pretty print any string with any layout with one command.

```bash 
gum style \
	--foreground 212 --border-foreground 212 --border double \
	--align center --width 50 --margin "1 2" --padding "2 4" \
	'Bubble Gum (1¢)' 'So sweet and so fresh!'
```

---

# Log

---

log logs messages to the terminal at using different levels

```bash 
# Log some debug information.
gum log --structured --level debug "Creating file..." name file.txt
# DEBUG Unable to create file. name=temp.txt

# Log some error.
gum log --structured --level error "Unable to create file." name file.txt
# ERROR Unable to create file. name=temp.txt

# Include a timestamp.
gum log --time rfc822 --level error "Unable to create file."
```

---

# Messagebox 

---

logs message into box 

```bash 
./bash-utils messagebox \
  --title=" Warn " \
  --type="Warning" \
  --title.align=center \
  --preffix.pad="1 0" \
  --message="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum." \
  --border="rounded" \
  --bold \
  --italic \
  --title.foreground="" \
  --title.background=0 \
  --preffix.background=0 \
  --preffix.foreground=""
```

---

# Text 

---

Show beautifiul text in terminal, with gradient effect! 

```bash 
./bash-utils text "♥ https://SelfDreamer.github.io" --bold --align=center 
```

---

<div align="center">
    A tool inspired by <a href="https://github.com/charmbracelet/gum">gum</a>, I hope you like it!! ^^
</div>
