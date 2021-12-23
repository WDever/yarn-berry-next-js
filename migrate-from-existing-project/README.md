# VSCode 설정

https://yarnpkg.com/getting-started/editor-sdks

아래 과정이 선행되지 않을 시 정상적으로 패키지의 정보를 불러오지 못함.

1. [ZipFS](https://marketplace.visualstudio.com/items?itemName=arcanis.vscode-zipfs) 확장 설치
2. `yarn dlx @yarnpkg/sdks vscode` 커맨드를 통해 .yarn/sdks 디렉토리 생성
3. TypeScript 버전을 "Use Workspace Version" 로 설정

# 기존 Next.js 프로젝트에 yarn berry 적용하기

[https://yarnpkg.com/getting-started/migration](https://yarnpkg.com/getting-started/migration)

1. `yarn set version berry` 를 통해 yarn berry 로 전환
2. `.yarnrc.yml` 파일에 `[nodeLinker: node-modules](https://yarnpkg.com/configuration/yarnrc#nodeLinker)` 추가

   `yarnrc` 혹은 `npmrc` 를 사용중이었다면 `yarnrc.yml` 로 마이그레이션 ([참고](https://yarnpkg.com/getting-started/migration#update-your-configuration-to-the-new-settings))

   > Yarnrc files (named this way because they must be called `.yarnrc.yml`) are the one place where you'll be able to configure Yarn's internal settings. While Yarn will automatically find them in the parent directories, they should usually be kept at the root of your project (often your repository). **Starting from the v2, they must be written in valid Yaml and have the right extension** (simply calling your file `.yarnrc` won't do).

3. node_modules 삭제 후 `yarn install`
4. .gitignore
   1. w Zero-Installs

      ```yaml
      .yarn/*
      !.yarn/cache
      !.yarn/patches
      !.yarn/plugins
      !.yarn/releases
      !.yarn/sdks
      !.yarn/versions
      ```

   2. w/o Zero-Installs

      ```yaml
      .pnp.*
      .yarn/*
      !.yarn/patches
      !.yarn/plugins
      !.yarn/releases
      !.yarn/sdks
      !.yarn/versions
      `
      ```
