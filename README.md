# Simple Online 3D Viewer

This project is a lightweight online viewer for GLB/GLTF models that lets you switch between character animations and inspect custom assets directly in the browser. It runs entirely on static files, so you can host it on any static hosting platform.

## Local development

Because the viewer loads external model and texture files, open the project through a local web server instead of directly from the filesystem. A quick way to do this is with [`serve`](https://www.npmjs.com/package/serve):

```bash
npm install --global serve
serve .
```

Then browse to the URL printed in the terminal (for example <http://localhost:3000>) to interact with the viewer.

## Deploying to GitHub Pages

The repository includes a GitHub Actions workflow that automatically publishes the site to GitHub Pages whenever you push to the `main` branch.

1. Push this repository to GitHub and make sure your default branch is named `main`.
2. In your GitHub repository, open **Settings → Pages** and ensure **Build and deployment** is set to **GitHub Actions**. (The workflow will automatically enable Pages if it is the first deployment.)
3. The `Deploy static site to GitHub Pages` workflow will build and deploy the contents of the repository to the `gh-pages` branch automatically on every push to `main`. You can also trigger it manually from the **Actions** tab using the `Run workflow` button.
4. After the first successful run, the public site URL appears both in the workflow run summary and on the **Settings → Pages** page.

If you need to adjust the workflow (for example to exclude large source assets), edit [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) accordingly.

## Uploading your own assets

The viewer UI supports uploading multiple model files (`.glb`, `.gltf`, and companion `.bin` files) along with textures. Drag and drop the files into the page or use the upload controls in the sidebar. Texture filenames must match the references used inside the model for them to load correctly.
