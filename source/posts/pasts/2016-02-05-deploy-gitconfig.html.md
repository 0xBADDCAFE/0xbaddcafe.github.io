---
title: middleman deploy 時に使われる git の config
date: 2016-02-05 11:00 JST
tags: middleman
---

middleman deploy は自動で指定したリポジトリへの push までやってくれるが、その為に build ディレクトリ配下を
別リポジトリとして管理する。その為初回 deploy 時のソース側リポジトリの設定が build 側に残ったままとなる
ことがある。

deploy.host を明示的に指定しないまま source 側のリモートを set-url のみで書き換えたりした際にハマる（ハマった）
