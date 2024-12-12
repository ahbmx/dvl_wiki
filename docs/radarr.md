## Radarr
# Create Directories

Iterate over each file in a directory, and move it to a folder with the same name.

=== "Linux"
    ``` bash
    find . -maxdepth 1 -type f -iname "*.mkv" -exec sh -c 'mkdir "${1%.*}" ; mv "${1%}" "${1%.*}" ' _ {} \;
    ```

=== "Powershell"
    ``` powershell
    Get-ChildItem -File | ForEach-Object {
        $dir = New-Item -ItemType Directory -Name $_.BaseName -Force
        $_ | Move-Item -Destination $dir
    }
    ```