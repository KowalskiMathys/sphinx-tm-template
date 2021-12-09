# Titre du chapitre 2

## Never

```python

def ui(x):
    x += 1
    return x

```

ducoup on fait comment pour les images

```{code-block} python
---
emphasize-lines: 31-47
linenos: true

---
import block_class
import TM_hash
import chain_document
import time


chain = chain_document.blockchain
sec_chain = []
for b in chain:
    sec_chain.append(b)

class blockchain:
    difficulty: int = 4
    def __init__(self, chain):
        self.chain = chain

    def set_difficulty(self, difficulty):
        self.difficulty = difficulty

    def add_block(self,block):
        self.chain.append(block)
        f = open('chain_document.py', 'a')
        f.write('\nb = block_class.block(' + str(block.data) + ')\n')
        f.write('b.block_number = ' + str(block.block_number) + '\n')
        f.write('b.block_hash = ' + '"' + str(block.block_hash) + '"\n')
        f.write('b.nonce = ' + str(block.nonce) + '\n')
        f.write('b.previous_block_hash = ' + '"' + str(block.previous_block_hash) + '"\n')
        f.write('blockchain.append(b)\n')
        f.close()

    def mining(self, block):
        block.block_number = len(self.chain)
        try:
            previous_hash = self.chain[block.block_number - 1].block_hash
            block.set_previous_hash(previous_hash)
        except IndexError:
            pass

        nonce = 0
        while True:
            block.set_block_hash()
            if  int(block.block_hash,16) < int(('0x' + self.difficulty * '0' + (64-self.difficulty)*'f'), 16):
                self.add_block(block)
                break
            else:
                nonce += 1
                block.set_nonce(nonce)
        
    def is_valid(self):
        for block in self.chain:
            prehash = self.chain[block.block_number].previous_block_hash
            realprehash = self.chain[block.block_number -1 ].block_hash
            realhash = '0x' + TM_hash.do_sha256(str(block.nonce) + TM_hash.do_sha256(TM_hash.do_sha256(str(block.data)) + block.previous_block_hash))
            if realprehash == self.chain[len(self.chain) - 1].block_hash:
                realprehash = 'follow the white rabbit'
            if prehash != realprehash:
                return False
            elif realhash != block.block_hash:
                return False
        return True

def main(*args):
    bchain = blockchain(sec_chain)
    for arg in args:
        kcolb = block_class.block(arg)
        bchain.mining(kcolb)
    v = bchain.is_valid()
    if v == False:
        print('something\'s wrong, I can feel it')

time0 = time.time()
main(
    ['load up on guns, bring your friends', 'it\'s fun to lose and to pretend', 'she\'s overboard and self-assured', 'oh no I know a dirty word'],
    [('hello ' *3 + 'how low? ')* 3 ,'hello, hello, hello', ''],
    ['whith the lights out, it\'s less dangerous', 'here we are now, entertain us', 'I feel stupid and contagious'],
    ['here we are now, entertain us', 'A mulatto, an albino, a mosquito, my libido', 'yeah, hey, yay'],
    [123, 277353, 1991]
)
time1 = time.time()
print(time1 - time0)


```

### Titre 2

```{figure} figures/make-html.png

```
