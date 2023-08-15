# How to Sign GIT Commits with GPG keys

If you are starting with git, you may be wondering how to get a verified tag for your commits. Initially, most of your commits will have an Unverified tag or nothing at all. This is just because you haven't signed your commits yet.

Well, there is nothing wrong with not signing your commits, but if you want to be able to verify your commits, you need to have a GPG key. Just follow the steps below.

## Stepwise procedure

Follow these steps to successfully generate a gpg key and add it to your GitHub account

### STEP 1 - Generate a GPG Key

Go to https://www.gnupg.org, and download the GPG CLI for your OS.

Open any terminal and run the following command:

```shell
gpg --full-generate-key
```

3. At the prompt, specify the kind of key you want, or press <kbd>ENTER</kbd> to accept the default.

4. Next, specify the key size you want or press <kbd>ENTER</kbd> to accept the default.

   > GitHub prefers the size to be at least `4096` bits.\
   > NOTE: Large size means more processing time

5. Enter the length of time the key should be valid. Press <kbd>ENTER</kbd> to specify the default selection, indicating that the key doesn't expire.
6. Verify that your selections are correct.
   > NOTE: the email should be the same as the email in your Github account and the name should be the GitHub account name
7. Enter your user ID information.
8. Type a secure passphrase that you could remember, and also note it down somewhere safe.

### STEP 2 - Get the Public key

1. Get the list of all your keys with key id using the following command...

   ```shell
   gpg --list-secret-keys --keyid-format=long
   ```

   This will give you a list of all your keys. for example:

   ```shell
   $ gpg --list-secret-keys --keyid-format=long
   /Users/hubot/.gnupg/secring.gpg
   ------------------------------------
   sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
   uid                          Hubot
   ssb   4096R/42B317FD4BA89E7A 2016-03-10
   ```

2. Paste the text below, substituting in the GPG key ID you'd like to use. In this example, the GPG key ID is `3AA5C34371567BD2`, or you can also use your _email address_:

   ```shell
   $ gpg --armor --export 3AA5C34371567BD2
   -----BEGIN PGP PUBLIC KEY BLOCK-----
     ******
   ---END PGP PUBLIC KEY BLOCK-----
   ```

3. Copy your GPG key, beginning with `-----BEGIN PGP PUBLIC KEY BLOCK-----` and ending with `-----END PGP PUBLIC KEY BLOCK-----`.
4. You can directly get the public key to the clipboard by using the following command:

   ```shell
   gpg --armor --export 3AA5C34371567BD2 | clip.exe
   ```

   > Note: this command only works for Windows.

### STEP 3 - Add GPG key to your Github account

1. Go to your Github account and click on the `Settings` tab.
2. In the user settings sidebar, click **SSH and GPG keys**.
3. Click **New GPG key**.
4. In the **Key** field, paste the GPG key you copied when you [generated the key](#2-get-the-public-key).
5. Click **Add GPG Key**, after that, you might have to confirm your GitHub password.

### STEP 4 - Sign your commits in GIT

This is the final but crucial step. Open the terminal of your choice and run the following command:

```
git config --global user.signingkey 3AA5C34371567BD2
git config --global commit.gpgsign true
```

> `3AA5C34371567BD2` is an example of the GPG key ID. You can also use your Email address preferred).

If you want to take a look at the configuration file, just run %userprofile%\.gitconfig in your terminal.

Remember, for the signing to work email in your GitHub account must match that of your GPG key as well as the Git config file.

If you are using **VS Code** you have to do another step. Go to `settings > git.alwaysSignOff` and set it to **true**. This will enable you to sign commits from VS Code.

And all done, after that, all your commits will be signed. You just have to put your GPG passphrase after each commit to verify the commit.
