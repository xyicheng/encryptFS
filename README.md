# encryptFS
A simple file system that encrypts each file individually. Designed for use with cloud storage.

## Details
Quick high-level overview:

1. You have some files `abc`, `123`, `asdf`.
2. You make an encryptFS in a directory and add all three files. You end up with an encrypted index file and three files with randomly generated names (e.g. `e4e90f66761a0ddf52ec47e3d9f1851e3e2304b2b9abd6ae0f818cafa26d56a0`).
3. Later, you can open the existing encryptFS and decrypt your files back.

Some quick points:

* Why are the files encrypted separately instead of being put together in blocks? Isn't this a flaw in the security? For now, I'm willing to trade off the security to simplify the code and to allow for easier/quicker decryption of specific individual files.
* Does this keep my original file metadata? For now, no.

## Usage
This project is **very** new and this API is **very** subject to change.

```python
from encryptfs.encryptfs import EncryptFS

encfs = EncryptFS('asdfasdf')

# This will encrypt all new files in the current directory
encfs.encrypt_all()

# This will decrypt all encrypted files in the index
encfs.decrypt_all()
```