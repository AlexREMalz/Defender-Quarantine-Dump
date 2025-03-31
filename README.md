# Windows Defender Quarantine Dumper

This script extracts and decrypts quarantined files from Windows Defender. It can list the quarantined entries or dump them into a `.tar` archive for further analysis.

## Features

- Extracts and decrypts files from the Windows Defender quarantine.
- Supports specifying the quarantine directory manually.
- Dumps all recovered files into a `quarantine.tar` archive.

## Usage

Run the script with the appropriate options:

### Dumping Quarantined Files:

```cmd
> python3 defender_dump.py --quarantine-path "Device\C%3A\ProgramData\Windows Defender\Quarantine" --dump
```

This extracts all quarantined files and saves them into a compressed archive named quarantine.tar.

### Listing Quarantined Files Without Dumping:
```cmd
> python3 defender_dump.py --quarantine-path "C:\ProgramData\Microsoft\Windows Defender\Quarantine"
```

This prints out the detected threats with timestamps and filenames.

### Using Root Directory Instead of Quarantine Path

```cmd
> python3 defender_dump.py C:\
```

The script automatically finds the default quarantine folder under C:\ProgramData\Microsoft\Windows Defender\Quarantine.

## Arguments

| Argument                      | Description  |
|--------------------------------|-------------|
| `rootdir`                      | (Optional) Root directory where Defender is installed (e.g., `C:\`). |
| `-q, --quarantine-path <path>` | Provide the full path to the Defender quarantine folder. Useful for forensic cases. |
| `-d, --dump`                   | Dump all extracted files into a `quarantine.tar` archive. |

## Notes

- **Requires Python 3**.
- **May require administrative privileges** to access the Defender quarantine folder.
- **Inspired by [knez/defender-dump](https://github.com/knez/defender-dump/tree/master)**.
