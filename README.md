# Introduction

The `perf_to_profile` binary can be used to turn a perf.data file, which is
generated by the linux profiler, perf, into a profile.proto file which can be
visualized using the tool pprof. 

For details on pprof, see https://github.com/google/pprof

**THIS IS NOT AN OFFICIAL GOOGLE PRODUCT**


# Prerequisites:
- Protocol buffers: http://github.com/google/protobuf
- Google Test: http://github.com/google/googletest

# Compilation
```
make perf_to_profile
```

# Usage:
Profile a command using perf, for example:
```
perf record /bin/ls
```

The example command will generate a profile named perf.data, you
should convert this into a profile.proto then visualize it using
pprof:

```
perf_to_profile perf.data profile.pb
pprof -web profile.pb
```

Recent versions of pprof will automatically invoke `perf_to_profile`:
```
pprof -web perf.data
```
