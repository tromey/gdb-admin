gdb-admin
=========

Admin scripts for use with gdb


merge-gcc-to-src
----------------

This merges shared files from GCC to binutils-gdb.git.

To use this script:

1. Set up a new directory to work in.  Let's call it X.

    mkdir X

2. Check out GCC and binutils-gdb:

    cd X
    git clone ssh://sourceware.org/git/binutils-gdb.git
    git clone ssh://gcc.gnu.org/git/gcc.git

3. Write a "config.pl" file that holds the location.  config.pl
   should be in the same directory as merge-gcc-to-src.

    $SYNC = 'X';
    
4. Find the most recent commit that was passed to the script.
   Normally the script will automatically determine this by looking at
   the "master" ref in the gcc repository, but you have to find it the
   first time.  You can find this commit by looking in
   binutils-gdb.git, finding the most recent sync, and then finding
   the corresponding commit in gcc.git.

5. Now run the script:

    merge-gcc-to-src COMMIT

6. The script will print some output as it works.  When it is done,
   you can look in X/Outputs to see what commits it thinks must be
   merged.  You must usually do this by hand, one commit at a time,
   using "git am".  Sometimes a bit of editing or merging is required.
