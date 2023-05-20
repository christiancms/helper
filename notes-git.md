GIT  ISO-8859-1
git status
 git checkout -b fse-bor-us042-ajuste-db
git add .
git commit -m "Ajustes para incluir e listar"
git push --set-upstream origin fse-bor-us042-ajuste-db

git status
git checkout -b fse-bor-us042-ajuste-db

git status
git add .
git commit --amend
(close editor)
git push --force -u origin

git push origin fse-bor-ajustes-endpoints

Go to working branch(fse-bor-ajustes-endpoints)
git rebase origin/fse-bor
git push -f
Create Pull Request
