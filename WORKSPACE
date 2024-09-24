# The workspace name appears at the top of the runfiles tree,
# and in paths to tests, so to keep python happy it is best
# if it is unique.
workspace(name = "com_google_deepvariant")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

# Note: absl_py and com_google_absl (the Python and C++ abseil libraries) are
# provided by TensorFlow.

# CCTZ (Time-zone framework).
# TODO: transitive WORKSPACE dependency resolution doesn't
# work in bazel, so we need to include this to enable nucleus's use of
# //absl/{time,synchronization}
http_archive(
    name = "com_googlesource_code_cctz",
    strip_prefix = "cctz-master",
    urls = ["https://github.com/google/cctz/archive/master.zip"],
)

# This is the 1.18 release of htslib.
http_archive(
    name = "htslib",
    build_file = "//:third_party/htslib.BUILD",
    sha256 = "f1ab53a593a2320a1bfadf4ef915dae784006c5b5c922c8a8174d7530a9af18f",
    strip_prefix = "htslib-1.18",
    urls = [
        "https://github.com/samtools/htslib/releases/download/1.18/htslib-1.18.tar.bz2",
    ],
)

http_archive(
    name = "libssw",
    build_file = "//:third_party/libssw.BUILD",
    sha256 = "b294c0cb6f0f3d578db11b4112a88b20583b9d4190b0a9cf04d83bb6a8704d9a",
    # Note: HHBlits requires a patch (internal) in ssw_align to work.
    strip_prefix = "Complete-Striped-Smith-Waterman-Library-1.2.5",
    urls = [
        "https://github.com/mengyao/Complete-Striped-Smith-Waterman-Library/archive/v1.2.5.tar.gz",
    ],
)

http_archive(
    name = "gbwt",
    build_file = "//:third_party/gbwt.BUILD",
    sha256 = "eb90732969ba646702c7490e00859ec99bb9d5fa5e017bdfd5ddd13dc0c4ddc6",
    strip_prefix = "gbwt-420f0f494a4cc4b258335d29bf43c58d59cfcd2e",
    urls = [
        "https://github.com/mobinasri/gbwt/archive/420f0f494a4cc4b258335d29bf43c58d59cfcd2e.zip",
    ],
)

http_archive(
    name = "libhandlegraph",
    build_file = "//:third_party/libhandlegraph.BUILD",
    sha256 = "078dee9ab07996193117b54d75f6e4cfd881851da5e3c3e3d8c669c7eefeaaa2",
    strip_prefix = "libhandlegraph-b2fc22c552440076b340306fc660b4fa309fb005",
    urls = [
        "https://github.com/mobinasri/libhandlegraph/archive/b2fc22c552440076b340306fc660b4fa309fb005.zip",
    ],
)

http_archive(
    name = "sdsl_lite",
    build_file = "//:third_party/sdsl_lite.BUILD",
    sha256 = "4d240a073f81c3b5b8f3eaf0fa25af7d6609ca68afd1ca3f354d3a2d58dd73c0",
    strip_prefix = "sdsl_lite-d51299437e7a25a5f8349098716295b0b7ca34cc",
    urls = [
        "https://github.com/mobinasri/sdsl_lite/archive/d51299437e7a25a5f8349098716295b0b7ca34cc.zip",
    ],
)

http_archive(
    name = "gbwtgraph",
    build_file = "//:third_party/gbwtgraph.BUILD",
    sha256 = "74ce1e0958c094717bbcf9e0c8d820ccc13b20b2c7824f2cca0045c764554748",
    strip_prefix = "gbwtgraph-98661b0253a298838d645e71f65bdb9ddedfd408",
    urls = [
        "https://github.com/mobinasri/gbwtgraph/archive/98661b0253a298838d645e71f65bdb9ddedfd408.zip",
    ],
)

http_archive(
    name = "libdivsufsort",
    build_file = "//:third_party/libdivsufsort.BUILD",
    sha256 = "6a94e0ae99824b027a732062fab2ebd16091ada33ba1b90ba0e9892f2afec8b8",
    strip_prefix = "libdivsufsort-22e6b23e619ff50fd086844b6e618d53ca9d53bd",
    urls = [
        "https://github.com/simongog/libdivsufsort/archive/22e6b23e619ff50fd086844b6e618d53ca9d53bd.zip",
    ],
)

