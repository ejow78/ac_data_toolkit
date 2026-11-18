# AC Data Toolkit

Python desktop and CLI tool for unpacking, modifying, and repacking **Assetto Corsa** `data.acd` archives, physics files, and FMOD sound banks.

## How It Works

* **`.acd` Binary Format & Cipher:** Parses and packs sequential `[name_len][ascii_name][file_len][uint32_le_data]` entries using modular byte shifting against a cyclic ASCII key (`generate_key`, `decrypt_bytes`, `encrypt_bytes`).
* **Key Auto-Recovery:** If a car folder was renamed, `auto_recover_key()` runs a known-plaintext check against standard AC `.ini` headers (`[HEADER]\r\nVERSION=...`) and validates printable ASCII ratio.
* **Physics, BoP & Sound:** Programmatic `.ini` and `.lut` parsers/writers rescale torque/power curves and ERS parameters (`ers.ini`, `et.lut`), while the sound/rename helpers update FMOD `.bank` files and `sfx/GUIDs.txt` paths before repacking with the new key.

## Run

```bash
python ac_data_toolkit.py
python ac_data_toolkit.py unpack <path>
python ac_data_toolkit.py pack <path>
```
