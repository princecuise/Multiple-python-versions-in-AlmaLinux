# Multiple-python-versions-in-AlmaLinux
Install multiple versions of Python on AlmaLinux 10

To install and manage multiple Python versions on AlmaLinux 10, you’ve got two reliable paths: compiling from source for full control, or using pyenv for convenience.

🧱 Method 1: Compile Python from Source

This gives you precise control and avoids interfering with the system Python.

🔧 Steps:

1. Update your system:

$ sudo dnf update -y

2. Install build dependencies:

$ sudo dnf groupinstall "Development Tools" -y

$ sudo dnf install gcc openssl-devel bzip2-devel libffi-devel zlib-devel wget make cmake -y

3. Download and compile Python: Replace 3.13.0 with any version you want.

$ cd /usr/src

$ sudo wget https://www.python.org/ftp/python/3.13.0/Python-3.13.0.tgz

$ sudo tar xzf Python-3.13.0.tgz

$ cd Python-3.13.0

$ sudo ./configure --enable-optimizations

$ sudo make altinstall

Use make altinstall to avoid overwriting the default python3 binary.

4. Verify installation:

$ python3.13 --version
	
Repeat for other versions like 3.10, 3.11, etc.

🧰 Method 2: Use pyenv for Easy Version Switching

pyenv simplifies installing and switching between Python versions.

🛠 Install pyenv:

$ curl https://pyenv.run | bash

Add this to your shell config (~/.bashrc, ~/.zshrc, etc.):

$ export PATH="$HOME/.pyenv/bin:$PATH"

$ eval "$(pyenv init --path)"

$ eval "$(pyenv init -)"

$ eval "$(pyenv virtualenv-init -)"

Restart your shell and install Python version:

$ pyenv install 3.13.0

Use Virtual Environments ->

Once installed, isolate projects using venv:

$ python3.13 -m venv myvenv

$ source myvenv/bin/activate
