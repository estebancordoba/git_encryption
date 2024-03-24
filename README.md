# Transcrypt: Managing Sensitive Files in Git

Transcrypt enables transparent encryption of sensitive files stored within a Git repository. Designated files will be automatically encrypted upon commit and decrypted upon checkout, facilitating the secure management of sensitive data without altering the normal workflow of your team.

## Installation

### Manual Option

Within the repository, you will find the `transcrypt` executable script. To use it directly, navigate to your repository directory and execute:

```bash
./transcrypt -c aes-256-cbc -p 'password'
```

Make sure to replace `'password'` with the secure password that will be provided by the team. This action will initialize Transcrypt in your repository with the specified encryption and password.

### Installation via Packages

For a more integrated installation, you can follow the detailed instructions in our installation guide:

[Transcrypt Installation Guide](https://github.com/elasticdog/transcrypt/blob/main/INSTALL.md)

After installation, you can use the script anywhere within your system as follows:

```bash
transcrypt -c aes-256-cbc -p 'password'
```

Remember, the password (`'password'`) will be provided to you by the team.

## Post-Installation

Once the installation is complete, the encryption and decryption of files will be handled automatically based on configurations specified in the `.gitattributes` file of the repository.

## Adding Files to Encrypt/Decrypt

To designate files for encryption/decryption, you must add a specific entry in the `.gitattributes` file at the root of your repository. For example, to encrypt a file named `file-to-encrypt.secret`, add the following line:

```bash
file-to-encrypt.secret filter=crypt diff=crypt merge=crypt
```

Then, simply perform `git add` and `git commit` for both the `.gitattributes` file and the file you wish to encrypt.

## Important

- Ensure all team members needing to work with encrypted files have Transcrypt configured with the same password.
- Do not share the password through insecure means. Consider using a secure password manager or encrypted communication to distribute the team's password.