# Import tensorflow.  Note path.
local_repository(
    name = "org_tensorflow",
    path = "../tensorflow",
)

# Required boilerplate for tf_workspace().
# This is copied from https://github.com/tensorflow/tensorflow/blob/v2.3.0/WORKSPACE.
http_archive(
    name = "io_bazel_rules_closure",
    sha256 = "5b00383d08dd71f28503736db0500b6fb4dda47489ff5fc6bed42557c07c6ba9",
    strip_prefix = "rules_closure-308b05b2419edb5c8ee0471b67a40403df940149",
    urls = [
        "https://storage.googleapis.com/mirror.tensorflow.org/github.com/bazelbuild/rules_closure/archive/308b05b2419edb5c8ee0471b67a40403df940149.tar.gz",
        "https://github.com/bazelbuild/rules_closure/archive/308b05b2419edb5c8ee0471b67a40403df940149.tar.gz",  # 2019-06-13
    ],
)

# This needs to be in sync with the version of protobuf used by TensorFlow,
# which is currently defined in @tensorflow/tensorflow/workspace.bzl.
# We supply our own BUILD file, though, so we can prevent ODR violations by
# putting all of Nucleus's C++ binary dependencies into a single library.
# That BUILD file must be kept in sync with the version of protobuf used.
http_archive(
    name = "com_google_protobuf",
    patch_args = ["-p1"],
    patches = ["//:third_party/protobuf.patch"],
    build_file = "//:third_party/protobuf.BUILD",
    sha256 = "cfcba2df10feec52a84208693937c17a4b5df7775e1635c1e3baffc487b24c9b",
    # This protobuf release is based on protobuf 3.9.2.
    strip_prefix = "protobuf-3.9.2",
    urls = [
        "https://storage.googleapis.com/mirror.tensorflow.org/github.com/protocolbuffers/protobuf/archive/v3.9.2.zip",
        "https://github.com/protocolbuffers/protobuf/archive/v3.9.2.zip",
    ],
)

http_archive(
    name = "com_google_glog",
    sha256 = "1ee310e5d0a19b9d584a855000434bb724aa744745d5b8ab1855c85bff8a8e21",
    strip_prefix = "glog-028d37889a1e80e8a07da1b8945ac706259e5fd8",
    urls = [
        "https://mirror.bazel.build/github.com/google/glog/archive/028d37889a1e80e8a07da1b8945ac706259e5fd8.tar.gz",
        "https://github.com/google/glog/archive/028d37889a1e80e8a07da1b8945ac706259e5fd8.tar.gz",
    ],
)


# bazel_skylib is now a required dependency of protobuf_archive.
http_archive(
    name = "bazel_skylib",
    sha256 = "74d544d96f4a5bb630d465ca8bbcfe231e3594e5aae57e1edbf17a6eb3ca2506",
    urls = [
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/1.3.0/bazel-skylib-1.3.0.tar.gz",
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.3.0/bazel-skylib-1.3.0.tar.gz",
    ],
)

http_archive(
    name = "pybind11_protobuf",
    sha256 = "21e0c32d81ece8039a3a8e6daafbd7f64cb0c2744492f3b00f11baa0e276d1a5",
    strip_prefix = "pybind11_protobuf-de94308491982c32ddfe305a5dfc3c38bc9ff2bc",
    urls = [
        "https://github.com/pichuan/pybind11_protobuf/archive/de94308491982c32ddfe305a5dfc3c38bc9ff2bc.zip",
    ],
)

# Import all of the tensorflow dependencies.
# Copied from tensorflow/WORKSPACE. Updated in v2.5.0:
load("@org_tensorflow//tensorflow:workspace3.bzl", "tf_workspace3")

tf_workspace3()

load("@org_tensorflow//tensorflow:workspace2.bzl", "tf_workspace2")

tf_workspace2()

load("@org_tensorflow//tensorflow:workspace1.bzl", "tf_workspace1")

tf_workspace1()

load("@org_tensorflow//tensorflow:workspace0.bzl", "tf_workspace0")

tf_workspace0()

new_local_repository(
    name = "clif",
    build_file = "third_party/clif.BUILD",
    path = "/usr/local",
)
