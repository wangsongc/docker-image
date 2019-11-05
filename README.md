# docker-image
Base images for oss-fuzzer,Solve the problem of not being able to access gcr.io.

## How to use oss-fuzz locally
```
1、下载oss-fuzz源码至本地
2、替换oss-fuzz/infra/helper.py中镜像源，将gcr.io/oss-fuzz-base替换为wangsongc
3、替换oss-fuzz/project/cjson/Dockerfile中的镜像源，将gcr.io/oss-fuzz-base替换为wangsongc
4、cd /oss-fuzz/project/<project name>
5、拉取基础镜像生成fuzz专用镜像
   python infra/helper.py build_image <projece name>
6、编译fuzz target
   python infra/helper.py build_fuzzers --sanitizer address <projece name>
7、检查构建环境
   python infra/helper.py check_build <projece name>
8、运行fuzz target
   python infra/helper.py run_fuzzer <projece name> <fuzz_target>
9、生成覆盖率报告
   python infra/helper.py build_fuzzers --sanitizer coverage <projece name>
   python infra/helper.py coverage <projece name> <fuzz_target>
```
