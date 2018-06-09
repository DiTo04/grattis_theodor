git_repository(
    name = "io_bazel_rules_docker",
    commit = "27c94dec66c3c9fdb478c33994471c5bfc15b6eb",
    remote = "https://github.com/bazelbuild/rules_docker.git",
)

git_repository(
    name = "io_bazel_rules_k8s",
    commit = "8c9b9cbc6a46a4c8db4a1da8565252b326d90331",
    remote = "https://github.com/bazelbuild/rules_k8s.git",
)

load(
    "@io_bazel_rules_docker//docker:docker.bzl",
    "docker_repositories",
)

docker_repositories()

load("@io_bazel_rules_k8s//k8s:k8s.bzl", "k8s_repositories", "k8s_defaults")

k8s_repositories()

k8s_defaults(
    # This becomes the name of the @repository and the rule
    # you will import in your BUILD files.
    name = "k8s_production_deploy",
    namespace = "spexflix-production",
    cluster = "gke_spexflix_europe-west1-b_develop",
)

load("@io_bazel_rules_docker//container:container.bzl", "container_pull")

container_pull(
    name = "static_nginx_server",
    registry = "registry.hub.docker.com",
    repository = "kyma/docker-nginx",
    digest = "sha256:c7e9c0c5d6b3c9112f644006484926aaadc84d99d960d39894cb2f79c399b026",
)
