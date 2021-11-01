# hello_world
仅仅是练习使用
T-DT
Horizon


from scipy.fftpack import fft, fftfreq
 
fft_series = fft(data["value"].values)
power = np.abs(fft_series)
sample_freq = fftfreq(fft_series.size)
 
pos_mask = np.where(sample_freq > 0)
freqs = sample_freq[pos_mask]
powers = power[pos_mask]
 
top_k_seasons = 3
# top K=3 index
top_k_idxs = np.argpartition(powers, -top_k_seasons)[-top_k_seasons:]
top_k_power = powers[top_k_idxs]
fft_periods = (1 / freqs[top_k_idxs]).astype(int)
 
print(f"top_k_power: {top_k_power}")
print(f"fft_periods: {fft_periods}")
