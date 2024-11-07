---
tags:
  - reference/github
date created: Wed, Oct 30th 2024, 12:26 pm
date modified: Sun, Nov 3rd 2024, 1:36 am
---

```
Git command to push file to repository:
git clone https://github.com/your-username/your-repository.git
mv /path/to/your/input.py /path/to/your/local/repository
cd /path/to/your/local/repository
git add input.py
git commit -m "message for commit"
git push origin main
(for large datasets, need to use lfs)
git lfs track " dog_dataset.zip " 
git add .gitattributes 
git add dog_dataset.zip
git lfs ls-files

```