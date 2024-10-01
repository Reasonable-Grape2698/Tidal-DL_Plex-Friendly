Docker:
```
FROM python:3.11-slim
COPY Tidal-DL_Plex-Friendly TIDALDL-PY
WORKDIR TIDALDL-PY
ENV PYTHONPATH=/TIDALDL-PY/tidal_dl/
RUN apt-get clean && rm -rf /var/lib/apt/lists/*
RUN pip install pipenv && \
  apt-get update && \
  apt-get install -y --no-install-recommends gcc python3-dev libssl-dev && \
pip3 install --no-cache-dir psutil && pip3 install --no-cache-dir -r requiremen>
pip3 install --no-cache-dir -e AIGPY/ && \
pip3 install --no-cache-dir -e . &&  apt-get remove -y gcc python3-dev libssl-d>
  apt-get autoremove -y && \
  pip uninstall pipenv -y
CMD tidal-dl
```

Non-docker (haven't tested)
```
pip3 install --no-cache-dir -r requirements.txt --user
pip3 install --no-cache-dir -e AIGPY/ --user
pip3 install --no-cache-dir -e . --user

Note I've created a pull request for the aigby glitch, it's a single line of code changed to avoid it turning strings into e, x, a, m, p, l, e.
```
