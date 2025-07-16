# QuantAnalyst: High-Performance Quantitative Analysis Library in Rust

A robust and efficient library for performing complex quantitative analysis, built for speed and reliability.

QuantAnalyst is a comprehensive Rust library designed to empower developers and quants with the tools they need to perform advanced quantitative analysis. Focused on performance, accuracy, and flexibility, this library provides a foundation for building sophisticated trading strategies, risk management systems, and financial modeling applications. Leveraging Rust's memory safety and concurrency features, QuantAnalyst offers a superior alternative to traditional languages like Python or R for computationally intensive tasks.

The library aims to provide a modular architecture, allowing users to select and combine specific analytical components as needed. This design philosophy promotes code reusability and reduces unnecessary dependencies, leading to leaner and more maintainable applications. Whether you are developing high-frequency trading algorithms, conducting statistical arbitrage, or simply need a reliable tool for time series analysis, QuantAnalyst provides the building blocks to succeed. Its focus on correctness and numerical stability ensures that your analyses are accurate and trustworthy.

QuantAnalyst is actively developed with a roadmap that includes expanding its feature set to encompass a wider range of financial instruments and analytical techniques. Future releases will incorporate more advanced machine learning algorithms tailored for financial data, further enhancing its capabilities. The project welcomes contributions from the community to accelerate its growth and solidify its position as a leading open-source quantitative analysis library in Rust. Our goal is to create a versatile and powerful tool that caters to both academic researchers and industry professionals.

**Key Features:**

*   **Time Series Analysis:** Implements a variety of time series analysis techniques, including moving averages (SMA, EMA, WMA), differencing, and autocorrelation functions. These algorithms are optimized for performance using SIMD instructions where applicable. Example: `let ema = ExponentialMovingAverage::new(data, 12)?;`
*   **Statistical Analysis:** Provides statistical functions such as mean, standard deviation, variance, skewness, kurtosis, and correlation. These functions are implemented using numerically stable algorithms to minimize rounding errors. Example: `let mean = calculate_mean(data);`
*   **Regression Analysis:** Includes linear regression and polynomial regression models, with support for multiple independent variables. Uses QR decomposition for numerical stability in solving linear systems. Example: `let model = LinearRegression::new(independent_vars, dependent_var)?;`
*   **Volatility Modeling:** Offers various volatility models, including simple historical volatility and exponentially weighted moving average volatility (EWMA). These models are crucial for risk management and option pricing. Example: `let ewma_vol = EWMAVolatility::new(data, 20)?;`
*   **Technical Indicators:** Implements a range of popular technical indicators, such as Relative Strength Index (RSI), Moving Average Convergence Divergence (MACD), and Bollinger Bands. These indicators are essential tools for technical analysis and trading strategy development. Example: `let rsi = RSI::new(data, 14)?;`
*   **Data Handling:** Provides efficient data structures for storing and manipulating financial time series data. This includes support for common data formats such as CSV and Parquet, enabling seamless integration with existing data pipelines. Example: `let data = load_csv_data("data.csv")?;`
*   **Backtesting Framework (Planned):** Future releases will include a backtesting framework for evaluating trading strategies using historical data. This framework will support various performance metrics and risk management techniques.

**Technology Stack:**

*   **Rust:** The primary programming language, providing memory safety, concurrency, and performance.
*   **ndarray:** Used for efficient numerical computation and array manipulation.
*   **csv:** Used for reading and writing CSV files.
*   **serde:** Used for serialization and deserialization of data.
*   **criterion:** Used for benchmarking performance.
*   **thiserror:** Used for custom error handling.

**Installation:**

1.  Ensure you have Rust installed. You can install it from [https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install).
2.  Clone the repository: `git clone https://github.com/jjfhwang/QuantAnalyst.git`
3.  Navigate to the project directory: `cd QuantAnalyst`
4.  Build the project: `cargo build`
5.  Run the tests: `cargo test`

**Configuration:**

The library does not currently require any external configuration files. However, certain modules might require environment variables for specific functionalities in the future (e.g., API keys for data providers). These will be documented in the relevant module documentation.

**Usage:**

Here's a simple example of calculating the simple moving average of a time series:



(Note: Compile the above code by making sure the `quantanalyst` crate is properly configured as a dependency in your `Cargo.toml` file).

For more detailed usage examples and API documentation, please refer to the library's source code and generated documentation (run `cargo doc --open`). The `src/` directory contains well-documented modules with examples of how to use the various functions and data structures.

**Contributing:**

We welcome contributions from the community! To contribute:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Implement your changes, ensuring that all tests pass (`cargo test`).
4.  Write clear and concise commit messages.
5.  Submit a pull request with a detailed description of your changes.

Please adhere to the project's coding style and conventions. All contributions must be licensed under the same license as the project.

**License:**

This project is licensed under the MIT License. See the [LICENSE](https://github.com/jjfhwang/QuantAnalyst/blob/main/LICENSE) file for details.

**Acknowledgements:**

We would like to thank the Rust community for providing such a powerful and supportive ecosystem. We are also grateful to the contributors to the libraries used in this project, such as ndarray, csv, and serde.