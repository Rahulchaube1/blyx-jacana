## Compare a crude rate with a standardized rate

Returns [crude rate, standardized rate, standardized minus crude, total observations]. Each reported stratum needs observations for the crude comparison. Causal interpretation depends on study design. Invalid arguments and nonfinite results return an empty vector.

1. Open an empty file named `jacana-demo.blyx`.
2. Type `blyx-jacana-demo` and select **Jacana — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
0.75
0.5
-0.25
8
```

[Work through the example in the browser](https://www.blyx-lang.space/play?example=package-jacana)
