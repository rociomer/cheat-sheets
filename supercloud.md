### Useful [Supercloud](supercloud.mit.edu) set-up instructions 

The MIT Supercloud is an HPC cluster available to researchers at the MIT Lincoln Laboratory in collaboration with researchers at other institutions.

For starters, you can request an account at https://supercloud.mit.edu/requesting-account.

Once you have an account (can take about a week or so), you can get started logging in by following the instructions at https://supercloud.mit.edu/getting-started.

Note that if you will be logging in to the Supercloud via VSCode (and have the appropriate extensions installed), the default settings in `VSCode Remote - SSH` will cause it to fail to connect due to it trying to do file locking in your home directory, which is disabled on the Supercloud for performance reasons. As such, you can make it use the local filesystem by:

1. Going to the VSCode settings
2. Finding the "Remote - SSH" extension settings
3. Once in the "Remote - SSH" settings, check the box next to "Remote.SSH: Lockfiles in Tmp". 

What this will do is put any lockfiles in `/tmp`, rather than your home directory, and then you should be able to SSH to the Supercloud via VSCode. 

For instructions on how to submit interactive and batch jobs on the Supercloud using LLsub, see this page https://supercloud.mit.edu/submitting-jobs.
