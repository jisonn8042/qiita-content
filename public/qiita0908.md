---
title: 初めてqittaにGitHubを活用して記事を作成するとき知って置いたら良かったこと
tags:
  - Qiita
  - 記事作成
private: true
updated_at: '2025-09-17T17:00:37+09:00'
id: a507a0e2d3dd093aaa04
organization_url_name: null
slide: false
ignorePublish: false
---
# 初めてqittaにGitHubを活用して記事を作成するとき知って置いたら良かったこと

## この記事を書くようになったきっかけ
qiitaに自分の経験や知ったことを共有したくて記事を書く方法を調べてみたのですが
各方法には３つがありました。

- qiitaサイトで直接作成する方法
- qiitaCLIを使ってローカル環境で作成する方法
- GitHubと連動して作成する方法

この中でGitHubを使うといつ更新したのか、更新日

    - name: Commit and push diff # Not executed recursively even if `push` is triggered. See https://docs.github.com/en/actions/using-workflows/triggering-a-workflow#triggering-a-workflow-from-a-workflow
      run: |
        git add ${{ inputs.root }}/public/*
        if ! git diff --staged --exit-code --quiet; then
          git config --global user.name 'github-actions[bot]'
          git config --global user.email '41898282+github-actions[bot]@users.noreply.github.com'
          git commit -m "${COMMIT_MESSAGE}"
          git push
        fi
      shell: bash
      env:
        COMMIT_MESSAGE: ${{ inputs.commit-message }}


git add ${{ inputs.root }}/public/*
        
새 파일이 생성되지 않고 커밋되지 않는 이유는 Git이 변경사항을 인식하지 못해서가 아니라, action.yml 파일의 git add 명령어가 새 파일이 생성되는 위치를 포함하고 있지 않기 때문입니다.