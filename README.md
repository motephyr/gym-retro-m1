# gym-retro-m1

This repository contains a version of gym-retro compatible with M1 Macs. Gym-retro is an emulator for reinforcement learning that provides environments for various classic games. You can learn more about OpenAI's gym-retro on the official page.

In CMakeLists.txt, I remove "add_core(gb gambatte)" because it needs i386 support.

System Requirements

- macOS (for M1 Macs)
- Python 3.6+

Compile Environment Setup (for M1 Mac users only)

0. Download or clone this repository:
```
git clone https://github.com/yourusername/gym-retro-m1.git
```
If you are an M1 Mac user, set up your environment following these steps.

1. Install llvm and add the following content to your ~/.zshrc (if using zsh) or ~/.bash_profile (if using bash):
```
brew install llvm
```

```
export PATH="/opt/homebrew/opt/llvm/bin:$PATH"
export LDFLAGS="-L/opt/homebrew/opt/llvm/lib"
export CPPFLAGS="-I/opt/homebrew/opt/llvm/include"
export SDKROOT=$(xcrun --sdk macosx --show-sdk-path)
export MACOSX_DEPLOYMENT_TARGET=$(xcrun --sdk macosx --show-sdk-version)
export LIBRARY_PATH="$LIBRARY_PATH:/usr/local/lib:/usr/lib"
export LIBRARY_PATH="/opt/homebrew/opt/llvm/lib:$LIBRARY_PATH"
export LIBRARY_PATH="/opt/homebrew/opt/llvm/lib/clang/16/lib/darwin:$LIBRARY_PATH"
```

2. Reload your configuration file:
```
source ~/.zshrc
or
source ~/.bash_profile
```

3. compile and execute.
```
brew install pkg-config capnp lua@5.1 qt5
cmake . -DCMAKE_PREFIX_PATH=/usr/local/opt/qt -DBUILD_UI=ON -UPYLIB_DIRECTORY
make -j$(sysctl hw.ncpu | cut -d: -f2)
open "Gym Retro Integration.app"
```

Usage

Use the environments provided by gym-retro in your reinforcement learning projects. For detailed usage and API, please refer to the official gym-retro documentation.

Troubleshooting

If you encounter any issues while using this version of gym-retro, please create an issue on the GitHub repository, and we'll do our best to assist you.