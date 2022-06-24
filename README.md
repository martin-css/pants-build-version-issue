# Minimal Reproducible Example

Attempting to create a pex archive with pants fails with the following error:

```
WARNING: Requested cartopy==0.20.2 from https://files.pythonhosted.org/packages/f6/55/1e1c737dc9436b320deead73d1c455ddbb74b8b6992081863492f6f6378a/Cartopy-0.20.2.tar.gz#sha256=4d08c198ecaa50a6a6b109d0f14c070e813defc046a83ac5d7ab494f85599e35 (from -r 3rdparty/python/default.lock (line 1)), but installing version 0.0
WARNING: Discarding https://files.pythonhosted.org/packages/f6/55/1e1c737dc9436b320deead73d1c455ddbb74b8b6992081863492f6f6378a/Cartopy-0.20.2.tar.gz#sha256=4d08c198ecaa50a6a6b109d0f14c070e813defc046a83ac5d7ab494f85599e35 (from https://pypi.org/simple/cartopy/) (requires-python:>=3.7). Requested cartopy==0.20.2 from https://files.pythonhosted.org/packages/f6/55/1e1c737dc9436b320deead73d1c455ddbb74b8b6992081863492f6f6378a/Cartopy-0.20.2.tar.gz#sha256=4d08c198ecaa50a6a6b109d0f14c070e813defc046a83ac5d7ab494f85599e35 (from -r 3rdparty/python/default.lock (line 1)) has different version in metadata: '0.0'
ERROR: Could not find a version that satisfies the requirement cartopy==0.20.2
ERROR: No matching distribution found for cartopy==0.20.2
pid 22130 -> /root/.cache/pants/named_caches/pex_root/venvs/24c8ad77660911810f98bcf75a8264e3b2d1722d/587d95bb4f21c70aedf0708bac1e6e728689715d/pex --disable-pip-version-check --no-python-version-warning --exists-action a --isolated -q --cache-dir /root/.cache/pants/named_caches/pex_root --log /tmp/process-execution5ET1Nb/.tmp/pex-pip-logmd298q9m/pip.log download --dest /tmp/process-execution5ET1Nb/.tmp/tmptyjkfz4j/usr.local.bin.python3.9 --no-deps --requirement 3rdparty/python/default.lock --index-url https://pypi.org/simple/ --retries 5 --timeout 15 exited with 1 and STDERR:
None
```

This repo provides a really simple project (using Poetry) which has a single dependency on [cartopy](https://scitools.org.uk/cartopy/docs/latest/).

To reproduce the error, run:

```
./pants export ::
```
