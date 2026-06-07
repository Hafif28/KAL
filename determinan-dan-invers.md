# Determinan dan Invers Matriks

## Pengenalan

Determinan dan invers matriks adalah dua konsep fundamental dalam aljabar linear yang memiliki banyak aplikasi praktis. Determinan digunakan untuk:
- Menentukan apakah matriks invertible
- Menghitung luas/volume dalam transformasi geometri
- Menyelesaikan sistem persamaan linear dengan Aturan Cramer

Invers matriks adalah "kebalikan" dari matriks, mirip dengan konsep bilangan invers dalam aritmetika biasa.

---

## 1. Determinan Matriks

### 1.1 Definisi Determinan

Determinan adalah nilai skalar yang dapat dihitung dari matriks persegi $n \times n$. Notasi: $\det(A)$ atau $|A|$.

#### **Kasus 1: Matriks 1×1**
Jika $A = [a]$, maka:
$$\det(A) = a$$

#### **Kasus 2: Matriks 2×2**
Jika $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$, maka:
$$\det(A) = ad - bc$$

**Contoh 2×2:**
$$A = \begin{bmatrix} 3 & 2 \\ 1 & 4 \end{bmatrix}$$
$$\det(A) = (3)(4) - (2)(1) = 12 - 2 = 10$$

#### **Kasus 3: Matriks 3×3**
Untuk matriks $A = \begin{bmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{bmatrix}$

Menggunakan **Ekspansi Kofaktor pada Baris Pertama:**
$$\det(A) = a_{11}C_{11} + a_{12}C_{12} + a_{13}C_{13}$$

di mana $C_{ij} = (-1)^{i+j}M_{ij}$ adalah **kofaktor**, dan $M_{ij}$ adalah **minor** (determinan submatriks setelah menghapus baris $i$ dan kolom $j$).

---

### 1.2 Ekspansi Kofaktor (Metode Laplace)

Untuk menghitung determinan matriks $n \times n$, gunakan ekspansi pada baris atau kolom:

$$\det(A) = \sum_{j=1}^{n} (-1)^{1+j} a_{1j} M_{1j}$$

**Langkah-langkah:**
1. Pilih baris atau kolom (biasanya baris pertama)
2. Untuk setiap elemen $a_{ij}$, hitung minornya $M_{ij}$
3. Hitung kofaktor $C_{ij} = (-1)^{i+j}M_{ij}$
4. Jumlahkan: $\det(A) = \sum a_{ij} \cdot C_{ij}$

**Contoh 3×3:**
$$A = \begin{bmatrix} 2 & 1 & -1 \\ -3 & -1 & 2 \\ -2 & 1 & 2 \end{bmatrix}$$

Ekspansi pada baris pertama:
$$\det(A) = 2 \begin{vmatrix} -1 & 2 \\ 1 & 2 \end{vmatrix} - 1 \begin{vmatrix} -3 & 2 \\ -2 & 2 \end{vmatrix} + (-1) \begin{vmatrix} -3 & -1 \\ -2 & 1 \end{vmatrix}$$

$$= 2[(-1)(2) - (2)(1)] - 1[(-3)(2) - (2)(-2)] - 1[(-3)(1) - (-1)(-2)]$$

$$= 2[-2 - 2] - 1[-6 + 4] - 1[-3 - 2]$$

$$= 2(-4) - 1(-2) - 1(-5) = -8 + 2 + 5 = -1$$

---

### 1.3 Sifat-Sifat Determinan

| Sifat | Penjelasan |
|-------|-----------|
| $\det(A^T) = \det(A)$ | Determinan transpose sama dengan determinan asli |
| $\det(AB) = \det(A) \cdot \det(B)$ | Determinan perkalian = perkalian determinan |
| $\det(cA) = c^n \det(A)$ | Mengalikan baris dengan skalar $c$ mengalikan determinan dengan $c^n$ |
| $\det(A) = 0$ jika ada dua baris/kolom identik | Matriks singular (tidak invertible) |
| $\det(I) = 1$ | Determinan matriks identitas adalah 1 |

---

## 2. Matriks Invers

### 2.1 Definisi Matriks Invers

Matriks invers dari $A$ (ditulis $A^{-1}$) adalah matriks yang memenuhi:
$$A \cdot A^{-1} = A^{-1} \cdot A = I$$

di mana $I$ adalah matriks identitas.

**Syarat Invertible:**
Matriks $A$ invertible jika dan hanya jika $\det(A) \neq 0$.

---

### 2.2 Invers Matriks 2×2

Untuk $A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}$ dengan $\det(A) = ad - bc \neq 0$:

$$A^{-1} = \frac{1}{ad-bc} \begin{bmatrix} d & -b \\ -c & a \end{bmatrix}$$

**Contoh 2×2:**
$$A = \begin{bmatrix} 3 & 2 \\ 1 & 4 \end{bmatrix}, \quad \det(A) = 10$$

$$A^{-1} = \frac{1}{10} \begin{bmatrix} 4 & -2 \\ -1 & 3 \end{bmatrix} = \begin{bmatrix} 0.4 & -0.2 \\ -0.1 & 0.3 \end{bmatrix}$$

**Verifikasi:**
$$A \cdot A^{-1} = \begin{bmatrix} 3 & 2 \\ 1 & 4 \end{bmatrix} \begin{bmatrix} 0.4 & -0.2 \\ -0.1 & 0.3 \end{bmatrix} = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$$ ✓

---

### 2.3 Invers Matriks 3×3 (Metode Adjoin)

Untuk matriks $n \times n$:
$$A^{-1} = \frac{1}{\det(A)} \text{adj}(A)$$

