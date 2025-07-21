# 🌐 DNS Benchmarking Tool

This project is a DNS benchmarking tool designed to evaluate the latency performance of multiple DNS servers (IPv4 and IPv6) across a wide range of domains. It uses `dig` (or optionally `dnspython`) to repeatedly query domains and report average, minimum, and maximum resolution times.

---

## 📦 Requirements

Ensure the following Python packages are installed:

```bash
pip install pandas matplotlib tqdm numpy ipywidgets dnspython
```

All requirements are already satisfied in the Anaconda setup as shown in the logs.

---

## 🚀 Features

- Tests DNS resolution times for **100+ popular domains**
- Supports both **IPv4 and IPv6** DNS servers
- Shows metrics: **Average**, **Median**, **Min/Max**, **Standard Deviation**
- Interactive plots using `matplotlib`
- Export results to `dns_results.csv`
- Can optionally read DNS servers and domain lists from a `config.json` file

---

## 🔧 Setup

Ensure `dig` is installed and available in your system’s path.

> 🔹 On Windows, install BIND or WSL to use `dig`.

If you can't install `dig`, an alternate version using `dnspython` is also partially included (see bottom section of script).

---

## 📁 Configuration

You can optionally define your own config file:

```json
{
  "dns_servers": {
    "MyDNS IPv4": "123.45.67.89",
    "MyDNS IPv6": "2001:abcd::1"
  },
  "domains": ["example.com", "github.com", "openai.com"]
}
```

Save it as `config.json` and the script will use it automatically.

---

## 🧪 How to Run

```bash
python dns_benchmark.py
```

Or inside Jupyter:

```python
%matplotlib inline
!python dns_benchmark.py
```

---

## 📊 Output

- CSV file: `dns_results.csv`
- Bar chart: Average latency for each DNS server
- Optional per-domain visualization (commented out in script)
- Console printout of **Top 2 IPv4** and **Top 2 IPv6** performers

---

## 📈 Sample Visualizations

Bar charts showing the average response time of each DNS server:

- Overall average latency
- Per-domain latency breakdown (if enabled)

---

## 🛠️ Notes

- The tool retries failed DNS queries with exponential backoff.
- Uses multithreading for speed using `ThreadPoolExecutor`
- Adjust `TRIES`, `MAX_RETRIES`, and `TIMEOUT` at the top of the script if needed.

---

## 🧠 Future Improvements

- Full GUI using `ipywidgets`
- Interactive filtering/sorting
- GeoIP integration for regional testing

---

## 📝 License

This project is free to use and modify. Attribution is appreciated.
