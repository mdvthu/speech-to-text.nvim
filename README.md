# speech-to-text.nvim
Neovim plugin offer speech to text capability using Python
[speech_recognition](https://github.com/Uberi/speech_recognition). 

You can select your favorite engine for speech-to-text:
[OpenAI whisper](https://github.com/openai/whisper), Google, [Vosk
API](https://github.com/alphacep/vosk-api/) etc.. (supported
*speech_recognition* engines)

This is basically a tin wrapper around speech_recognition. So, you really want
to check out its
[documentation](https://github.com/Uberi/speech_recognition#readme). Should
work OOB with whisper function. 

Uses [keyboard package](https://pypi.org/project/keyboard/), which equires
admin on Linux. Luckily, only used for detection of ESC so ESC might not work.

## Installation

Using [vim-plug](https://github.com/junegunn/vim-plug):
```
Plug 'eyalk11/speech-to-text.nvim'
```
or with [Vundle](https://github.com/VundleVim/Vundle.vim):
```
Plugin 'eyalk11/speech-to-text.nvim'
```


To install Python dependencies:
```
!pip install -r ~/.vim/plugged/speech-to-text.nvim/requirements.txt
:UpdateRemotePlugins
```
(Those are minimal requirements. It may need additional - see
[speech_recognition](https://github.com/Uberi/speech_recognition))

### Alternative 

Try  
```
Plug 'eyalk11/speech-to-text.nvim', {'do': ':!python -m pip install -r ./requirements.txt \| :UpdateRemotePlugins'}
```
Should work, but couldn't confirm this due to unclear output by vim-plug. Possibly OS  dependet. 
Let me know if works.

## Usage

It will add the 

`GetVoice()` function - which returns text by speech

`:Voice` which replaces the selected range with text (by speech). Gets the same parameters as the ConfigureVoice commmand. 

You can cancel both voice commands by pressing esc.

`:ConfigureVoice [enginename] [paramsdic]` - which configures engine parameters (can also be done by yaml config). 
The enginename and params would be used for the next Voice/GetVoice call. 

## Mappings

Mappings are not added by default.

Suggested mappings:
```
nmap <c-L> :Voice<CR>
imap <C-L> <C-R>=GetVoice()<CR>
```

## Credits

https://vi.stackexchange.com/users/23502/vivian-de-smedt for helping out with replacing text. 