di mana $\text{adj}(A)$ adalah **matriks adjoin** (adjugat).

**Langkah-langkah:**

1. **Hitung determinan** $\det(A)$ (harus $\neq 0$)
2. **Hitung matriks kofaktor** $C_{ij} = (-1)^{i+j}M_{ij}$
3. **Transpose matriks kofaktor** untuk mendapatkan adjoin: $\text{adj}(A) = C^T$
4. **Hitung invers:** $A^{-1} = \frac{1}{\det(A)} \text{adj}(A)$

**Contoh 3×3:**
$$A = \begin{bmatrix} 2 & 1 & -1 \\ -3 & -1 & 2 \\ -2 & 1 & 2 \end{bmatrix}$$

Dari contoh sebelumnya: $\det(A) = -1$

Matriks kofaktor:
$$C_{11} = (-1)^{1+1}\begin{vmatrix} -1 & 2 \\ 1 & 2 \end{vmatrix} = -4$$
$$C_{12} = (-1)^{1+2}\begin{vmatrix} -3 & 2 \\ -2 & 2 \end{vmatrix} = 2$$
$$C_{13} = (-1)^{1+3}\begin{vmatrix} -3 & -1 \\ -2 & 1 \end{vmatrix} = -5$$
$$\ldots \text{(lanjutkan untuk elemen lainnya)}$$

Matriks adjoin = transpose dari matriks kofaktor

$$A^{-1} = \frac{1}{-1} \text{adj}(A) = -\text{adj}(A)$$

---

### 2.4 Menggunakan Python

```python
import numpy as np
from numpy.linalg import det, inv

# Contoh matriks 3x3
A = np.array([
    [2, 1, -1],
    [-3, -1, 2],
    [-2, 1, 2]
])

# Hitung determinan
det_A = det(A)
print(f"Determinan A: {det_A}")

# Hitung invers
A_inv = inv(A)
print(f"Invers A:\n{A_inv}")

# Verifikasi: A * A^{-1} = I
I = A @ A_inv
print(f"A * A^{-1}:\n{I}")
```

---

## 3. Aplikasi: Menyelesaikan Sistem Persamaan Linear

### 3.1 Menggunakan Invers Matriks

Sistem linear $Ax = b$ dapat diselesaikan dengan:
$$x = A^{-1}b$$

**Contoh:**
$$\begin{cases} 2x + y - z = 8 \\ -3x - y + 2z = -11 \\ -2x + y + 2z = -3 \end{cases}$$

Dalam bentuk matriks:
$$\begin{bmatrix} 2 & 1 & -1 \\ -3 & -1 & 2 \\ -2 & 1 & 2 \end{bmatrix} \begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} 8 \\ -11 \\ -3 \end{bmatrix}$$

Hitung $x = A^{-1}b$:
$$\begin{bmatrix} x \\ y \\ z \end{bmatrix} = A^{-1} \begin{bmatrix} 8 \\ -11 \\ -3 \end{bmatrix}$$

**Solusi:** $x = 2, y = 3, z = -1$

```python
import numpy as np

A = np.array([
    [2, 1, -1],
    [-3, -1, 2],
    [-2, 1, 2]
])

b = np.array([8, -11, -3])

# Selesaikan menggunakan invers
x = np.linalg.inv(A) @ b
print(f"Solusi: x = {x[0]}, y = {x[1]}, z = {x[2]}")
```

---

## 4. Tugas Latihan

### A. Hitung Determinan

Hitunglah determinan matriks berikut menggunakan ekspansi kofaktor:

1. $A = \begin{bmatrix} -7 & -5 \\ 1 & 4 \end{bmatrix}$

2. $A = \begin{bmatrix} 0 & 2 & -3 \\ 1 & -2 & -1 \\ 0 & 0 & 1 \end{bmatrix}$

3. $A = \begin{bmatrix} 1 & -3 & 1 & -3 \\ 1 & -3 & 1 & 1 \\ 1 & -3 & 1 & 1 \\ 1 & -3 & 1 & 1 \end{bmatrix}$

### B. Hitung Invers Matriks

Gunakan rumus matriks adjoin untuk menghitung invers dari matriks berikut dengan rumus $A^{-1} = \frac{1}{\det(A)} \text{adj}(A)$:

1. $A = \begin{bmatrix} -7 & -5 \\ 1 & 4 \end{bmatrix}$

2. $A = \begin{bmatrix} 0 & 2 & -3 \\ 1 & -2 & -1 \\ 0 & 0 & 1 \end{bmatrix}$

### C. Selesaikan Sistem Persamaan Linear

Gunakan invers matriks untuk menyelesaikan sistem persamaan:

$$\begin{cases} x + y + z + w = 10 \\ 2x - y + z + w = 5 \\ 3x + y - z + w = 1 \\ 2x + 2y + 3z - w = 7 \end{cases}$$

---

## 5. Kesimpulan

| Konsep | Penjelasan |
|--------|-----------|
| **Determinan** | Nilai skalar yang menunjukkan sifat matriks; $\det(A) = 0$ berarti matriks singular |
| **Matriks Invers** | Matriks yang memenuhi $AA^{-1} = I$; hanya ada jika $\det(A) \neq 0$ |
| **Aplikasi** | Menyelesaikan sistem linear, transformasi geometri, eigenvalue problems |
| **Metode Perhitungan** | Ekspansi kofaktor (manual), operasi baris elementer, atau menggunakan library (NumPy) |

---

## 6. Referensi

- Kajabbej et al. "Komputasi Aljabar Linear"
- KALI Repository: https://kajabbej.github.io/kalghrn/
- Moelaab's KALI: https://moelaab.github.io/kali/
