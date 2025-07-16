# QuantAnalyst: Algorithmic Forex Signal Generation

Generating profitable Forex trading signals using Kalman filter smoothing, wavelet anomaly detection, and rigorous tick data backtesting.

## Detailed Description

QuantAnalyst is a Rust-based algorithmic trading system designed to generate high-quality Forex trading signals. The core of the system lies in its sophisticated signal processing pipeline. First, raw tick data is ingested and pre-processed to remove noise and outliers. Then, a Kalman filter is applied to smooth the price data, providing a more stable and reliable trend estimate. This smoothed data is then subjected to wavelet transform-based anomaly detection. This approach allows for the identification of significant price deviations from the smoothed trend, potentially indicating profitable entry or exit points.

The novelty of QuantAnalyst lies in its combination of these signal processing techniques. While Kalman filters are commonly used for time series smoothing, and wavelet transforms are powerful for anomaly detection, their synergistic application in a Forex trading context, coupled with thorough backtesting, is where the project derives its strength. The wavelet transform specifically uses a Daubechies wavelet, chosen for its compact support and ability to effectively decompose the signal into different frequency components. The anomaly detection algorithm is configured to detect statistically significant deviations from the reconstructed signal, using a threshold based on the standard deviation of the wavelet coefficients.

Finally, all generated signals are rigorously backtested using historical tick data. The backtesting framework incorporates realistic trading constraints, such as transaction costs (spreads and commissions) and slippage, to provide an accurate assessment of the system's profitability. The backtesting results are used to optimize the system's parameters, such as the Kalman filter parameters, wavelet parameters, and signal thresholds. This iterative optimization process ensures that the system is adapted to the specific characteristics of the Forex market and the particular currency pairs being traded. This iterative procedure leverages a genetic algorithm to efficiently explore the parameter space and identify optimal configurations.

## Key Features

*   **Kalman Filter Smoothing:** Implements a Kalman filter using the `nalgebra` crate for linear algebra, providing robust noise reduction and trend estimation of Forex price data. The filter's transition and observation matrices are configurable, allowing for fine-tuning to different currency pairs and market conditions.

*   **Wavelet Anomaly Detection:** Utilizes a Daubechies wavelet transform implemented using a custom Rust library optimized for performance. Identifies statistically significant deviations from the smoothed trend based on wavelet coefficients. The threshold for anomaly detection is dynamically adjusted based on the historical volatility of the currency pair.

*   **Tick Data Backtesting:** A comprehensive backtesting engine that simulates trades using historical tick data. Incorporates realistic trading constraints, including spreads, commissions, and slippage. The backtesting engine uses a vectorized implementation for fast and efficient evaluation of different trading strategies.

*   **Parameter Optimization:** Employs a genetic algorithm implemented with the `ga` crate to optimize the Kalman filter parameters, wavelet parameters, and signal thresholds. This ensures the system adapts to changing market conditions and maximizes profitability.

*   **Real-time Signal Generation:** Designed for integration with real-time market data feeds for live trading. The system can be easily deployed to a cloud server or a local machine for automated trading.

*   **Modular Architecture:** The codebase is structured into modular components, making it easy to extend and customize. New signal processing techniques or trading strategies can be easily integrated into the system.

*   **Detailed Reporting:** Generates comprehensive reports detailing the backtesting results, including key performance metrics such as profit factor, Sharpe ratio, and maximum drawdown. These reports are used to evaluate the performance of the system and identify areas for improvement.

## Technology Stack

*   **Rust:** The primary programming language, chosen for its performance, safety, and concurrency capabilities. Rust ensures efficient execution of the signal processing algorithms and robust handling of real-time data.
*   **Nalgebra:** A linear algebra library for Rust, used for matrix operations in the Kalman filter implementation. Nalgebra provides efficient and reliable matrix calculations.
*   **GA (Genetic Algorithm):** A Rust library that allows for the implementation of genetic algorithms used to optimize the model parameters. The genetic algorithm is used to search for the optimal configuration of parameters that maximizes profitability.
*   **Tokio:** An asynchronous runtime for Rust, used for handling concurrent tasks, such as processing multiple data streams or executing backtests in parallel.
*   **Serde:** A serialization/deserialization framework for Rust, used for reading and writing data in various formats, such as CSV and JSON.
*   **Chronium:** A time handling library for Rust, used to ensure accurate calculation of date and time values when working with tick data.

## Installation

1.  Ensure you have Rust installed. You can download it from [https://www.rust-lang.org/](https://www.rust-lang.org/).
2.  Clone the repository:

   git clone https://github.com/jjfhwang/QuantAnalyst.git

3.  Navigate to the project directory:

   cd QuantAnalyst

4.  Build the project:

   cargo build --release

## Configuration

The system is configured using environment variables. The following variables are required:

*   `TICK_DATA_PATH`: The path to the historical tick data file. The file should be in CSV format with columns for timestamp, bid price, and ask price.
*   `SPREAD`: The spread to use for backtesting, in pips. For example, a spread of 2 pips would be set to 2.
*   `COMMISSION`: The commission to use for backtesting, in currency per lot.
*   `KALMAN_Q`: The process noise covariance for the Kalman filter.
*   `KALMAN_R`: The measurement noise covariance for the Kalman filter.
*   `WAVELET_LEVEL`: The decomposition level for the wavelet transform.
*   `ANOMALY_THRESHOLD`: The threshold for anomaly detection, in standard deviations.

You can set these environment variables in your `.env` file or directly in your shell. For example:

TICK_DATA_PATH=/path/to/tick_data.csv
SPREAD=2
COMMISSION=0.0
KALMAN_Q=0.0001
KALMAN_R=0.01
WAVELET_LEVEL=5
ANOMALY_THRESHOLD=3.0

## Usage

1.  Run the system:

   cargo run --release

This will load the tick data, generate trading signals, and backtest the system. The backtesting results will be printed to the console. You can modify the trading logic or parameters in the respective modules to adjust the trading behavior of the system.

2.  To view the detailed reports you can invoke the reporting module separately, however, you will need to run the core system beforehand to generate the data. The reporting module expects to find data in a subfolder of the project called "reports".

   cargo run --release --features reporting

## Contributing

We welcome contributions to QuantAnalyst! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write tests for your code.
4.  Ensure all tests pass.
5.  Submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/jjfhwang/QuantAnalyst/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the Rust community for providing excellent libraries and resources that made this project possible. Also, thanks to the developers of the Nalgebra, GA, Tokio, Serde, and Chronium crates that this project depends on.