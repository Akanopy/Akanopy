### Herkese merhaba ben Akano 👋


- 💬 Ben discord.js,Pyhton İle uğraşan birisiyim
- ⚡ Bu hesabıma elimden geldiğince kodlar,örnekler paylaşacağım
- ❤️ Şimdilik Anlatıcaklarım Bu kadar olsun :>
- 🥳 Discord, Steam Hesaplarım : [Akano#8824](https://discord.com/channels/@me) [Steam](https://steamcommunity.com/profiles/76561199044085364)



![Discord Badge](https://media.discordapp.net/attachments/608711485849337856/818181207996235796/da29c18358462edb2b07762f5d7f813e.gif)




on:
  schedule:
    - cron: '0 */12 * * *' # every 12 hours
  push:
    branches:
      - master
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
      with:
        fetch-depth: 0
    - name: Generate README.md
      uses: teoxoy/profile-readme-stats@v1
      with:
        token: ${{ secrets.USER_TOKEN }}
    - name: Update README.md
      run: |
        if [[ "$(git status --porcelain)" != "" ]]; then
        git config user.name github-actions[bot]
        git config user.email 41898282+github-actions[bot]@users.noreply.github.com
        git add .
        git commit -m "Update README"
        git push
        fi
