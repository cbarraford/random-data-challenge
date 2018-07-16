# Random Compression Challenge
Proof you can compress a file of random data

Mark Nelson has a
[challenge](https://marknelson.us/posts/2012/10/09/the-random-compression-challenge-turns-ten.html)
for anyone to compress a million digit file. This repo is my submission that
it is possible. 

Furthermore, the algorithm that I have developed can be used on any file or
any size and be able to compress it (at least a byte), and I believe it could
be used to compress a file multiple times. Maybe even just to a few bytes. But
there is more work to be done to prove this (TODO).

For now, I have been able to compress this given file by 8 bytes.

### How to decompress
The files in the `compressed_data` directory are 8 bytes less than the
original file, `AMillionRandomDigits.bin`. To decompress the compressed files,
run the following command on a linux box (works on mac as well). Sorry, no
windows support right now, although it isn't too hard to do.
```
docker run --rm -v $(pwd):/code alpine /code/decompressor --source /code/compressed_data --target AMillionRandomDigits.bin
```

Once the decompressed file is created, you can verify it has the correct size
and checksum as the original file in the `uncompressed_data` directory.

#### Note on filenames
When we compress a file, we do break into separate files, but the file name
does NOT contain any data from our original file, `AMillionRandomDigits.bin`.
The only thing that is important about the file names, is maintaining order,
so we know which file comes first/second/last/etc when we decompress the file.
Because of this, in theory, you could change the file names to be whatever you
want, as long as, they still in the same order they are now. 
