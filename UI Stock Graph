import yfinance as yf
import pandas as pd
import matplotlib.pyplot as plt
import tkinter as tk

def analyze_stock():
    ticker_symbol = symbol_entry.get()
    start_date = start_entry.get()
    end_date = end_entry.get()
    
    # Fetch stock data
    stock_data = yf.download(ticker_symbol, start=start_date, end=end_date)

    # Calculate daily returns
    stock_data['Daily_Return'] = stock_data['Adj Close'].pct_change()

    # Calculate moving averages
    stock_data['MA_50'] = stock_data['Adj Close'].rolling(window=50).mean()
    stock_data['MA_200'] = stock_data['Adj Close'].rolling(window=200).mean()

    # Plotting
    plt.figure(figsize=(10, 6))
    plt.plot(stock_data['Adj Close'], label='Adjusted Close')
    plt.plot(stock_data['MA_50'], label='50-day Moving Average')
    plt.plot(stock_data['MA_200'], label='200-day Moving Average')
    plt.title(ticker_symbol + ' Stock Analysis')
    plt.xlabel('Date')
    plt.ylabel('Price')
    plt.legend()
    plt.show()

# Create GUI window
window = tk.Tk()
window.title("Stock Analysis")
window.geometry("400x200")

# Create input fields
symbol_label = tk.Label(window, text="Stock Symbol:")
symbol_label.pack()
symbol_entry = tk.Entry(window)
symbol_entry.pack()

start_label = tk.Label(window, text="Start Date (YYYY-MM-DD):")
start_label.pack()
start_entry = tk.Entry(window)
start_entry.pack()

end_label = tk.Label(window, text="End Date (YYYY-MM-DD):")
end_label.pack()
end_entry = tk.Entry(window)
end_entry.pack()

# Create analyze button
analyze_button = tk.Button(window, text="Analyze", command=analyze_stock)
analyze_button.pack()

# Run the GUI loop
window.mainloop()
