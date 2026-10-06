name: Sherlock Bot

on:
  schedule:
    - cron: '*/5 * * * *'
  workflow_dispatch:
  push:
    branches: [ main ]

jobs:
  run-bot:
    runs-on: ubuntu-latest
    timeout-minutes: 5
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Cache pip
        uses: actions/cache@v4
        with:
          path: ~/.cache/pip
          key: ${{ runner.os }}-pip-${{ hashFiles('requirements.txt') }}

      - name: Install deps
        run: pip install -r requirements.txt

      - name: Run bot
        run: timeout 240 python bot.py || true
