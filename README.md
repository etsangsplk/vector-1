<p align="center">
  <strong>
    <a href="https://vector.dev/docs/">Docs<a/>&nbsp;&nbsp;&bull;&nbsp;&nbsp;<a href="https://vector.dev/community">Chat<a/>&nbsp;&nbsp;&bull;&nbsp;&nbsp;<a href="https://twitter.com/vectordotdev">@vectordotdev<a/>&nbsp;&nbsp;&bull;&nbsp;&nbsp;<a href="https://vector.dev/releases/latest/download">Download v0.7.2<a/>
  </strong>
</p>

---

<p align="center">
  <img src="./website/static/img/readme_diagram.svg" alt="Vector">
</p>


Vector is a _highly reliable_ observability data router built for demanding
production environments. Vector is designed on the following principles:

* **High reliability** - Built in [Rust][urls.rust], Vector is [memory safe][urls.rust_memory_safety], [correct][pages.index#correctness], and [performant][pages.index#performance].
* **Operator safety** - Vector is pragmatic and hard to break. It [avoids the common pitfalls](#the-little-details-make-all-of-the-difference) in similar tools.
* **All data** - [Logs][docs.data-model.log], [metrics][docs.data-model.metric], and traces (coming soon). A [sophisticated data model][docs.data-model] enables _correct_ interoperability.
* **One tool** - Deploys as an [agent][docs.roles.agent] or [service][docs.roles.service]. One tool gets your data from A to B.

Vector is **deployed over 100,000 times per day**, and is trusted by Fortune 500
companies and engineering teams trying to tame observability pipelines.


<!--
     THIS FILE IS AUTOGENERATED!

     To make changes please edit the template located at:

     README.md.erb
-->

## [Documentation](https://vector.dev/docs/)

#### About

* [**Concepts**][docs.concepts]
* [**Data model (Event)**][docs.data_model] - [log event][docs.data-model.log], [metric event][docs.data-model.metric]
* [**Guarantees**][docs.guarantees]

#### Setup

* [**Installation**][docs.installation] - [containers][docs.containers], [operating systems][docs.operating_systems], [package managers][docs.package_managers], [from archives][docs.from-archives], [from source][docs.from-source]
* [**Configuration**][docs.configuration]
* [**Deployment**][docs.deployment] - [topologies][docs.topologies], [roles][docs.roles]
* [**Guides**][docs.guides] - [getting started][docs.guides.getting_started], [unit testing][docs.guides.unit-testing]

#### Reference

* [**Sources**][docs.sources] - [docker][docs.sources.docker], [file][docs.sources.file], [journald][docs.sources.journald], [kafka][docs.sources.kafka], [socket][docs.sources.socket], [syslog][docs.sources.syslog], and [6 more...][docs.sources]
<<<<<<< HEAD
* [**Transforms**][docs.transforms] - [json_parser][docs.transforms.json_parser], [log_to_metric][docs.transforms.log_to_metric], [logfmt_parser][docs.transforms.logfmt_parser], [lua][docs.transforms.lua], [regex_parser][docs.transforms.regex_parser], [sampler][docs.transforms.sampler], and [14 more...][docs.transforms]
* [**Sinks**][docs.sinks] - [aws_cloudwatch_logs][docs.sinks.aws_cloudwatch_logs], [aws_s3][docs.sinks.aws_s3], [clickhouse][docs.sinks.clickhouse], [elasticsearch][docs.sinks.elasticsearch], [gcp_cloud_storage][docs.sinks.gcp_cloud_storage], [gcp_pubsub][docs.sinks.gcp_pubsub], and [21 more...][docs.sinks]
=======
* [**Transforms**][docs.transforms] - [json_parser][docs.transforms.json_parser], [log_to_metric][docs.transforms.log_to_metric], [logfmt_parser][docs.transforms.logfmt_parser], [lua][docs.transforms.lua], [regex_parser][docs.transforms.regex_parser], [sampler][docs.transforms.sampler], and [15 more...][docs.transforms]
* [**Sinks**][docs.sinks] - [aws_cloudwatch_logs][docs.sinks.aws_cloudwatch_logs], [aws_s3][docs.sinks.aws_s3], [clickhouse][docs.sinks.clickhouse], [elasticsearch][docs.sinks.elasticsearch], [gcp_pubsub][docs.sinks.gcp_pubsub], [gcp_stackdriver_logging][docs.sinks.gcp_stackdriver_logging], and [19 more...][docs.sinks]
>>>>>>> Add docs for swimlanes

#### Administration

* [**Process management**][docs.process-management]
* [**Monitoring**][docs.monitoring]
* [**Updating**][docs.updating]
* [**Validating**][docs.validating]

#### Resources

* [**Community**][urls.vector_community] - [chat][urls.vector_chat], [@vectordotdev][urls.vector_twitter], [mailing list][urls.mailing_list]
* [**Releases**][urls.vector_releases] - [v0.7.2 (latest)][urls.v0.7.2]
* [**Roadmap**][urls.vector_roadmap] - [vote on new features][urls.vote_feature]


## Performance

| Test | Vector | Filebeat | FluentBit | FluentD | Logstash | SplunkUF | SplunkHF |
| ---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| [TCP to Blackhole](https://github.com/timberio/vector-test-harness/tree/master/cases/tcp_to_blackhole_performance) | _**86mib/s**_ | n/a | 64.4mib/s | 27.7mib/s | 40.6mib/s | n/a | n/a |
| [File to TCP](https://github.com/timberio/vector-test-harness/tree/master/cases/file_to_tcp_performance) | _**76.7mib/s**_ | 7.8mib/s | 35mib/s | 26.1mib/s | 3.1mib/s | 40.1mib/s | 39mib/s |
| [Regex Parsing](https://github.com/timberio/vector-test-harness/tree/master/cases/regex_parsing_performance) | 13.2mib/s | n/a | _**20.5mib/s**_ | 2.6mib/s | 4.6mib/s | n/a | 7.8mib/s |
| [TCP to HTTP](https://github.com/timberio/vector-test-harness/tree/master/cases/tcp_to_http_performance) | _**26.7mib/s**_ | n/a | 19.6mib/s | <1mib/s | 2.7mib/s | n/a | n/a |
| [TCP to TCP](https://github.com/timberio/vector-test-harness/tree/master/cases/tcp_to_tcp_performance) | 69.9mib/s | 5mib/s | 67.1mib/s | 3.9mib/s | 10mib/s | _**70.4mib/s**_ | 7.6mib/s |

To learn more about our performance tests, please see the [Vector test harness][urls.vector_test_harness].


## Correctness

The following correctness tests are not exhaustive, but they demonstrate
fundamental differences in quality and design:

| Test | Vector | Filebeat | FluentBit | FluentD | Logstash | Splunk UF | Splunk HF |
| ---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| [Disk Buffer Persistence](https://github.com/timberio/vector-test-harness/tree/master/cases/disk_buffer_persistence_correctness) | ✅ | ✅ | ❌ | ❌ | ⚠️ | ✅ | ✅ |
| [File Rotate (create)](https://github.com/timberio/vector-test-harness/tree/master/cases/file_rotate_create_correctness) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| [File Rotate (copytruncate)](https://github.com/timberio/vector-test-harness/tree/master/cases/file_rotate_truncate_correctness) | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ |
| [File Truncation](https://github.com/timberio/vector-test-harness/tree/master/cases/file_truncate_correctness) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| [Process (SIGHUP)](https://github.com/timberio/vector-test-harness/tree/master/cases/sighup_correctness) | ✅ | ❌ | ❌ | ❌ | ⚠️ | ✅ | ✅ |
| [JSON (wrapped)](https://github.com/timberio/vector-test-harness/tree/master/cases/wrapped_json_correctness) | ✅ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ |

To learn more about our correctness tests, please see the [Vector test harness][urls.vector_test_harness].


## The Little Details Make All Of The Difference

* **Zero delay start** - Starts and restarts without a delay.
* **Hot reload** - [Reload configuration on the fly][docs.process-management#reloading] without disrupting data flow.
* **Configurable concurrency** - All CPU cores (service) or just one (agent) via the [`--threads` flag][docs.process-management#starting].
* **Programmable transforms** - [Lua][docs.transforms.lua], [Javascript (coming soon)][urls.pr_721], and [WASM (coming soon)][urls.issue_1802].
* **Templating** - [Use event fields to create dynamic values][docs.reference.templating], enabling dynamic partitioning and more.
* **Sink healthchecks** - Protection against downstream disruptions make Vector a good citizen.
* **Customizable schema** - A schema is not forced on you. [Change Vector's schema][docs.global-options#log_schema] to anything you like.
* **Decoupled buffer design** - Buffers are coupled with sinks; a bad sink won't bring the entire pipeline to a halt.
* **Thoughtful disk buffering** - Transfers data to operating system memory to reduce the risk of data loss.
* **Merge split logs** - Easily merge multi-line logs into one event.
* **Custom DNS** - [Custom DNS][docs.global-options#dns_servers] makes service discovery possible.
* **Rate-limited logging** - Vector's internal logging is rate-limited and noise-free.
* **Optionally fully static binary** - Optional MUSL static binaries mean zero required dependencies.
* **Thoughtful docs** - [Quality documentation][docs.what-is-vector] that respects your time and reduces communication overhead.
* **Clear Guarantees** - A [guarantee support matrix][docs.guarantees] helps you make the appropriate tradeoffs.
* **Config unit tests** - [Develop Vector config files like code][docs.guides.unit-testing]. Avoid the frustrating dev style required by other tools.
* **Config linting** - [Quickly lint][docs.administration.validating] Vector config files to spot errors and prevent bad configs in CI.


## Installation

Run the following in your terminal, then follow the on-screen instructions.

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.vector.dev | sh
```

Or use your own [preferred method][docs.installation].


## Latest Posts & Announcements

* [Prometheus Source](https://vector.dev/blog/prometheus-source)
* [EC2 Metadata Enrichments](https://vector.dev/blog/ec2-metadata)
* [Alpha Kubernetes Source](https://vector.dev/blog/kubernetes-source-alpha)
* [Use Custom DNS Servers](https://vector.dev/blog/custom-dns)
* [Unit Testing Your Vector Config Files](https://vector.dev/blog/unit-testing-vector-config-files)

[view all...][urls.vector_blog]

---

<p align="center">
  Developed with ❤️ by <strong><a href="https://timber.io">Timber.io</a></strong>
</p>


[docs.administration.validating]: https://vector.dev/docs/administration/validating/
[docs.concepts]: https://vector.dev/docs/about/concepts/
[docs.configuration]: https://vector.dev/docs/setup/configuration/
[docs.containers]: https://vector.dev/docs/setup/installation/containers/
[docs.data-model.log]: https://vector.dev/docs/about/data-model/log/
[docs.data-model.metric]: https://vector.dev/docs/about/data-model/metric/
[docs.data-model]: https://vector.dev/docs/about/data-model/
[docs.data_model]: https://vector.dev/docs/about/data-model/
[docs.deployment]: https://vector.dev/docs/setup/deployment/
[docs.from-archives]: https://vector.dev/docs/setup/installation/manual/from-archives/
[docs.from-source]: https://vector.dev/docs/setup/installation/manual/from-source/
[docs.global-options#dns_servers]: https://vector.dev/docs/reference/global-options/#dns_servers
[docs.global-options#log_schema]: https://vector.dev/docs/reference/global-options/#log_schema
[docs.guarantees]: https://vector.dev/docs/about/guarantees/
[docs.guides.getting_started]: https://vector.dev/docs/setup/guides/getting-started/
[docs.guides.unit-testing]: https://vector.dev/docs/setup/guides/unit-testing/
[docs.guides]: https://vector.dev/docs/setup/guides/
[docs.installation]: https://vector.dev/docs/setup/installation/
[docs.monitoring]: https://vector.dev/docs/administration/monitoring/
[docs.operating_systems]: https://vector.dev/docs/setup/installation/operating-systems/
[docs.package_managers]: https://vector.dev/docs/setup/installation/package-managers/
[docs.process-management#reloading]: https://vector.dev/docs/administration/process-management/#reloading
[docs.process-management#starting]: https://vector.dev/docs/administration/process-management/#starting
[docs.process-management]: https://vector.dev/docs/administration/process-management/
[docs.reference.templating]: https://vector.dev/docs/reference/templating/
[docs.roles.agent]: https://vector.dev/docs/setup/deployment/roles/agent/
[docs.roles.service]: https://vector.dev/docs/setup/deployment/roles/service/
[docs.roles]: https://vector.dev/docs/setup/deployment/roles/
[docs.sinks.aws_cloudwatch_logs]: https://vector.dev/docs/reference/sinks/aws_cloudwatch_logs/
[docs.sinks.aws_s3]: https://vector.dev/docs/reference/sinks/aws_s3/
[docs.sinks.clickhouse]: https://vector.dev/docs/reference/sinks/clickhouse/
[docs.sinks.elasticsearch]: https://vector.dev/docs/reference/sinks/elasticsearch/
[docs.sinks.gcp_cloud_storage]: https://vector.dev/docs/reference/sinks/gcp_cloud_storage/
[docs.sinks.gcp_pubsub]: https://vector.dev/docs/reference/sinks/gcp_pubsub/
[docs.sinks]: https://vector.dev/docs/reference/sinks/
[docs.sources.docker]: https://vector.dev/docs/reference/sources/docker/
[docs.sources.file]: https://vector.dev/docs/reference/sources/file/
[docs.sources.journald]: https://vector.dev/docs/reference/sources/journald/
[docs.sources.kafka]: https://vector.dev/docs/reference/sources/kafka/
[docs.sources.socket]: https://vector.dev/docs/reference/sources/socket/
[docs.sources.syslog]: https://vector.dev/docs/reference/sources/syslog/
[docs.sources]: https://vector.dev/docs/reference/sources/
[docs.topologies]: https://vector.dev/docs/setup/deployment/topologies/
[docs.transforms.json_parser]: https://vector.dev/docs/reference/transforms/json_parser/
[docs.transforms.log_to_metric]: https://vector.dev/docs/reference/transforms/log_to_metric/
[docs.transforms.logfmt_parser]: https://vector.dev/docs/reference/transforms/logfmt_parser/
[docs.transforms.lua]: https://vector.dev/docs/reference/transforms/lua/
[docs.transforms.regex_parser]: https://vector.dev/docs/reference/transforms/regex_parser/
[docs.transforms.sampler]: https://vector.dev/docs/reference/transforms/sampler/
[docs.transforms]: https://vector.dev/docs/reference/transforms/
[docs.updating]: https://vector.dev/docs/administration/updating/
[docs.validating]: https://vector.dev/docs/administration/validating/
[docs.what-is-vector]: https://vector.dev/docs/about/what-is-vector/
[pages.index#correctness]: https://vector.dev/#correctness
[pages.index#performance]: https://vector.dev/#performance
[urls.issue_1802]: https://github.com/timberio/vector/issues/1802
[urls.mailing_list]: https://vector.dev/community/
[urls.pr_721]: https://github.com/timberio/vector/pull/721
[urls.rust]: https://www.rust-lang.org/
[urls.rust_memory_safety]: https://hacks.mozilla.org/2019/01/fearless-security-memory-safety/
[urls.v0.7.2]: https://vector.dev/releases/0.7.2/download
[urls.vector_blog]: https://vector.dev/blog
[urls.vector_chat]: https://chat.vector.dev
[urls.vector_community]: https://vector.dev/community
[urls.vector_releases]: https://vector.dev/releases/latest
[urls.vector_roadmap]: https://github.com/timberio/vector/milestones?direction=asc&sort=due_date&state=open
[urls.vector_test_harness]: https://github.com/timberio/vector-test-harness/
[urls.vector_twitter]: https://twitter.com/vectordotdev
[urls.vote_feature]: https://github.com/timberio/vector/issues?q=is%3Aissue+is%3Aopen+sort%3Areactions-%2B1-desc+label%3A%22Type%3A+New+Feature%22
