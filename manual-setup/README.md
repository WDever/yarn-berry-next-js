# VSCode 설정

https://yarnpkg.com/getting-started/editor-sdks

아래 과정이 선행되지 않을 시 정상적으로 패키지의 정보를 불러오지 못함.

1. [ZipFS](https://marketplace.visualstudio.com/items?itemName=arcanis.vscode-zipfs) 확장 설치
2. `yarn dlx @yarnpkg/sdks vscode` 커맨드를 통해 .yarn/sdks 디렉토리 생성
3. TypeScript 버전을 "Use Workspace Version" 로 설정

# 새로운 Next.js 프로젝트에 yarn berry 적용하기

1. `mkdir [project-name]` and `cd [project-name]`
2. `yarn init -2`
3. `yarn add next react react-dom`
4. pakage.json 에

   ```json
   "scripts": {
     "dev": "next dev",
     "build": "next build",
     "start": "next start",
     "lint": "next lint"
   }
   ```

   위 내용 추가

5. `mkdir pages && touch pages/index.tsx` 혹은 `mkdir src && mkdir src/pages && touch pages/index.tsx`
6. 위의 index.tsx 파일 내에

   ```jsx
   function HomePage() {
     return <div>Welcome to Next.js!</div>;
   }

   export default HomePage;
   ```

   내용 추가

7. `yarn dev`
