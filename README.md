<img src="assets/logo.png" width="112" height="112" alt="A chestnut jacana with a red forehead spreads its toes over a lily pad.">

# Jacana

Compare a crude event rate with a directly standardized rate. This Blyx workflow framework is part of the probability and causal analysis collection.

A change in the mix of observed groups can move the pooled rate. Recalculate rates against fixed reference weights before comparing populations. [NCI SEER, direct age adjustment](https://seer.cancer.gov/seerstat/tutorials/aarates/definition.html)

## Editor extension

Install **RahulChaube.blyx-jacana** to run the worked example and use the framework’s function completions in a Blyx file. Open an empty `.blyx` file, enter `blyx-jacana-demo`, then choose **Blyx: Run File**. [Editor downloads](https://www.blyx-lang.space/packages/jacana#editor) · [Download the extension](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-jacana-0.1.0.vsix) · [Starter with framework source](https://github.com/Rahulchaube1/blyxxxx/releases/download/framework-editors-v0.1.0/blyx-jacana-starter-0.1.0.zip)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.1 https://github.com/Rahulchaube1/blyx-jacana.git
cd blyx-jacana
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-jacana) · [Package page](https://www.blyx-lang.space/packages/jacana) · [Handbook](https://doc.blyx-lang.space/guide/jacana)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.1 https://github.com/Rahulchaube1/blyx-jacana.git vendor/jacana
```

```blyx
use vendor::jacana::jacana;

fn main() {
    let events = [0, 6];
    let trials = [2, 6];
    let weights = [1, 1];
    let result = jacana_standardize(events, trials, weights);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
0.75
0.5
-0.25
8
```

## API

`jacana_standardize(events, trials, weights)`

Returns [crude rate, standardized rate, standardized minus crude, total observations]. Each reported stratum needs observations for the crude comparison. Causal interpretation depends on study design. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| events | Vector of values, each a nonnegative exact integer |
| trials | Vector of values, each a nonnegative exact integer |
| weights | Vector of values, each a nonnegative finite number |

## Run the command-line project

Run the example with your own numbers. Vector arguments accept up to 16 comma-separated entries; use `[]` for an empty vector. The imported API accepts longer vectors. Invalid arguments return a nonzero exit status.

```sh
blyxc native-run project.blyx -- "0,6" "2,6" "1,1"
```

## Libraries

- [StrataMean](https://github.com/Rahulchaube1/blyx-stratamean/tree/v0.1.1) — Pool event counts and expose the crude observed rate.
- [StdWeight](https://github.com/Rahulchaube1/blyx-stdweight/tree/v0.1.1) — Directly standardize stratum-specific rates to a reference population.

This release includes identical copies of both library modules so a tagged clone can build offline.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-jacana/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The [artwork notice](assets/NOTICE.txt) records credits for earlier editions.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
