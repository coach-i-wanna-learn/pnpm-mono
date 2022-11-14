
> https://blog.nrwl.io/setup-a-monorepo-with-pnpm-workspaces-and-speed-it-up-with-nx-bc5d97258a7e

Node 生态的项目管理比较初级，我们需要掌握更多的细节，进行琐碎的配置，有时候这是让人感到沮丧的并且是浪费时间的


monorepo 的难点：
- 各个 repo 相互依赖
- 各个 repo 依赖管理
- 各个 repo 版本管理（统一版本发布，独立发布）

通常形式有两种形式的 monorepo

```
app-centric
  apps
  packages


package-centric
  packages
```

## app-centric
```shell
mkdir apps packages

touch pnpm-workspace.yaml

cd apps

# 不要进行以来安装，默认使用 npm，我们改为 pnpm
pnpm create qwik@latest

cd ..

pnpm install


mkdir -p packages/shared-ui


cd packages/shared-ui

pnpm init -y

pnpm add --filter shared-ui react
pnpm add --filter shared-ui typescript -D
pnpm add --filter shared-ui @types/react -D

pnpx tsc --init

```


```

pnpm --filter my-qwik-basic-starter start
pnpm --filter shared-ui build
```