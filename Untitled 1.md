```
solie@SJE_DESK MINGW64 ~
$ node -v
v22.18.0

solie@SJE_DESK MINGW64 ~
$ npm -v
10.9.3

solie@SJE_DESK MINGW64 ~
$ git clone https://github.com/jackyzha0/quartz.git
Cloning into 'quartz'...
remote: Enumerating objects: 11854, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 11854 (delta 1), reused 0 (delta 0), pack-reused 11849 (from 2)
Receiving objects: 100% (11854/11854), 36.76 MiB | 21.50 MiB/s, done.
Resolving deltas: 100% (7438/7438), done.

solie@SJE_DESK MINGW64 ~
$ cd quartz

solie@SJE_DESK MINGW64 ~/quartz (v4)
$ npm i

added 479 packages, and audited 480 packages in 7s

169 packages are looking for funding
  run `npm fund` for details

1 low severity vulnerability

To address all issues, run:
  npm audit fix

Run `npm audit` for details.

solie@SJE_DESK MINGW64 ~/quartz (v4)
$ npx quartz create

T   Quartz v4.5.1
|
o  Choose how to initialize the content in `C:\Users\solie\quartz\content`
|  Empty Quartz
|
o  Choose how Quartz should resolve links in your content. This should match
Obsidian's link format. You can change this later in `quartz.config.ts`.
|  Treat links as shortest path
|
—  You're all set! Not sure what to do next? Try:
  • Customizing Quartz a bit more by editing `quartz.config.ts`
  • Running `npx quartz build --serve` to preview your Quartz locally
  • Hosting your Quartz online (see: https://quartz.jzhao.xyz/hosting)

solie@SJE_DESK MINGW64 ~/quartz (v4)
$ npx quartz build --serve

 Quartz v4.5.1

Cleaned output directory `public` in 501μs
Found 1 input files from `content` in 9ms
Parsed 1 Markdown files in 131ms
Filtered out 0 files in 47μs
Emitted 15 files to `public` in 550ms
Done processing 1 files in 692ms
Started a Quartz server listening at http://localhost:8080
hint: exit with ctrl+c
[200] /
[200] /index.css
[200] /prescript.js
[200] /postscript.js
[200] /static/contentIndex.json
[200] /static/icon.png
```

