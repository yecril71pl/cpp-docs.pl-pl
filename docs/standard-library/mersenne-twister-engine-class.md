---
title: mersenne_twister_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::mersenne_twister_engine
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
ms.openlocfilehash: 79613c76b3ea6dc15643e83a15d5bd6d90b60c6a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687701"
---
# <a name="mersenne_twister_engine-class"></a>mersenne_twister_engine — Klasa

Generuje losową sekwencję liczb całkowitych o wysokiej jakości na podstawie algorytmu Mersenne Twister.

## <a name="syntax"></a>Składnia

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>Parametry

@No__t_1 *UIntType*
Typ wyniku bez znaku liczby całkowitej. W przypadku możliwych typów zobacz [\<random >](../standard-library/random.md).

*W* \
**Rozmiar wyrazu**. Rozmiar każdego wyrazu, w bitach, sekwencji stanu. **Warunek wstępny**: `2u < W ≤ numeric_limits<UIntType>::digits`

*N* \
**Rozmiar stanu**. Liczba elementów (wartości) w sekwencji stanu.

*M* \
**Rozmiar przesunięcia**. Liczba elementów do pominięcia podczas każdego skrętu. **Warunek wstępny**: `0 < M ≤ N`

@No__t_1 *R*
**Bity maski**. **Warunek wstępny**: `R ≤ W`

*@No__t_1*
**Maska XOR**. **Warunek wstępny**: `A ≤ (1u<<W) - 1u`

*U*, *S*, *T*, *L* \
**Przepuszczanie parametrów Shift**. Używane jako wartości Shift podczas mieszania (odpuszczanie). Warunek wstępny: `U,S,T,L ≤ W`

*D*, *B*, *C* \
**Odpuszczanie parametrów maski bitów**. Używane jako wartości maski bitowej podczas mieszania (odpuszczanie). Warunek wstępny: `D,B,C ≤ (1u<<W) - 1u`

@No__t_1 *F*
**Mnożnik inicjalizacji**. Używane do zainicjowania sekwencji. Warunek wstępny: `F ≤ (1u<<W) - 1u`

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed` jest stałą członkowską, zdefiniowaną jako `5489u`, używaną jako domyślna wartość parametru `mersenne_twister_engine::seed` i konstruktora pojedynczego wartości.

Aby uzyskać więcej informacji na temat elementów członkowskich silnika, zobacz [\<random >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ten szablon klasy opisuje losowy aparat liczb, zwracając wartości w zamkniętym interwale [`0`, `2`<sup>W</sup>  -  `1`]. Posiada dużą wartość całkowitą z `W * (N - 1) + R` BITS. Wyodrębnia w czasie z tej dużej wartości, a kiedy użył *wszystkich bitów,* przysunie dużą wartość, przenosząc i mieszając bity, tak aby miał nowy zestaw bitów do wyodrębnienia. Stan aparatu to ostatnie `N` `W`-bitowe wartości używane, jeśli `operator()` zostało wywołane co najmniej *N* razy, w przeciwnym razie wartości `M` `W`-bitowe, które zostały użyte, oraz ostatnie `N - M` wartości inicjatora.

Generator przytrzymuje dużą wartość, która jest używana przez przykręcone wysunięte uogólnione rejestry przesunięcia, zdefiniowane przez przesunięcia wartości *N* i *M*, wartość parametru przekręć *R*i warunkowe XOR-mask *a*. Ponadto bity nieprzetworzonego rejestru przesunięcia są szyfrowane (odporne) zgodnie z macierzą szyfrowana, zdefiniowaną przez wartości *U*, *D*, *S*, *B*, *T*, *C*i *L*.

@No__t_0 argumentu szablonu musi być wystarczająco duży, aby pomieścić wartości do `2`<sup>w</sup>  -  `1`. Wartości innych argumentów szablonu muszą spełniać następujące wymagania: `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.

Chociaż można skonstruować Generator z tego aparatu bezpośrednio, zaleca się użycie jednego z tych wstępnie zdefiniowanych typów typedef:

`mt19937`:32-bitowy aparat Twister Mersenne (Matsumoto i Nishimura, 1998).

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64`:64-bitowy aparat Twister Mersenne (Matsumoto i Nishimura, 2000).

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

Aby uzyskać szczegółowe informacje na temat algorytmu Mersenne Twister, zobacz artykuł Wikipedia [Mersenne Twister](https://go.microsoft.com/fwlink/p/?linkid=402356).

## <a name="example"></a>Przykład

Aby zapoznać się z przykładem kodu, zobacz [\<random >](../standard-library/random.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<random >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<random >](../standard-library/random.md)
