# Yarn Symlinking Bug

Let's assume the current project cwd is `/Users/hammadbalkhi/yarn-bug`

Then: 
1. Create a folder inside the workspace:
`mkdir -p /Users/hammadbalkhi/yarn-bug/my-workspace/backup`

2. Create a symlink:
`ln -s /Users/hammadbalkhi/yarn-bug/my-workspace/backup /Users/hammadbalkhi/yarn-bug/my-workspace/node_modules`

3. Run `Yarn install`

You will see both `yarn-bug/my-workspace/backup` & `yarn-bug/my-workspace/node_modules` populated with the same contents.

4. Now remove `"react": "17"` from `yarn-bug/my-workspace/package.json`

5. Run `yarn install`

You will see error:
`Error: ENOTDIR: not a directory, rmdir '/Users/hammadbalkhi/yarn-bug/my-workspace/node_modules'`