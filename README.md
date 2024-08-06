# Regex Cheatsheet

## Introduction
Testing your regular expressions can be done in two ways:
1. **Create a text file** with some test paragraphs on a Unix machine, then use `egrep <pattern> <file>` to see what matches and what doesn't.
2. **Use an online editor** like [regexr.com](https://regexr.com/). Add your text in the "Text" field and type your expressions in the "Expression" field. This method is highly recommended for ease of use.

## Charsets
When searching for specific strings or patterns in a file or block of text, regular expressions (regex) come in handy.

### Basic Charsets
- `[abc]`: Matches any occurrence of 'a', 'b', or 'c'.
- `[abc]zz`: Matches 'azz', 'bzz', and 'czz'.

### Ranges
- `[a-c]zz`: Same as above.
- `[a-cx-z]zz`: Matches 'azz', 'bzz', 'czz', 'xzz', 'yzz', and 'zzz'.
- `[a-zA-Z]`: Matches any single letter (lowercase or uppercase).
- `file[1-3]`: Matches 'file1', 'file2', and 'file3'.

### Exclusions
- `[^k]ing`: Matches 'ring', 'sing', '$ing', but not 'king'.
- `[^a-c]at`: Matches 'fat' and 'hat', but not 'bat' or 'cat'.

### Notes
1. Charsets match any occurrence of the specified characters, not just strings.
2. Type characters in the same order as the questions to avoid confusion.
3. Efficient regex means:
   - Be specific: Use `[a-c]` instead of `[a-z]` if only matching 'a' to 'c'.
   - Don't be too specific: Use `[a-z]` for a broader range to avoid complexity.

## Practical Examples
1. **Match characters `c`, `o`, `g`:**

   ```regex
   [cog]
   ```

2. **Match words `cat`, `fat`, `hat`:**
   
   ```regex
   [cfh]at
   ```

3. **Match words `Cat`, `cat`, `Hat`, `hat`:**
   ```regex
   [CcHh]at
   ```

4. **Match filenames `File1`, `File2`, `file3`, `file4`, `file5`, `File7`, `file9`:**
   
   ```regex
   [Ff]ile[1-9]
   ```

5. **Match all filenames except "File7":**
   
   ```regex
   [Ff]ile[^7]
   ```


## Wildcards and Optional Characters
- `.`: Matches any single character except the line break.
- `?`: Makes the preceding character optional.

### Practical Examples
1. **Match words `Cat`, `fat`, `hat`, `rat`:**

   ```regex
   .at
   ```

3. **Match words `Cat`, `cats`:**

   ```regex
   [Cc]ats?
   ```

4. **Match domain name `cat.xyz`:**

   ```regex
   cat\.xyz
   ```

5. **Match domain names `cat.xyz`, `cats.xyz`, `hats.xyz`:**

   ```regex
   [ch]ats?\.xyz
   ```

6. **Match 4-letter strings not ending with letters `n` to `z`:**

   ```regex
   ...[^n-z]
   ```


## Metacharacters and Repetitions
### Basic Metacharacters
- `\d`: Matches a digit.
- `\D`: Matches a non-digit.
- `\w`: Matches an alphanumeric character.
- `\W`: Matches a non-alphanumeric character.
- `\s`: Matches a whitespace character.
- `\S`: Matches everything else.

### Repetitions
- `{n}`: Matches exactly `n` times.
- `{n,m}`: Matches between `n` and `m` times.
- `{n,}`: Matches `n` or more times.
- `*`: Matches 0 or more times.
- `+`: Matches 1 or more times.

### Practical Examples
1. **Match word `catssss`:**

   ```regex
   cats{4}
   ```

3. **Match words `Cat`, `cats`, `catsss`:**

   ```regex
   [Cc]ats*
   ```

4. **Match sentences `regex go br`, `regex go brrrrrr`:**

   ```regex
   regex go br+
   ```

5. **Match filenames `ab0001`, `bb0000`, `abc1000`, `cba0110`, `c0000`:**

   ```regex
   [abc]{1,3}[01]{4}
   ```

6. **Match filenames `File01`, `File2`, `file12`, `File20`, `File99`:**

   ```regex
   [Ff]ile\d{1,2}
   ```


## Start/End Patterns, Groups, and Either/Or
### Start/End Characters
- `^`: Matches the start of a line.
- `$`: Matches the end of a line.

### Groups and Either/Or
- `(pattern)`: Defines a group.
- `|`: Specifies an either/or pattern.

### Practical Examples
1. **Match string starting with "Password:" followed by 10 characters excluding "0":**

   ```regex
   Password:[^0]{10}
   ```

3. **Match "username: " at the beginning of a line:**

   ```regex
   ^username:\s
   ```

4. **Match lines not starting with a digit:**

   ```regex
   ^\D
   ```

5. **Match string `EOF$` at the end of a line:**

   ```regex
   EOF\$$
   ```

6. **Match sentences `I use nano` and `I use vim`:**

   ```regex
   I use (nano|vim)
   ```

7. **Match lines starting with `$` followed by a digit, another `$`, and non-whitespace characters:**

   ```regex
   \$\d\$\S+
   ```

8. **Match any IPv4 address:**

   ```regex
   (\d{1,3}\.){3}\d{1,3}
   ```

10. **Match emails `hello@tryhackme.com`, `username@domain.com`, `dummy_email@xyz.com` and group the username and domain:**
   
   ```regex
   (\w+)@(\w+)\.com


---

This cheatsheet provides a comprehensive guide to regular expressions, ensuring you can effectively search and manipulate text patterns. 
