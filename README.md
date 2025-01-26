# Short-time Variational Mode Decomposition (STVMD)

Python implementation of Short-time Variational Mode Decomposition (STVMD) algorithm, as described in our paper "[Short-time Variational Mode Decomposition](https://arxiv.org/abs/2501.09174)".

## Overview

STVMD extends traditional Variational Mode Decomposition (VMD) by incorporating Short-Time Fourier Transform (STFT) for analyzing non-stationary signals. The method comes in two variants:

- Non-dynamic STVMD: Uses fixed central frequencies across time windows
- Dynamic STVMD: Allows central frequencies to vary with time

## Requirements

```
numpy
scipy
numba
matplotlib
tqdm
```

## Usage

Basic example:

```python
from stvmd import STVMD

# Initialize STVMD
stvmd = STVMD(
    num_channel=1,      # Number of input channels
    n_fft=64,          # FFT size
    alpha=50,          # Balancing parameter
    K=3,               # Number of modes
    tol=1e-9,         # Convergence tolerance
    tau=0.00001       # Update step size
)

# Prepare data
f_hat_s, b_hat_s = stvmd.prepare_offline(signal)

# Apply decomposition
# For non-dynamic STVMD:
u_hat_s, w_hat_s = stvmd.apply(f_hat_s, dynamic=False)

# For dynamic STVMD:
u_hat_s, w_hat_s = stvmd.apply(f_hat_s, dynamic=True)

# Get mode functions
imf_stvmd = stvmd.postprocess(u_hat_s)
```

See `paste.txt` for complete implementation and examples.

## Citation

If you use this code in your research, please cite:

```
@article{jia2024shorttime,
  title={Short-time Variational Mode Decomposition},
  author={Jia, Hao and Cao, Pengfei and Liang, Tong and others},
  journal={arXiv preprint arXiv:2501.09174},
  year={2024}
}
```

## License

[MIT License](LICENSE)

## References

- Original VMD paper: Dragomiretskiy, K., & Zosso, D. (2014). Variational mode decomposition. IEEE transactions on signal processing, 62(3), 531-544.
- MVMD paper: Rehman, N., & Aftab, H. (2019). Multivariate variational mode decomposition. IEEE Transactions on Signal Processing, 67(23), 6039-6052.
