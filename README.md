# react-native-bundle-visualizer

[![react-native-bundle-visualizer on npm](https://badgen.net/npm/v/react-native-bundle-visualizer)](https://www.npmjs.com/package/react-native-bundle-visualizer)
[![react-native-bundle-visualizer downloads](https://badgen.net/npm/dm/react-native-bundle-visualizer)](https://www.npmtrends.com/react-native-bundle-visualizer)
[![react-native-bundle-visualizer install size](https://packagephobia.com/badge?p=react-native-bundle-visualizer)](https://packagephobia.com/result?p=react-native-bundle-visualizer)
[![CI status](https://github.com/callstack/react-native-bundle-visualizer/actions/workflows/test.yml/badge.svg)](https://github.com/callstack/react-native-bundle-visualizer/actions/workflows/test.yml)


See what's inside your react-native bundle 📦

![bundle-visualizer-animation](./react-native-bundle-visualizer2.gif)

Uses the awesome [source-map-explorer](https://github.com/danvk/source-map-explorer) to visualize the output of the [Metro bundler](https://github.com/facebook/metro).

## Purpose

Sometimes, importing a single JavaScript library can drastically increase your bundle size. This package helps you to identify such a library, so you can keep the bundle size low and loading times fast.

## Usage

Using `npx` is the recommended way to run the visualizer

```sh
# React Native 0.72+
npx react-native-bundle-visualizer@latest
# or Expo SDK 50+
npx react-native-bundle-visualizer@latest --expo
```

### Or you can install as a dev-dependency

```sh
yarn add --dev react-native-bundle-visualizer
# or npm
npm install --save-dev react-native-bundle-visualizer
```

To run the local version of visualizer, use the following command:

```sh
npx react-native-bundle-visualizer # if installed by yarn or npm
yarn run react-native-bundle-visualizer # if installed by Yarn
```

## Command line arguments

All command-line arguments are optional. By default a production build will be created for the `ios` platform.

| Option            | Description                                                                                                                                                                 | Example                                   |
| ----------------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| `platform`        | Platform to build (default is **ios**)                                                                                                                                      | `--platform ios`                          |
| `dev`             | Dev or production build (default is **false**)                                                                                                                              | `--dev false`                             |
| `entry-file`      | Entry-file (when omitted tries to auto-resolve it)                                                                                                                          | `--entry-file ./index.ios.js`             |
| `bundle-output`   | Output bundle-file (default is **tmp**)                                                                                                                                     | `--bundle-output ./myapp.bundle`          |
| `format`          | Output format **html**, **json** or **tsv** (default is **html**) (see [source-map-explorer options][smeo])                                                                 | `--format json`                           |
| `only-mapped`     | Exclude "unmapped" bytes from the output (default is **false**). This will result in total counts less than the file size.                                                  | `--only-mapped`                           |
| `verbose`         | Dumps additional output to the console (default is **false**)                                                                                                               | `--verbose`                               |
| `reset-cache`     | Removes cached react-native files (default is **false**)                                                                                                                    | `--reset-cache`                           |
| `--expo`          | Set this to true/ false based on whether using expo or not. For eg, set `--expo true` when using expo. Not required to pass this for react-native cli. (default is `false`) | `--expo false`                            |
| `--border-checks` | Pass the same flag to the underlying `source-map-explorer` to enable invalid mapping column/line checks. (default is **false**, no check)                                   | `--no-border-checks` or `--border-checks` |

[smeo]: https://github.com/danvk/source-map-explorer#options


## Common questions

#### 1. What version of React Native and Expo is supported?

See the [version compatibility](#version-compatibility) table below.

#### 2. What does `[unmapped]` represent?

`[unmapped]` is code in a final bundle without mapping to original source code (usually generated by bundlers: Webpack, Metro, Babel)

You can [open your source maps online](https://evanw.github.io/source-map-visualization) and check it

See example (red borders is unmapped code):

![](https://github.com/user-attachments/assets/9f0d095f-336e-4bda-af67-b0df09d3a5fb)

#### 3. What alternatives I can use to inspect my bundle?

See the [similar projects](#similar-projects) section below for alternatives to this package.

#### 4. `InvalidMappingColumn` error

> example: Your source map refers to generated column Infinity on line 2, but the source only contains 2075 column(s) on that line

if you faced this error, try to run the visualizer with `--no-border-checks` flag to disable invalid mapping column/line checks.


## Similar projects

You can use then following alternatives:

- [expo-atlas](https://github.com/expo/atlas) [![expo-atlas downloads](https://badgen.net/npm/dm/expo-atlas)](https://www.npmtrends.com/expo-atlas) [![expo-atlas install size](https://packagephobia.com/badge?p=expo-atlas)](https://packagephobia.com/result?p=expo-atlas)
- [expo-atlas-without-expo](https://github.com/v3ron/expo-atlas-without-expo) [![expo-atlas-without-expo downloads](https://badgen.net/npm/dm/expo-atlas-without-expo)](https://www.npmtrends.com/expo-atlas-without-expo) [![expo-atlas-without-expo install size](https://packagephobia.com/badge?p=expo-atlas-without-expo)](https://packagephobia.com/result?p=expo-atlas-without-expo)
- [react-native-bundle-visualizer](https://github.com/callstack/react-native-bundle-visualizer) [![react-native-bundle-visualizer downloads](https://badgen.net/npm/dm/react-native-bundle-visualizer)](https://www.npmtrends.com/react-native-bundle-visualizer)[![react-native-bundle-visualizer install size](https://packagephobia.com/badge?p=react-native-bundle-visualizer)](https://packagephobia.com/result?p=react-native-bundle-visualizer)
- [react-native-bundle-discovery](https://github.com/retyui/react-native-bundle-discovery) [![react-native-bundle-discovery downloads](https://badgen.net/npm/dm/react-native-bundle-discovery)](https://www.npmtrends.com/react-native-bundle-discovery) [![react-native-bundle-discovery install size](https://packagephobia.com/badge?p=react-native-bundle-discovery)](https://packagephobia.com/result?p=react-native-bundle-discovery)
- [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) [![webpack-bundle-analyzer downloads](https://badgen.net/npm/dm/webpack-bundle-analyzer)](https://www.npmtrends.com/webpack-bundle-analyzer)[![webpack-bundle-analyzer install size](https://packagephobia.com/badge?p=webpack-bundle-analyzer)](https://packagephobia.com/result?p=webpack-bundle-analyzer)
- [bundle-stats](https://github.com/relative-ci/bundle-stats/tree/master/packages/cli#readme) [![bundle-stats downloads](https://badgen.net/npm/dm/bundle-stats)](https://www.npmtrends.com/bundle-stats)[![bundle-stats install size](https://packagephobia.com/badge?p=bundle-stats)](https://packagephobia.com/result?p=bundle-stats)
- [statoscope](https://github.com/statoscope/statoscope) [![@statoscope/cli downloads](https://badgen.net/npm/dm/@statoscope/cli)](https://www.npmtrends.com/@statoscope/cli)[![@statoscope/cli install size](https://packagephobia.com/badge?p=@statoscope/cli)](https://packagephobia.com/result?p=@statoscope/cli)


## Version compatibility

| Version                                                                      | Comments                                                         |
|------------------------------------------------------------------------------|------------------------------------------------------------------|
| 4.x                                                                          | Compatible with React Native 0.72+ or Expo SDK 50+ (Node.js 20+) |
| [3.x](https://github.com/IjzerenHein/react-native-bundle-visualizer/tree/v3) | Compatible with React-Native CLI bootstrapped projects and Expo SDK 41 or higher. |
| [2.x](https://github.com/IjzerenHein/react-native-bundle-visualizer/tree/v2) | Compatible with React-Native CLI bootstrapped projects and Expo SDK 40 or earlier. |
| [1.x](https://github.com/IjzerenHein/react-native-bundle-visualizer/tree/v1) | Uses the [Haul bundler](https://github.com/callstack/haul) instead instead of the Metro output. |


## License

[MIT](./LICENSE.txt)
