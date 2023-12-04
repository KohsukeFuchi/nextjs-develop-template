# Next.jsでWebページを開発するときの環境テンプレート

## 事前準備

### nodebrewをインストールする
ローカルでプロジェクトを作成してからDockerに環境を移すため，
ローカルでNext.jsを作成できる必要がある。

```shell
$ brew install nodebrew
$ nodebrew setup

$ echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.zshrc
$ source ~/.zshrc

# 利用するバージョンを指定する
$ nodebrew install latest
$ nodebrew use latest
```

### yarnをインストールする

```shell
$ npm install -g yarn
```

### pnpmをインストールする

```shell
$ npm install -g pnpm
```

## DockerとMacのNodeのバージョンを合わせる

```shell
# 使用できるバージョンの確認
$ nodebrew ls-remote

# バージョンの確認
$ node -v
$ npm -v
```

**2023年12月4日**

- Node: v21.3.0
- npm: 10.2.4

## バージョンの更新

```shell
$ pnpm dlx create-next-app@latest --ts
What is your project name? > container

# Prettier
$ cd container
$ pnpm add --save-dev prettier eslint-config-prettier prettier-plugin-tailwindcss

# ESlint
$ pnpm add --save-dev @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-plugin-import eslint-plugin-unused-imports

# Husky & lint-staged
$ pnpm add --save-dev husky lint-staged
$ pnpm pkg set scripts.prepare="husky install"
$ pnpm run prepare
$ pnpm dlx husky add .husky/pre-commit "npx lint-staged"

# Jest & React Testing Library
$ pnpm add --save-dev jest jest-environment-jsdom @types/jest @testing-library/react @testing-library/jest-dom

# Storybook
$ pnpm dlx storybook@latest init
✔ Do you want to manually choose a Storybook project type to install? … yes
✔ Please choose a project type from the following list: › nextjs

$ pnpm add --save-dev @storybook/addon-styling
$ pnpm addon-styling-setup
```

