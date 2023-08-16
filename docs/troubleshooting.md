# Troubleshooting

!!! warning
    This documentation site is a work in progress, and is being tested and refined internally. Do not use this documentation as a reference in its current state.

## What should I do if my notebook is hanging/non-responsive?
* First try to restart your Jupyter Kernel. From your notebook, go to Kernel > Shutdown and confirm by clicking the Shutdown button. Then click on Kernel > Restart Kernel...
* If restarting your kernel did not resolve the problem, try restarting your Jupyter server. Go to your JupyterHub home page via File > Hub Control Panel. From there, you can click on the "Stop My Server" button. Wait a minute or two for your server to completely stop and then click Start My Server.
* If restarting your kernel or server did not resolve the problem, contact your instructor or other course staff. If you are course staff, or cannont resolve the issue with their help, reach out to atg@fas.harvard.edu for assistance.

## When I try to save, I get an "Invalid response: 403" error

**Symptoms:** This error accompanies other problems like disappearing text in cells, and the error message popping up on its own. The best way to verify is to try to save a file and see if you see the text "Invalid response: 403".

**Solution:** This indicates a networking issue that needs to be resolved by the developers that maintain the JupyterHub configuration. The problem is usually specific to a single file, or triggered by trying to save certain code. To help us fix this issue as quickly as possible, please send a message to [atg@fas.harvard.edu](mailto:atg@fas.harvard.edu) with your name, what class you are using JupyterHub in, and the name of the file that you were editing when the error occurred.

We have only observed this error in Safari and Chrome, so using Firefox may be a way to continue working in the meantime.

We have also observed that once the file stops saving, the download option in JupyterLab will no longer reflect current changes. To back up the work you have done, you will need to copy the most recently edited cells into another text file. Since this error prevents files from being saved, we recommend stopping work in a notebook where this error occurs as soon as you see it, as any work you do after encountering it is likely to be lost.

## When importing matplotlib, I get an error about a cache directory

**Symptoms:** When importing `matplotlib.pyplot`, as in via the following code,

```python
import matplotlib.pyplot as plt
```

you may encounter an error like this:

> ```Matplotlib created a temporary config/cache directory at /tmp/matplotlib-nj9ket54 because the default path (/home/jovyan/.cache/matplotlib) is not a writable directory; it is highly recommended to set the MPLCONFIGDIR environment variable to a writable directory, in particular to speed up the import of Matplotlib and to better support multiprocessing.```

**Solution:** The library will still work, but may not perform as well. To fix this, add the following code to notebooks before importing `matplotlib.pyplot`:

```python
import os
os.environ["MPLCONFIGDIR"] = os.path.join(os.getcwd(), ".cache/matplotlib")
```

This will configure `matplotlib` to use a cache directory in your own home directory, where it won't have any trouble writing whatever it needs to. You may not need the `import os` if you've already imported it.
