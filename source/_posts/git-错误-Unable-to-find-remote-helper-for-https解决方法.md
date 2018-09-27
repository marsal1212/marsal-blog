---
title: 'git 错误: Unable to find remote helper for https解决方法'
date: 2018-09-27 19:31:03
tags:
---

git 错误: Unable to find remote helper for 'https'，是因为 /usr/libexec/git-core/ 路径没在 PATH 环境变量中。

我们查看一下：

```bash
   ls /usr/libexec/git-core/
   git                           git-fast-import        git-mergetool--lib       git-revert
   git-add                       git-fetch              git-merge-tree           git-rev-list
   git-add--interactive          git-fetch-pack         git-mktag                git-rev-parse
   git-am                        git-filter-branch      git-mktree               git-rm
   git-annotate                  git-fmt-merge-msg      git-mv                   git-send-pack
   git-apply                     git-for-each-ref       git-name-rev             git-shell
   git-archive                   git-format-patch       git-notes                git-sh-i18n
   git-bisect                    git-fsck               git-pack-objects         git-sh-i18n--envsubst
   git-bisect--helper            git-fsck-objects       git-pack-redundant       git-shortlog
   git-blame                     git-gc                 git-pack-refs            git-show
   git-branch                    git-get-tar-commit-id  git-parse-remote         git-show-branch
   git-bundle                    git-grep               git-patch-id             git-show-index
   git-cat-file                  git-hash-object        git-peek-remote          git-show-ref
   git-check-attr                git-help               git-prune                git-sh-setup
   git-check-ignore              git-http-backend       git-prune-packed         git-stage
   git-checkout                  git-http-fetch         git-pull                 git-stash
   git-checkout-index            git-http-push          git-push                 git-status
   git-check-ref-format          git-imap-send          git-quiltimport          git-stripspace
   git-cherry                    git-index-pack         git-read-tree            git-submodule
   git-cherry-pick               git-init               git-rebase               git-submodule--helper
   git-clean                     git-init-db            git-rebase--am           git-subtree
   git-clone                     git-instaweb           git-rebase--interactive  git-symbolic-ref
   git-column                    git-log                git-rebase--merge        git-tag
   git-commit                    git-lost-found         git-receive-pack         git-tar-tree
   git-commit-tree               git-ls-files           git-reflog               git-unpack-file
   git-config                    git-ls-remote          git-relink               git-unpack-objects
   git-count-objects             git-ls-tree            git-remote               git-update-index
   git-credential                git-mailinfo           git-remote-ext           git-update-ref
   git-credential-cache          git-mailsplit          git-remote-fd            git-update-server-info
   git-credential-cache--daemon  git-merge              git-remote-ftp           git-upload-archive
   git-credential-gnome-keyring  git-merge-base         git-remote-ftps          git-upload-pack
   git-credential-store          git-merge-file         git-remote-http          git-var
   git-describe                  git-merge-index        git-remote-https         git-verify-pack
   git-diff                      git-merge-octopus      git-remote-testpy        git-verify-tag
   git-diff-files                git-merge-one-file     git-repack               git-web--browse
   git-diff-index                git-merge-ours         git-replace              git-whatchanged
   git-difftool                  git-merge-recursive    git-repo-config          git-write-tree
   git-difftool--helper          git-merge-resolve      git-request-pull         mergetools
   git-diff-tree                 git-merge-subtree      git-rerere
   git-fast-export               git-mergetool          git-reset
```

这导致里面的 git-remote-https, git-remote-http 这些得不到执行。所以 git 所表现出来的功能不全。

# 解决办法

将 /usr/libexec/git-core 纳入 PATH，至少在使用 git 之前，设置一下PATH。

```bash
    $ PATH=$PATH:/usr/libexec/git-core
```