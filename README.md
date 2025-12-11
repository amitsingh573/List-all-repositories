mkdir -p ~/github-all
cd ~/github-all

gh repo list amitsingh573 --limit 200 --ssh | awk '{print $1}' | while read repo; do
  gh repo clone "$repo"
done gh repo list amitsingh573 --limit 200 --json name --jq '.[].name' | while read name; do
  echo "========== $name =========="
  ls -1 "$name"
  echo ""
done
