
# Summary of Shells in windows

## Table of contents

* [Summary of Shells in windows](#summary-of-shells-in-windows)
  * [Table of contents](#table-of-contents)
  * [Table of Table of Contents](#table-of-table-of-contents)
  * [Command Prompt](#command-prompt)
    * [shortcut | hotkeys | keybinds](#shortcut--hotkeys--keybinds)
    * [command history](#command-history)
    * [asking for help](#asking-for-help)
      * [the help's syntax structure](#the-helps-syntax-structure)
      * [Examples](#examples)
    * [list commands](#list-commands)
    * [writing comments](#writing-comments)
    * [Referencing variables](#referencing-variables)
  * [Powershell](#powershell)
    * [shortcut | hotkeys | keybinds](#shortcut--hotkeys--keybinds-1)
    * [command history](#command-history-1)
    * [asking for help](#asking-for-help-1)
      * [Examples](#examples-1)
    * [list commands](#list-commands-1)
    * [writing comments](#writing-comments-1)
  * [WSL (Windows Subsystem for Linux)](#wsl-windows-subsystem-for-linux)
    * [asking for help](#asking-for-help-2)
    * [Referencing variables](#referencing-variables-1)
  * [Cygwin](#cygwin)
  * [MSYS](#msys)

## Table of Table of Contents

```diff
-sort the table of contents as a comparison table between everything
```

----------

## [Command Prompt](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands)

----------

```diff
-TODO brief summary about the origins of command prompt, what it is used for, what it can't do. deprecation?
-TODO can command prompt do pipes?
-TODO command prompt is a dos artifact, cmd.exe command.exe, link to article about feature differences.
-TODO current shipped version, why should you care? or shouldn't you. maybe because it is old there are still programs but everything is moving towards powershell.
```

### shortcut | hotkeys | keybinds

* [general keybinds](https://ss64.com/nt/syntax-keyboard.html#btn:~:text=Keyboard%20shortcuts%20for%20the%20Windows%20CMD%20shell%20and%20PowerShell)

* [hisotry related keybinds](https://ss64.com/nt/syntax-keyboard.html#btn:~:text=CMD%20shell%20Command%20History%20shortcuts)

### command history

* `UP/DOWN Arrow` keys scrolling
* searching for matches in history with `F8`
* display history `F7`
* print history `doskey /history`

### asking for help

```cmd
help [command]
command /?
```

#### [the help's syntax structure](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/command-line-syntax-key)

```text x
command <required-value-placeholder> [optional block] {required-one out-of set} (optional|mutually|exclusive) (repeatable)
```

#### Examples

1. Basic usage

    ```cmd
    copy /?
    ```

    <!-- #region(collapsed) output -->
    <details>
    <summary>output</summary>

    ```text
    Copies one or more files to another location.

    COPY [/D] [/V] [/N] [/Y | /-Y] [/Z] [/L] [/A | /B ] source [/A | /B]
        [+ source [/A | /B] [+ ...]] [destination [/A | /B]]

    source       Specifies the file or files to be copied.
    /A           Indicates an ASCII text file.
    /B           Indicates a binary file.
    /D           Allow the destination file to be created decrypted
    destination  Specifies the directory and/or filename for the new file(s).
    /V           Verifies that new files are written correctly.
    /N           Uses short filename, if available, when copying a file with a
                non-8dot3 name.
    /Y           Suppresses prompting to confirm you want to overwrite an
                existing destination file.
    /-Y          Causes prompting to confirm you want to overwrite an
                existing destination file.
    /Z           Copies networked files in restartable mode.
    /L           If the source is a symbolic link, copy the link to the target
                instead of the actual file the source link points to.

    The switch /Y may be preset in the COPYCMD environment variable.
    This may be overridden with /-Y on the command line.  Default is
    to prompt on overwrites unless COPY command is being executed from
    within a batch script.

    To append files, specify a single file for destination, but multiple files
    for source (using wildcards or file1+file2+file3 format).
    ```

    </details>
    <!-- #endregion -->

### list commands

```cmd
help
```

```diff
-TODO
```

### writing comments

Writing comments can be done by prepending `::` or `REM` to a line. comments aren't executed.

```diff
-todo the difference between :: and rem
```

Example:

```cmd
@echo off
echo Hello
rem echo World
echo That was a comment
::This is also a comment
```
<!-- #region(collapsed) output-->
<details>
<summary>output</summary>

```cmd
Hello
That was a comment
```

</details>
<!-- #endregion -->

### Referencing variables

by wrapping the a variable name with two `%` a variable named `VARIABLE` can be referenced by typing `%VARIABLE%`.
Example:

```cmd
echo %userprofile%
```
<!-- #region(collapsed) output -->
<details>
<summary>output</summary>
Note: The current user is named `user`
```text
C:\Users\user
```
</details>
<!-- #endregion -->

Issues and solutions: since command prompt "expands"(evaluates) the variable at parsing time the resulting value is the initial one. this can cause problems in loops. to resolve this issue an the `SETLOCAL EnableDelayedExpansion` was added.
to "late expand" a variable wrap the variable's name with `!`, `!VARIABLE!`  
Example:

```diff
-TODO CMD delayed expantion loop example with %% and !!
```

```cmd
Example placeholder
```

----------

## [Powershell](https://docs.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7)

----------

Powershell is a `.NET` object based shell. It support similar functionality to other shells such as pipes (chaining multiple cmdlets) by passing and manipulating .NET objects rather than `raw text`.  
Note, as of October 2020 (10/2020) the default version of powershell is 5.1 make to use the right documentation.

```diff
-TODO insert more functionalities that powershell support compared to other shells.
```

### shortcut | hotkeys | keybinds

* [general keybinds](https://ss64.com/nt/syntax-keyboard.html#btn:~:text=Keyboard%20shortcuts%20for%20the%20Windows%20CMD%20shell%20and%20PowerShell)

### command history

```diff
-todo, ctrl+r and #tabcomplition
```

### asking for help

<!-- #region Use Update Help First -->
<details open>
 <summary>please run `Update-Help` first, see more:</summary>

  [*Why you need to run this at all?*](https://docs.microsoft.com/en-us/powershell/scripting/learn/ps101/02-help-system?view=powershell-7#code-try-1:~:text=Beginning%20with%20PowerShell%20version%203%2C%20PowerShell,cmdlet%2C%20you%20don't%20receive%20this%20prompt.)

> Beginning with PowerShell version 3, PowerShell help doesn't ship with the operating system. The first time Get-Help is run for a command, the previous message is displayed. If the help function or man alias is used instead of the Get-Help cmdlet, you don't receive this prompt.

```powershell
Update-help
```

  Note: this command errors out. this is a [known behavior](https://answers.microsoft.com/en-us/windows/forum/all/updateing-powershell-user-help-files/07afd880-c543-4e56-9446-1e9eb509003d). use `Update-Help -ErrorAction SilentlyContinue` if you want to avoid the error.
 <!-- #region(collapsed) output -->
 <details>
  <summary>output</summary>
  
```text
Update-help : Failed to update Help for the module(s) 'HostNetworkingService, PSReadline' with UI culture(s) {en-US} :
Unable to retrieve the HelpInfo XML file for UI culture en-US. Make sure the HelpInfoUri property in the module
manifest is valid or check your network connection and then try the command again.
At line:1 char:1
+ Update-help
+ ~~~~~~~~~~~
    + CategoryInfo          : ResourceUnavailable: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToRetrieveHelpInfoXml,Microsoft.PowerShell.Commands.UpdateHelpCommand

Update-help : Failed to update Help for the module(s) 'HgsClient, HgsDiagnostics' with UI culture(s) {en-US} : Unable
to connect to Help content. The server on which Help content is stored might not be available. Verify that the server
is available, or wait until the server is back online, and then try the command again.
At line:1 char:1

+ Update-help
+
+
+ ~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Update-Help], Exception
    + FullyQualifiedErrorId : UnableToConnect,Microsoft.PowerShell.Commands.UpdateHelpCommand

```

 </details>
 <!-- #endregion -->

</details>
<!-- #endregion -->

powershell has a standard way to ask for help details of `command`s:

> You can also type `help` or `man`, which displays one screen of text at a time. Or, `<cmdlet-name> -?`, that is         identical to `Get-Help`, but only works for cmdlets.

```powershell
Get-Help -Name <cmdlet>
Get-Help <cmdlet> (-online|-full|-detailed|-example|-parameter|-showwindow)
help [command]
man [command]
<command> -?
```

#### Examples  

1. basic usage

    ```powershell
    copy-item -?
    ```

    <!-- #region(collapsed) output -->
    <details>
    <summary>output</summary>

    ```text
    NAME
        Copy-Item

    SYNTAX
        Copy-Item [-Path] <string[]> [[-Destination]
        <string>] [-Container] [-Force] [-Filter <string>]
        [-Include <string[]>] [-Exclude <string[]>]
        [-Recurse] [-PassThru] [-Credential <pscredential>]
        [-WhatIf] [-Confirm] [-UseTransaction]
        [-FromSession <PSSession>] [-ToSession <PSSession>]
        [<CommonParameters>]

        Copy-Item [[-Destination] <string>] -LiteralPath
        <string[]> [-Container] [-Force] [-Filter <string>]
        [-Include <string[]>] [-Exclude <string[]>]
        [-Recurse] [-PassThru] [-Credential <pscredential>]
        [-WhatIf] [-Confirm] [-UseTransaction]
        [-FromSession <PSSession>] [-ToSession <PSSession>]
        [<CommonParameters>]


    ALIASES
        cpi
        cp
        copy


    REMARKS
        Get-Help cannot find the Help files for this cmdlet
        on this computer. It is displaying only partial
        help.
            -- To download and install Help files for the
        module that includes this cmdlet, use Update-Help.
            -- To view the Help topic for this cmdlet
        online, type: "Get-Help Copy-Item -Online" or
            go to
        https://go.microsoft.com/fwlink/?LinkID=113292.
    ```

    </details>
    <!-- #endregion -->

2. powershell can also open the online documentation:

    ```powershell
    Get-Help copy -Online
    ```

    This will open the [online documentation for Copy-Item](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/copy-item?view=powershell-5.1&WT.mc_id=ps-gethelp)

3. The Get-Help command can provide a lot of detail about `cmdlet`s with the `-example` `-parameter` flags.  

    ```powershell
    Get-Help Get-Help -example
    ```

    <!-- #region(collapsed) output-->
    <details>
    <summary>output</summary>

    ```text
    NAME
        Get-Help

    SYNOPSIS
        Displays information about PowerShell commands and concepts.


        --- Example 1: Display basic help information about a cmdlet ---

        Get-Help Format-Table
        Get-Help -Name Format-Table
        Format-Table -?

        `Get-Help <cmdlet-name>` is the simplest and default syntax of `Get-Help` cmdlet. You can omit the Name parameter.

        The syntax `<cmdlet-name> -?` works only for cmdlets.
        --- Example 2: Display basic information one page at a time ---

        help Format-Table
        man Format-Table
        Get-Help Format-Table | Out-Host -Paging

        `help` is a function that runs `Get-Help` cmdlet internally and displays the result one page at a time.

        `man` is an alias for the `help` function.

        `Get-Help Format-Table` sends the object down the pipeline. `Out-Host -Paging` receives the output from the
        pipeline and displays it one page at a time. For more information, see Out-Host (Out-Host.md).
        ------- Example 3: Display more information for a cmdlet -------

        Get-Help Format-Table -Detailed
        Get-Help Format-Table -Full

        The Detailed parameter displays the help article's detailed view that includes parameter descriptions and examples.

        The Full parameter displays the help article's full view that includes parameter descriptions, examples, input and
        output object types, and additional notes.

        The Detailed and Full parameters are effective only for the commands that have help files installed on the
        computer. The parameters aren't effective for the conceptual ( about_ ) help articles.
        Example 4: Display selected parts of a cmdlet by using parameters

        Get-Help Format-Table -Examples
        Get-Help Format-Table -Parameter *
        Get-Help Format-Table -Parameter GroupBy

        The Examples parameter displays the help file's NAME and SYNOPSIS sections, and all the Examples. You can't
        specify an Example number because the Examples parameter is a switch parameter.

        The Parameter parameter displays only the descriptions of the specified parameters. If you specify only the
        asterisk (`*`) wildcard character, it displays the descriptions of all parameters. When Parameter specifies a
        parameter name such as GroupBy , information about that parameter is shown.

        These parameters aren't effective for the conceptual ( about_ ) help articles.
        ---------- Example 5: Display online version of help ----------

        Get-Help Format-Table -Online


        -------- Example 6: Display help about the help system --------

        Get-Help


        ---------- Example 7: Display available help articles ----------

        Get-Help *


        ------- Example 8: Display a list of conceptual articles -------

        Get-Help about_*


        --------- Example 9: Search for a word in cmdlet help ---------

        Get-Help Add-Member -Full | Out-String -Stream | Select-String -Pattern Clixml

        the Export-Clixml cmdlet to save the instance of the object, including the additional members...
        can use the Import-Clixml cmdlet to re-create the instance of the object from the information...
        Export-Clixml
        Import-Clixml

        `Get-Help` uses the Full parameter to get help information for `Add-Member`. The MamlCommandHelpInfo object is
        sent down the pipeline. `Out-String` uses the Stream parameter to convert the object into a string.
        `Select-String` uses the Pattern parameter to search the string for Clixml .
        -- Example 10: Display a list of articles that include a word --

        Get-Help -Name remoting

        Name                              Category  Module                    Synopsis
        ----                              --------  ------                    --------
        Install-PowerShellRemoting.ps1    External                            Install-PowerShellRemoting.ps1
        Disable-PSRemoting                Cmdlet    Microsoft.PowerShell.Core Prevents remote users...
        Enable-PSRemoting                 Cmdlet    Microsoft.PowerShell.Core Configures the computer...


        ---------- Example 11: Display provider-specific help ----------

        Get-Help Get-Item -Path SQLSERVER:\DataCollection

        NAME

            Get-Item

        SYNOPSIS

            Gets a collection of Server objects for the local computer and any computers

            to which you have made a SQL Server PowerShell connection.
            ...

        Set-Location SQLSERVER:\DataCollection
        SQLSERVER:\DataCollection> Get-Help Get-Item

        NAME

            Get-Item

        SYNOPSIS

            Gets a collection of Server objects for the local computer and any computers

            to which you have made a SQL Server PowerShell connection.
            ...


        ------------ Example 12: Display help for a script ------------

        Get-Help -Name C:\PS-Test\MyScript.ps1
    ```

    </details>
    <!-- #endregion -->

4. [Get-Help's example 4 parameter information](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/get-help?view=powershell-5.1&WT.mc_id=ps-gethelp#example-4--display-selected-parts-of-a-cmdlet-by-using-parameters)

    ```powershell
    Get-Help Format-Table -Parameter GroupBy
    ```

    <!-- #region(collapsed) output-->
    <details>
    <summary>output</summary>

    ```text
    -GroupBy <System.Object>
        Specifies sorted output in separate tables based on a property value. For example, you can use GroupBy to list
        services in separate tables based on their status.

        Enter an expression or a property. The GroupBy parameter expects that the objects are sorted. Use the
        `Sort-Object` cmdlet before using `Format-Table` to group the objects.

        The value of the GroupBy parameter can be a new calculated property. To create a calculated, property, use a hash
        table. The valid keys are as follows:

        - Name (or Label) = `<string>`

        - Expression = `<string>` or `<script block>`

        - FormatString = `<string>`

        Required?                    false
        Position?                    named
        Default value                None
        Accept pipeline input?       False
        Accept wildcard characters?  false
    ```

    </details>
    <!-- #endregion -->

5. [Get-Help's Example 8 (`about_` / conceptual  articles)](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/get-help?view=powershell-5.1&WT.mc_id=ps-gethelp#example-8--display-a-list-of-conceptual-articles)

    ```powershell
    Get-Help about_for
    ```

    <!-- #region(collapsed) output-->
    <details>
    <summary>output</summary>

    ```text
    ABOUT FOR


    Short description

    Describes a language command you can use to run statements based on a
    conditional test.


    Long description

    The For statement (also known as a For loop) is a language construct you
    can use to create a loop that runs commands in a command block while a
    specified condition evaluates to $true.

    A typical use of the For loop is to iterate an array of values and to
    operate on a subset of these values. In most cases, if you want to iterate
    all the values in an array, consider using a Foreach statement.

    Syntax

    The following shows the For statement syntax.

        for (<Init>; <Condition>; <Repeat>)
        {
            <Statement list>
        }

    The INIT placeholder represents one or more commands that are run before
    the loop begins. You typically use the INIT portion of the statement to
    create and initialize a variable with a starting value.

    This variable will then be the basis for the condition to be tested in the
    next portion of the For statement.

    The CONDITION placeholder represents the portion of the For statement that
    resolves to a $true or $false BOOLEAN value. PowerShell evaluates the
    condition each time the For loop runs. If the statement is $true, the
    commands in the command block run, and the statement is evaluated again. If
    the condition is still $true, the commands in the STATEMENT LIST run again.
    The loop is repeated until the condition becomes $false.

    The REPEAT placeholder represents one or more commands, separated by
    commas, that are executed each time the loop repeats. Typically, this is
    used to modify a variable that is tested inside the CONDITION part of the
    statement.

    The STATEMENT LIST placeholder represents a set of one or more commands
    that are run each time the loop is entered or repeated. The contents of the
    STATEMENT LIST are surrounded by braces.

    Support for multiple operations

    The following syntaxes are supported for multiple assignment operations in
    the INIT statement:

        # Comma separated assignment expressions enclosed in parenthesis.
        for (($i = 0), ($j = 0); $i -lt 10; $i++)
        {
            "`$i:$i"
            "`$j:$j"
        }

        # Sub-expression using the semicolon to separate statements.
        for ($($i = 0;$j = 0); $i -lt 10; $i++)
        {
            "`$i:$i"
            "`$j:$j"
        }

    The following syntaxes are supported for multiple assignment operations in
    the REPEAT statement:

        # Comma separated assignment expressions.
        for (($i = 0), ($j = 0); $i -lt 10; $i++)
        {
            "`$i:$i"
            "`$j:$j"
        }

        # Comma separated assignment expressions enclosed in parenthesis.
        for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
        {
            "`$i:$i"
            "`$j:$j"
        }

        # Sub-expression using the semicolon to separate statements.
        for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
        {
            "`$i:$i"
            "`$j:$j"
        }

    [!NOTE] Operations other than pre or post increment may not work with all
    syntaxes.

    For multiple CONDITIONS use logical operators as demonstrated by the
    following example.

        for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
        {
            "`$i:$i"
            "`$j:$j"
        }

    For more information, see about_Logical_Operators.

    Examples

    At a minimum, a For statement requires the parenthesis surrounding the
    INIT, CONDITION, and REPEAT part of the statement and a command surrounded
    by braces in the STATEMENT LIST part of the statement.

    Note that the upcoming examples intentionally show code outside the For
    statement. In later examples, code is integrated into the For statement.

    For example, the following For statement continually displays the value of
    the $i variable until you manually break out of the command by pressing
    CTRL+C.

        $i = 1
        for (;;)
        {
            Write-Host $i
        }

    You can add additional commands to the statement list so that the value of
    $i is incremented by 1 each time the loop is run, as the following example
    shows.

        for (;;)
        {
            $i++; Write-Host $i
        }

    Until you break out of the command by pressing CTRL+C, this statement will
    continually display the value of the $i variable as it is incremented by 1
    each time the loop is run.

    Rather than change the value of the variable in the statement list part of
    the For statement, you can use the REPEAT portion of the For statement
    instead, as follows.

        $i=1
        for (;;$i++)
        {
            Write-Host $i
        }

    This statement will still repeat indefinitely until you break out of the
    command by pressing CTRL+C.

    You can terminate the For loop using a _condition_. You can place a
    condition using the CONDITION portion of the For statement. The For loop
    terminates when the condition evaluates to $false.

    In the following example, the For loop runs while the value of $i is less
    than or equal to 10.

        $i=1
        for(;$i -le 10;$i++)
        {
            Write-Host $i
        }

    Instead of creating and initializing the variable outside the For
    statement, you can perform this task inside the For loop by using the INIT
    portion of the For statement.

        for($i=1; $i -le 10; $i++){Write-Host $i}

    You can use carriage returns instead of semicolons to delimit the INIT,
    CONDITION, and REPEAT portions of the For statement. The following example
    shows a For that uses this alternative syntax.

        for ($i = 0
        $i -lt 10
        $i++){
        $i
        }

    This alternative form of the For statement works in PowerShell script files
    and at the PowerShell command prompt. However, it is easier to use the For
    statement syntax with semicolons when you enter interactive commands at the
    command prompt.

    The For loop is more flexible than the Foreach loop because it allows you
    to increment values in an array or collection by using patterns. In the
    following example, the $i variable is incremented by 2 in the REPEAT
    portion of the For statement.

        for ($i = 0; $i -le 20; $i += 2)
        {
            Write-Host $i
        }

    The For loop can also be written on one line as in the following example.

        for ($i = 0; $i -lt 10; $i++) { Write-Host $i }


    SEE ALSO

    about_Comparison_Operators

    about_Foreach
    ```

    </details>
    <!-- #endregion -->

### list commands

```powershell
Get-Command
```

```diff
-TODO
```

### writing comments

Writing comments can be done by prepending `#` to a line. comments aren't executed
Example:

```ps
Write-Output Hello
# Write-Output World
```
<!-- #region(collapsed) output-->
<details open>
<summary>output</summary>

```text
Hello
```

</details>
<!-- #endregion -->

----------

## [WSL (Windows Subsystem for Linux)](https://docs.microsoft.com/en-us/windows/wsl/)

----------

```diff
-TODO summary,help,list of commands
- this is basically bash so this is a summary of bash
-todo `-` flags vs `--` flags
case sensetive
```

### asking for help

often [(POSIX based)](https://www.gnu.org/prep/standards/html_node/Command_002dLine-Interfaces.html) the `-?` or the `--help` flag can be used to view help about a specific utility.
man is a manual or a "help" utility to view in-depth documentation about installed software on your linux machine.
to exit press q.

```bash
man [command]
command -?
command --help
command -h
```

```bash
man -?
```
<!-- #region(collapsed) output-->
<details>
<summary>output</summary>

```
Usage: man [OPTION...] [SECTION] PAGE...

  -C, --config-file=FILE     use this user configuration file
  -d, --debug                emit debugging messages
  -D, --default              reset all options to their default values
      --warnings[=WARNINGS]  enable warnings from groff

 Main modes of operation:
  -f, --whatis               equivalent to whatis
  -k, --apropos              equivalent to apropos
  -K, --global-apropos       search for text in all pages
  -l, --local-file           interpret PAGE argument(s) as local filename(s)
  -w, --where, --path, --location
                             print physical location of man page(s)
  -W, --where-cat, --location-cat
                             print physical location of cat file(s)

  -c, --catman               used by catman to reformat out of date cat pages
  -R, --recode=ENCODING      output source page encoded in ENCODING

 Finding manual pages:
  -L, --locale=LOCALE        define the locale for this particular man search
  -m, --systems=SYSTEM       use manual pages from other systems
  -M, --manpath=PATH         set search path for manual pages to PATH

  -S, -s, --sections=LIST    use colon separated section list

  -e, --extension=EXTENSION  limit search to extension type EXTENSION

  -i, --ignore-case          look for pages case-insensitively (default)
  -I, --match-case           look for pages case-sensitively

      --regex                show all pages matching regex
      --wildcard             show all pages matching wildcard

      --names-only           make --regex and --wildcard match page names only,
                             not descriptions

  -a, --all                  find all matching manual pages
  -u, --update               force a cache consistency check

      --no-subpages          don't try subpages, e.g. 'man foo bar' => 'man
                             foo-bar'

 Controlling formatted output:
  -P, --pager=PAGER          use program PAGER to display output
  -r, --prompt=STRING        provide the `less' pager with a prompt

  -7, --ascii                display ASCII translation of certain latin1 chars
  -E, --encoding=ENCODING    use selected output encoding
      --no-hyphenation, --nh turn off hyphenation
      --no-justification,                              --nj   turn off justification
  -p, --preprocessor=STRING  STRING indicates which preprocessors to run:
                             e - [n]eqn, p - pic, t - tbl,
g - grap, r - refer, v - vgrind

  -t, --troff                use groff to format pages
  -T, --troff-device[=DEVICE]   use groff with selected device

  -H, --html[=BROWSER]       use www-browser or BROWSER to display HTML output
  -X, --gxditview[=RESOLUTION]   use groff and display through gxditview
                             (X11):
                             -X = -TX75, -X100 = -TX100, -X100-12 = -TX100-12
  -Z, --ditroff              use groff and force it to produce ditroff

  -?, --help                 give this help list
      --usage                give a short usage message
  -V, --version              print program version

Mandatory or optional arguments to long options are also mandatory or optional
for any corresponding short options.

Report bugs to cjwatson@debian.org.

```

</details>
<!-- #endregion -->

```bash
man man
```
<!-- #region(collapsed) output-->
<details>
<summary>output</summary>

```
MAN(1)                                            Manual pager utils                                           MAN(1)

NAME
       man - an interface to the system reference manuals

SYNOPSIS
       man [man options] [[section] page ...] ...
       man -k [apropos options] regexp ...
       man -K [man options] [section] term ...
       man -f [whatis options] page ...
       man -l [man options] file ...
       man -w|-W [man options] page ...

DESCRIPTION
       man  is the system's manual pager.  Each page argument given to man is normally the name of a program, utility
       or function.  The manual page associated with each of these arguments is then found and displayed.  A section,
       if  provided,  will direct man to look only in that section of the manual.  The default action is to search in
       all of the available sections following a pre-defined order (see DEFAULTS), and to show only  the  first  page
       found, even if page exists in several sections.

       The table below shows the section numbers of the manual followed by the types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions, e.g. /etc/passwd
       6   Games
       7   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

       A manual page consists of several sections.

       Conventional  section  names  include  NAME,  SYNOPSIS,  CONFIGURATION, DESCRIPTION, OPTIONS, EXIT STATUS, RE‐
       TURN VALUE, ERRORS, ENVIRONMENT, FILES, VERSIONS, CONFORMING TO, NOTES, BUGS, EXAMPLE, AUTHORS, and SEE ALSO.

       The following conventions apply to the SYNOPSIS section and can be used as a guide in other sections.

       bold text          type exactly as shown.
       italic text        replace with appropriate argument.
       [-abc]             any or all arguments within [ ] are optional.
       -a|-b              options delimited by | cannot be used together.
       argument ...       argument is repeatable.
       [expression] ...   entire expression within [ ] is repeatable.

       Exact rendering may vary depending on the output device.  For instance, man will usually not be able to render
       italics when running in a terminal, and will typically use underlined or coloured text instead.

       The  command  or function illustration is a pattern that should match all possible invocations.  In some cases
       it is advisable to illustrate several exclusive invocations as is shown in the SYNOPSIS section of this manual
       page.

EXAMPLES
       man ls
           Display the manual page for the item (program) ls.

       man man.7
           Display  the manual page for macro package man from section 7.  (This is an alternative spelling of "man 7
           man".)

       man 'man(7)'
           Display the manual page for macro package man from section 7.  (This is another  alternative  spelling  of
           "man  7  man".  It may be more convenient when copying and pasting cross-references to manual pages.  Note
           that the parentheses must normally be quoted to protect them from the shell.)

       man -a intro
           Display, in succession, all of the available intro manual pages contained within the manual.  It is possi‐
           ble to quit between successive displays or skip any of them.

       man -t bash | lpr -Pps
           Format  the  manual  page for bash into the default troff or groff format and pipe it to the printer named
           ps.  The default output for groff is usually PostScript.  man --help should advise as to  which  processor
           is bound to the -t option.

       man -l -Tdvi ./foo.1x.gz > ./foo.1x.dvi
           This command will decompress and format the nroff source manual page ./foo.1x.gz into a device independent
           (dvi) file.  The redirection is necessary as the -T flag causes output to be directed to  stdout  with  no
           pager.   The output could be viewed with a program such as xdvi or further processed into PostScript using
           a program such as dvips.

       man -k printf
           Search the short descriptions and manual page names for the keyword printf as regular  expression.   Print
           out any matches.  Equivalent to apropos printf.

       man -f smail
           Lookup the manual pages referenced by smail and print out the short descriptions of any found.  Equivalent
           to whatis smail.

OVERVIEW
       Many options are available to man in order to give as much flexibility as possible to the user.   Changes  can
       be  made to the search path, section order, output processor, and other behaviours and operations detailed be‐
       low.

       If set, various environment variables are interrogated to determine the operation of man.  It is  possible  to
       set  the "catch-all" variable $MANOPT to any string in command line format, with the exception that any spaces
       used as part of an option's argument must be escaped (preceded by a backslash).  man will parse $MANOPT  prior
       to  parsing  its own command line.  Those options requiring an argument will be overridden by the same options
       found on the command line.  To reset all of the options set in $MANOPT, -D can be  specified  as  the  initial
       command  line  option.   This will allow man to "forget" about the options specified in $MANOPT, although they
       must still have been valid.

       Manual pages are normally stored in nroff(1) format under a directory such as /usr/share/man.  In some instal‐
       lations, there may also be preformatted cat pages to improve performance.  See manpath(5) for details of where
       these files are stored.

       This package supports manual pages in multiple languages, controlled by your locale.  If your system  did  not
       set  this  up for you automatically, then you may need to set $LC_MESSAGES, $LANG, or another system-dependent
       environment variable to indicate your preferred locale, usually specified in the POSIX format:

       <language>[_<territory>[.<character-set>[,<version>]]]

       If the desired page is available in your locale, it will be displayed in lieu of the standard (usually  Ameri‐
       can English) page.

       If you find that the translations supplied with this package are not available in your native language and you
       would like to supply them, please contact the maintainer who will be coordinating such activity.

       Individual manual pages are normally written and maintained by the maintainers of the  program,  function,  or
       other  topic  that  they  document, and are not included with this package.  If you find that a manual page is
       missing or inadequate, please report that to the maintainers of the package in question.

       For information regarding other features and extensions available with this manual pager, please read the doc‐
       uments supplied with the package.

DEFAULTS
       The  order  of sections to search may be overridden by the environment variable $MANSECT or by the SECTION di‐
       rective in /etc/manpath.config.  By default it is as follows:

              1 n l 8 3 2 3posix 3pm 3perl 3am 5 4 9 6 7

       The formatted manual page is displayed using a pager.  This can be specified in a number of ways, or else will
       fall back to a default (see option -P for details).

       The filters are deciphered by a number of means.  Firstly, the command line option -p or the environment vari‐
       able $MANROFFSEQ is interrogated.  If -p was not used and the environment variable was not  set,  the  initial
       line of the nroff file is parsed for a preprocessor string.  To contain a valid preprocessor string, the first
       line must resemble

       '\" <string>

       where string can be any combination of letters described by option -p below.

       If none of the above methods provide any filter information, a default set is used.

       A formatting pipeline is formed from the filters and the primary formatter (nroff or [tg]roff with -t) and ex‐
       ecuted.   Alternatively,  if  an  executable program mandb_nfmt (or mandb_tfmt with -t) exists in the man tree
       root, it is executed instead.  It gets passed the manual source file, the preprocessor string, and  optionally
       the device specified with -T or -E as arguments.

OPTIONS
       Non-argument  options  that  are  duplicated either on the command line, in $MANOPT, or both, are not harmful.
       For options that require an argument, each duplication will override the previous argument value.

   General options
       -C file, --config-file=file
              Use this user configuration file rather than the default of ~/.manpath.

       -d, --debug
              Print debugging information.

       -D, --default
              This option is normally issued as the very first option and resets man's behaviour to its default.  Its
              use  is to reset those options that may have been set in $MANOPT.  Any options that follow -D will have
              their usual effect.

       --warnings[=warnings]
              Enable warnings from groff.  This may be used to perform sanity checks on the  source  text  of  manual
              pages.   warnings  is  a  comma-separated  list of warning names; if it is not supplied, the default is
              "mac".  See the “Warnings” node in info groff for a list of available warning names.

   Main modes of operation
       -f, --whatis
              Equivalent to whatis.  Display a short description from the manual page, if available.   See  whatis(1)
              for details.

       -k, --apropos
              Equivalent to apropos.  Search the short manual page descriptions for keywords and display any matches.
              See apropos(1) for details.

       -K, --global-apropos
              Search for text in all manual pages.  This is a brute-force search, and is likely to take some time; if
              you  can,  you should specify a section to reduce the number of pages that need to be searched.  Search
              terms may be simple strings (the default), or regular expressions if the --regex option is used.

              Note that this searches the sources of the manual pages, not the rendered  text,  and  so  may  include
              false positives due to things like comments in source files.  Searching the rendered text would be much
              slower.

       -l, --local-file
              Activate "local" mode.  Format and display local manual files instead of searching through the system's
              manual  collection.   Each manual page argument will be interpreted as an nroff source file in the cor‐
              rect format.  No cat file is produced.  If '-' is listed as one of the arguments, input will  be  taken
              from  stdin.   When this option is not used, and man fails to find the page required, before displaying
              the error message, it attempts to act as if this option was supplied, using the name as a filename  and
              looking for an exact match.

       -w, --where, --path, --location
              Don't  actually  display the manual page, but do print the location of the source nroff file that would
              be formatted.  If the -a option is also used, then print the locations of all source files  that  match
              the search criteria.

       -W, --where-cat, --location-cat
              Don't  actually  display  the  manual page, but do print the location of the preformatted cat file that
              would be displayed.  If the -a option is also used, then print the locations of  all  preformatted  cat
              files that match the search criteria.

              If  -w  and -W are both used, then print both source file and cat file separated by a space.  If all of
              -w, -W, and -a are used, then do this for each possible match.

       -c, --catman
              This option is not for general use and should only be used by the catman program.

       -R encoding, --recode=encoding
              Instead of formatting the manual page in the usual way, output its source converted  to  the  specified
              encoding.   If  you already know the encoding of the source file, you can also use manconv(1) directly.
              However, this option allows you to convert several manual pages to a single encoding without having  to
              explicitly state the encoding of each, provided that they were already installed in a structure similar
              to a manual page hierarchy.

              Consider using man-recode(1) instead for converting multiple manual pages, since it  has  an  interface
              designed for bulk conversion and so can be much faster.

   Finding manual pages
       -L locale, --locale=locale
              man will normally determine your current locale by a call to the C function setlocale(3) which interro‐
              gates various environment variables, possibly including $LC_MESSAGES and $LANG.  To  temporarily  over‐
              ride  the  determined  value,  use this option to supply a locale string directly to man.  Note that it
              will not take effect until the search for pages actually begins.  Output such as the help message  will
              always be displayed in the initially determined locale.

       -m system[,...], --systems=system[,...]
              If this system has access to other operating system's manual pages, they can be accessed using this op‐
              tion.  To search for a manual page from NewOS's manual page collection, use the option -m NewOS.

              The system specified can be a combination of comma delimited operating  system  names.   To  include  a
              search  of  the  native  operating  system's  manual pages, include the system name man in the argument
              string.  This option will override the $SYSTEM environment variable.

       -M path, --manpath=path
              Specify an alternate manpath to use.  By default, man uses manpath derived code to determine  the  path
              to search.  This option overrides the $MANPATH environment variable and causes option -m to be ignored.

              A  path  specified as a manpath must be the root of a manual page hierarchy structured into sections as
              described in the man-db manual (under "The manual page system").  To view manual pages outside such hi‐
              erarchies, see the -l option.

       -S list, -s list, --sections=list
              The given list is a colon- or comma-separated list of sections, used to determine which manual sections
              to search and in what order.  This option overrides the $MANSECT environment variable.  (The -s  spell‐
              ing is for compatibility with System V.)

       -e sub-extension, --extension=sub-extension
              Some  systems incorporate large packages of manual pages, such as those that accompany the Tcl package,
              into the main manual page hierarchy.  To get around the problem of having two  manual  pages  with  the
              same  name  such as exit(3), the Tcl pages were usually all assigned to section l.  As this is unfortu‐
              nate, it is now possible to put the pages in the correct section, and to assign a specific  "extension"
              to  them,  in this case, exit(3tcl).  Under normal operation, man will display exit(3) in preference to
              exit(3tcl).  To negotiate this situation and to avoid having to know which section the page you require
              resides  in,  it  is  now possible to give man a sub-extension string indicating which package the page
              must belong to.  Using the above example, supplying the option -e tcl to man will restrict  the  search
              to pages having an extension of *tcl.

       -i, --ignore-case
              Ignore case when searching for manual pages.  This is the default.

       -I, --match-case
              Search for manual pages case-sensitively.

       --regex
              Show all pages with any part of either their names or their descriptions matching each page argument as
              a regular expression, as with apropos(1).  Since there is usually no reasonable way to  pick  a  "best"
              page when searching for a regular expression, this option implies -a.

       --wildcard
              Show  all  pages  with any part of either their names or their descriptions matching each page argument
              using shell-style wildcards, as with apropos(1) --wildcard.  The page argument must  match  the  entire
              name or description, or match on word boundaries in the description.  Since there is usually no reason‐
              able way to pick a "best" page when searching for a wildcard, this option implies -a.

       --names-only
              If the --regex or --wildcard option is used, match only page names,  not  page  descriptions,  as  with
              whatis(1).  Otherwise, no effect.

       -a, --all
              By  default,  man will exit after displaying the most suitable manual page it finds.  Using this option
              forces man to display all the manual pages with names that match the search criteria.

       -u, --update
              This option causes man to update its database caches of installed manual pages.  This is only needed in
              rare situations, and it is normally better to run mandb(8) instead.

       --no-subpages
              By  default,  man will try to interpret pairs of manual page names given on the command line as equiva‐
              lent to a single manual page name containing a hyphen or an underscore.  This supports the common  pat‐
              tern of programs that implement a number of subcommands, allowing them to provide manual pages for each
              that can be accessed using similar syntax as would be used to invoke the subcommands  themselves.   For
              example:

                $ man -aw git diff
                /usr/share/man/man1/git-diff.1.gz

              To disable this behaviour, use the --no-subpages option.

                $ man -aw --no-subpages git diff
                /usr/share/man/man1/git.1.gz
                /usr/share/man/man3/Git.3pm.gz
                /usr/share/man/man1/diff.1.gz

   Controlling formatted output
       -P pager, --pager=pager
              Specify  which  output  pager  to use.  By default, man uses pager, falling back to cat if pager is not
              found or is not executable.  This option overrides the $MANPAGER environment variable,  which  in  turn
              overrides the $PAGER environment variable.  It is not used in conjunction with -f or -k.

              The  value  may  be a simple command name or a command with arguments, and may use shell quoting (back‐
              slashes, single quotes, or double quotes).  It may not use pipes to connect multiple commands;  if  you
              need  that,  use a wrapper script, which may take the file to display either as an argument or on stan‐
              dard input.

       -r prompt, --prompt=prompt
              If a recent version of less is used as the pager, man will attempt to set its prompt and some  sensible
              options.  The default prompt looks like

               Manual page name(sec) line x

              where  name  denotes the manual page name, sec denotes the section it was found under and x the current
              line number.  This is achieved by using the $LESS environment variable.

              Supplying -r with a string will override this default.  The string may contain the text  $MAN_PN  which
              will be expanded to the name of the current manual page and its section name surrounded by "(" and ")".
              The string used to produce the default could be expressed as

              \ Manual\ page\ \$MAN_PN\ ?ltline\ %lt?L/%L.:
              byte\ %bB?s/%s..?\ (END):?pB\ %pB\\%..
              (press h for help or q to quit)

              It is broken into three lines here for the sake of readability only.  For its meaning see  the  less(1)
              manual  page.   The  prompt string is first evaluated by the shell.  All double quotes, back-quotes and
              backslashes in the prompt must be escaped by a preceding backslash.  The prompt string may  end  in  an
              escaped $ which may be followed by further options for less.  By default man sets the -ix8 options.

              The $MANLESS environment variable described below may be used to set a default prompt string if none is
              supplied on the command line.

       -7, --ascii
              When viewing a pure ascii(7) manual page on a 7 bit terminal or terminal emulator, some characters  may
              not  display  correctly when using the latin1(7) device description with GNU nroff.  This option allows
              pure ascii manual pages to be displayed in ascii with the latin1 device.  It  will  not  translate  any
              latin1  text.   The following table shows the translations performed: some parts of it may only be dis‐
              played properly when using GNU nroff's latin1(7) device.

              Description           Octal   latin1   ascii
              ─────────────────────────────────────────────
              continuation hyphen    255      ‐        -
              bullet (middle dot)    267      •        o
              acute accent           264      ´        '
              multiplication sign    327      ×        x

              If the latin1 column displays correctly, your terminal may be set up for latin1 characters and this op‐
              tion  is not necessary.  If the latin1 and ascii columns are identical, you are reading this page using
              this option or man did not format this page using the latin1 device description.  If the latin1  column
              is missing or corrupt, you may need to view manual pages with this option.

              This  option  is  ignored  when using options -t, -H, -T, or -Z and may be useless for nroff other than
              GNU's.

       -E encoding, --encoding=encoding
              Generate output for a character encoding other than the default.  For backward compatibility,  encoding
              may  be  an  nroff  device  such as ascii, latin1, or utf8 as well as a true character encoding such as
              UTF-8.

       --no-hyphenation, --nh
              Normally, nroff will automatically hyphenate text at line breaks even in words that do not contain  hy‐
              phens,  if  it is necessary to do so to lay out words on a line without excessive spacing.  This option
              disables automatic hyphenation, so words will only be hyphenated if they already contain hyphens.

              If you are writing a manual page and simply want to prevent nroff from hyphenating a word at  an  inap‐
              propriate point, do not use this option, but consult the nroff documentation instead; for instance, you
              can put "\%" inside a word to indicate that it may be hyphenated at that point,  or  put  "\%"  at  the
              start of a word to prevent it from being hyphenated.

       --no-justification, --nj
              Normally,  nroff will automatically justify text to both margins.  This option disables full justifica‐
              tion, leaving justified only to the left margin, sometimes called "ragged-right" text.

              If you are writing a manual page and simply want to prevent nroff from justifying  certain  paragraphs,
              do  not  use  this  option,  but consult the nroff documentation instead; for instance, you can use the
              ".na", ".nf", ".fi", and ".ad" requests to temporarily disable adjusting and filling.

       -p string, --preprocessor=string
              Specify the sequence of preprocessors to run before nroff or troff/groff.  Not all  installations  will
              have  a  full  set  of preprocessors.  Some of the preprocessors and the letters used to designate them
              are: eqn (e), grap (g), pic (p), tbl (t), vgrind (v), refer (r).  This option overrides the $MANROFFSEQ
              environment variable.  zsoelim is always run as the very first preprocessor.

       -t, --troff
              Use groff -mandoc to format the manual page to stdout.  This option is not required in conjunction with
              -H, -T, or -Z.

       -T[device], --troff-device[=device]
              This option is used to change groff (or possibly troff's) output to be suitable for a device other than
              the  default.   It  implies -t.  Examples (provided with Groff-1.17) include dvi, latin1, ps, utf8, X75
              and X100.

       -H[browser], --html[=browser]
              This option will cause groff to produce HTML output, and will display that output  in  a  web  browser.
              The  choice  of  browser  is  determined  by  the  optional browser argument if one is provided, by the
              $BROWSER environment variable, or by a compile-time default if that is unset (usually lynx).  This  op‐
              tion implies -t, and will only work with GNU troff.

       -X[dpi], --gxditview[=dpi]
              This  option  displays  the output of groff in a graphical window using the gxditview program.  The dpi
              (dots per inch) may be 75, 75-12, 100, or 100-12, defaulting to 75; the -12  variants  use  a  12-point
              base font.  This option implies -T with the X75, X75-12, X100, or X100-12 device respectively.

       -Z, --ditroff
              groff will run troff and then use an appropriate post-processor to produce output suitable for the cho‐
              sen device.  If groff -mandoc is groff, this option is passed to groff and will suppress the use  of  a
              post-processor.  It implies -t.

   Getting help
       -?, --help
              Print a help message and exit.

       --usage
              Print a short usage message and exit.

       -V, --version
              Display version information.

EXIT STATUS
       0      Successful program execution.

       1      Usage, syntax or configuration file error.

       2      Operational error.

       3      A child process returned a non-zero exit status.

       16     At least one of the pages/files/keywords didn't exist or wasn't matched.

ENVIRONMENT
       MANPATH
              If $MANPATH is set, its value is used as the path to search for manual pages.

       MANROFFOPT
              Every  time  man invokes the formatter (nroff, troff, or groff), it adds the contents of $MANROFFOPT to
              the formatter's command line.

       MANROFFSEQ
              If $MANROFFSEQ is set, its value is used to determine the set of preprocessors to pass each manual page
              through.  The default preprocessor list is system dependent.

       MANSECT
              If  $MANSECT  is set, its value is a colon-delimited list of sections and it is used to determine which
              manual sections to search and in what order.  The default is "1 n l 8 3 2 3posix 3pm 3perl 3am 5 4 9  6
              7", unless overridden by the SECTION directive in /etc/manpath.config.

       MANPAGER, PAGER
              If  $MANPAGER  or $PAGER is set ($MANPAGER is used in preference), its value is used as the name of the
              program used to display the manual page.  By default, pager is used, falling back to cat  if  pager  is
              not found or is not executable.

              The  value  may  be a simple command name or a command with arguments, and may use shell quoting (back‐
              slashes, single quotes, or double quotes).  It may not use pipes to connect multiple commands;  if  you
              need  that,  use a wrapper script, which may take the file to display either as an argument or on stan‐
              dard input.

       MANLESS
              If $MANLESS is set, its value will be used as the default prompt string for the less pager,  as  if  it
              had  been  passed  using  the -r option (so any occurrences of the text $MAN_PN will be expanded in the
              same way).  For example, if you want to set the prompt string unconditionally to  “my  prompt  string”,
              set $MANLESS to ‘-Psmy prompt string’.  Using the -r option overrides this environment variable.

       BROWSER
              If  $BROWSER  is set, its value is a colon-delimited list of commands, each of which in turn is used to
              try to start a web browser for man --html.  In each command, %s is replaced by  a  filename  containing
              the  HTML output from groff, %% is replaced by a single percent sign (%), and %c is replaced by a colon
              (:).

       SYSTEM If $SYSTEM is set, it will have the same effect as if it had been specified as the argument to  the  -m
              option.

       MANOPT If  $MANOPT  is  set,  it will be parsed prior to man's command line and is expected to be in a similar
              format.  As all of the other man specific environment variables can be expressed as  command  line  op‐
              tions, and are thus candidates for being included in $MANOPT it is expected that they will become obso‐
              lete.  N.B.  All spaces that should be interpreted as part of an option's argument must be escaped.

       MANWIDTH
              If $MANWIDTH is set, its value is used as the line length for which manual pages should  be  formatted.
              If it is not set, manual pages will be formatted with a line length appropriate to the current terminal
              (using the value of $COLUMNS, and ioctl(2) if available, or falling back to 80 characters if neither is
              available).   Cat  pages  will  only be saved when the default formatting can be used, that is when the
              terminal line length is between 66 and 80 characters.

       MAN_KEEP_FORMATTING
              Normally, when output is not being directed to a terminal (such as to a file  or  a  pipe),  formatting
              characters  are  discarded  to  make  it  easier to read the result without special tools.  However, if
              $MAN_KEEP_FORMATTING is set to any non-empty value, these formatting characters are retained.  This may
              be useful for wrappers around man that can interpret formatting characters.

       MAN_KEEP_STDERR
              Normally,  when  output is being directed to a terminal (usually to a pager), any error output from the
              command used to produce formatted versions of manual pages is discarded to avoid interfering  with  the
              pager's display.  Programs such as groff often produce relatively minor error messages about typograph‐
              ical problems such as poor alignment, which are unsightly and generally confusing when displayed  along
              with  the  manual page.  However, some users want to see them anyway, so, if $MAN_KEEP_STDERR is set to
              any non-empty value, error output will be displayed as usual.

       LANG, LC_MESSAGES
              Depending on system and implementation, either or both of $LANG and $LC_MESSAGES will  be  interrogated
              for the current message locale.  man will display its messages in that locale (if available).  See set‐
              locale(3) for precise details.

FILES
       /etc/manpath.config
              man-db configuration file.

       /usr/share/man
              A global manual page hierarchy.

SEE ALSO
       apropos(1), groff(1), less(1), manpath(1), nroff(1), troff(1), whatis(1), zsoelim(1), manpath(5), man(7), cat‐
       man(8), mandb(8)

       Documentation for some packages may be available in other formats, such as info(1) or HTML.

HISTORY
       1990, 1991 – Originally written by John W. Eaton (jwe@che.utexas.edu).

       Dec   23   1992:   Rik   Faith   (faith@cs.unc.edu)   applied   bug   fixes   supplied   by   Willem   Kasdorp
       (wkasdo@nikhefk.nikef.nl).

       30th April 1994 – 23rd February 2000: Wilf. (G.Wilford@ee.surrey.ac.uk) has been  developing  and  maintaining
       this package with the help of a few dedicated people.

       30th October 1996 – 30th March 2001: Fabrizio Polacco <fpolacco@debian.org> maintained and enhanced this pack‐
       age for the Debian project, with the help of all the community.

       31st March 2001 – present day: Colin Watson <cjwatson@debian.org> is now developing and maintaining man-db.

2.9.1                                                 2020-02-25                                               MAN(1)
```

</details>
<!-- #endregion -->

### Referencing variables

by using the `$` sign a variable named `VARIABLE` can be referenced by typing `$VARIABLE`.
Example:

```bash
echo $HOME
```
<!-- #region(collapsed) output-->
<details>
<summary>output</summary>

```bash
/home/user
```

</details>
<!-- #endregion -->

----------
Pipes and Output redirection
`>` - Write
`>>` - Append
`<` -

## Cygwin

----------

```diff
-todo: actually have no clue about cygwin.
```

----------

## MSYS

----------

```diff
-todo: how's msys related to cygwin?
```
