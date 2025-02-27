load(
    "//bazel:envoy_build_system.bzl",
    "envoy_package",
    "envoy_select_admin_functionality",
)
load(
    "//test/extensions:extensions_build_system.bzl",
    "envoy_extension_cc_test",
)

licenses(["notice"])  # Apache 2

envoy_package()

envoy_extension_cc_test(
    name = "config_test",
    srcs = ["config_test.cc"],
    extension_names = ["envoy.stat_sinks.hystrix"],
    rbe_pool = "6gig",
    deps = [
        "//envoy/registry",
        "//source/common/protobuf:utility_lib",
        "//source/extensions/stat_sinks/hystrix:config",
        "//test/mocks/server:instance_mocks",
        "//test/test_common:environment_lib",
        "//test/test_common:network_utility_lib",
        "//test/test_common:utility_lib",
        "@envoy_api//envoy/config/metrics/v3:pkg_cc_proto",
    ],
)

envoy_extension_cc_test(
    name = "hystrix_test",
    srcs = ["hystrix_test.cc"],
    extension_names = ["envoy.stat_sinks.hystrix"],
    rbe_pool = "6gig",
    deps = [
        "//source/common/json:json_loader_lib",
        "//source/common/stats:stats_lib",
        "//source/extensions/stat_sinks/hystrix:hystrix_lib",
        "//test/mocks/server:admin_mocks",
        "//test/mocks/server:admin_stream_mocks",
        "//test/mocks/server:instance_mocks",
        "//test/mocks/stats:stats_mocks",
        "//test/mocks/upstream:cluster_info_mocks",
        "//test/mocks/upstream:cluster_manager_mocks",
        "//test/mocks/upstream:priority_set_mocks",
    ],
)

envoy_extension_cc_test(
    name = "hystrix_integration_test",
    size = "large",
    srcs = envoy_select_admin_functionality(["hystrix_integration_test.cc"]),
    extension_names = ["envoy.stat_sinks.hystrix"],
    rbe_pool = "6gig",
    deps = [
        "//source/extensions/stat_sinks/hystrix:config",
        "//test/integration:http_protocol_integration_lib",
    ],
)
