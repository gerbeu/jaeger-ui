[![Build Status][ci-img]][ci] [![Coverage Status][cov-img]][cov] [![FOSSA Status][fossa-img]][fossa]

# Jaeger UI - TraceAsBPMNChoreographyDiagram Extension

This extension to the JaegerUI adds the ability to visualize the trace of an event-driven, choreographically controlled microservices application as a BPMN choreography diagram. To convert the trace into a BPMN choreography diagram XML, the [backend application](https://github.com/gerbeu/EventsTraceToBPMNChorConverter/tree/a87c694da3bc5dcb17f1ea92268565704146026f) is used. To model the generated XML, the NavigatedViewer of the library [chor-js](https://github.com/bptlab/chor-js) is used.

## Requirements
In order to be able to analyze the trace, the following [backend application](https://github.com/gerbeu/EventsTraceToBPMNChorConverter/tree/a87c694da3bc5dcb17f1ea92268565704146026f) must be running: 

## Use Cases

![JaegerUIErweiterung](https://user-images.githubusercontent.com/74001567/221686903-3ea123dd-c299-49f0-9ffd-260f764ef10f.svg)

## Screenshots
The following screenshots show examples of the output generated for the instrumented [IBM microservices application](https://ibm-cloud-architecture.github.io/eda-saga-choreography/#implementation-explanation), which can be accessed [here](https://github.com/gerbeu/bachelor-thesis-resources).

![jaeger-ui-topics-tabelle](https://user-images.githubusercontent.com/74001567/221687133-c0cbf1ea-9e41-41f1-8423-71e3526efbb3.png)

![jaeger-ui-bpmn-chor](https://user-images.githubusercontent.com/74001567/221687124-f965fcd8-4dd9-4834-a3e8-8de5f9c8a88f.png)


Visualize distributed tracing with Jaeger.

|              Trace Search              |             Trace Details              |
| :------------------------------------: | :------------------------------------: |
| ![Trace Search](./media/ss_search.png) | ![Trace Details](./media/ss_trace.png) |

## Contributing

See [CONTRIBUTING](./CONTRIBUTING.md).

## Development

The app was built with [create-react-app](https://github.com/facebookincubator/create-react-app).

### Running the application

Fork, then clone the `jaeger-ui` repo and change directory into it.

```
git clone https://github.com/jaegertracing/jaeger-ui.git
cd jaeger-ui
```

Use the recommended Node versions: (defined in [.nvmrc](./.nvmrc) file):

```
nvm use
```

Install dependencies via `yarn`:

```
yarn install
# or
yarn
```

Make sure you have the Jaeger Query service running on http://localhost:16686. For example, you can run Jaeger all-in-one Docker image as described in the [documentation][aio-docs].

If you don't have it running locally, then tunnel to the correct host and port.

```
ssh -fN -L 16686:$BACKEND_HOST:$BACKEND_PORT $BACKEND_HOST
```

If you are using [UI Base Path](https://www.jaegertracing.io/docs/1.7/deployment/#ui-base-path) feature, you need to append the base path into `proxy->/api->target` in package.json file. for example: if the base path is `"/jaeger"`, then the target should be `"http://localhost:16686/jaeger"`

Start the development server with hot loading:

```
yarn start
```

The above command will run a web server on port :3000 that will serve the UI assets, with hot reloading support, and it will proxy all API requests to `http://localhost:16686` where Jaeger query should be running.

#### Commands

| Command      | Description                                                         |
| ------------ | ------------------------------------------------------------------- |
| `yarn start` | Starts development server with hot reloading and api proxy.         |
| `yarn test`  | Run all the tests                                                   |
| `yarn lint`  | Lint the project (eslint, prettier, typescript)                     |
| `yarn build` | Runs production build. Outputs files to `packages/jaeger-ui/build`. |

## Build

Running build will output all the static files to the `packages/jaeger-ui/build` folder:

```
yarn install
yarn build
```

## UI Configuration

See the [configuration guide](https://www.jaegertracing.io/docs/latest/frontend-ui/) for details on configuring Google Analytics tracking, menu customizations, and other aspects of UI behavior.

## License

[Apache 2.0 License](./LICENSE).

[ci-img]: https://github.com/jaegertracing/jaeger-ui/workflows/Unit%20Tests/badge.svg?branch=main
[ci]: https://github.com/jaegertracing/jaeger-ui/actions
[cov-img]: https://codecov.io/gh/jaegertracing/jaeger-ui/branch/main/graph/badge.svg
[cov]: https://codecov.io/gh/jaegertracing/jaeger-ui
[aio-docs]: https://www.jaegertracing.io/docs/latest/getting-started/
[fossa-img]: https://app.fossa.io/api/projects/git%2Bgithub.com%2Fjaegertracing%2Fjaeger-ui.svg?type=shield
[fossa]: https://app.fossa.io/projects/git%2Bgithub.com%2Fjaegertracing%2Fjaeger-ui?ref=badge_shield
