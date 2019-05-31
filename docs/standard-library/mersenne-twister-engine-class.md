---
title: mersenne_twister_engine — Klasa
ms.date: 11/04/2016
f1_keywords:
- random/std::mersenne_twister_engine
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
ms.openlocfilehash: 9949d1cab5a97b30df0b156289dff2dfbe15d851
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449674"
---
# <a name="mersennetwisterengine-class"></a>mersenne_twister_engine — Klasa

Generuje losową sekwencję liczb całkowitych, w oparciu o algorytmu Mersenne twister wysokiej jakości.

## <a name="syntax"></a>Składnia

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>Parametry

*UIntType*<br/>
Typ wyniku liczby całkowitej bez znaku. Aby możliwych typów, zobacz [ \<losowy >](../standard-library/random.md).

*W*<br/>
**Word rozmiar**. Rozmiar każdego wyrazu w bitach sekwencji stanu. **Warunek wstępny**: `2u < W ≤ numeric_limits<UIntType>::digits`

*N*<br/>
**Stan: rozmiar**. Liczba elementów (wartości) w sekwencji stanu.

*M*<br/>
**Zmiany rozmiaru**. Liczba elementów do pominięcia podczas każdego akcentem. **Warunek wstępny**: `0 < M ≤ N`

*R*<br/>
**Maski bitów**. **Warunek wstępny**: `R ≤ W`

*A*<br/>
**Maska XOR**. **Warunek wstępny**: `A ≤ (1u<<W) - 1u`

*U*, *S*, *T*, *L*<br/>
**Jej parametry przesunięcia**. Używane jako wartości przesunięcia podczas zaszyfrowanie (jej). Warunek wstępny: `U,S,T,L ≤ W`

*D*, *B*, *C*<br/>
**Jej bit maski parametry**. Używane jako wartości maski bitowej podczas zaszyfrowanie (jej). Warunek wstępny: `D,B,C ≤ (1u<<W) - 1u`

*F*<br/>
**Mnożnik inicjowania**. Używane z inicjalizacją sekwencji. Warunek wstępny: `F ≤ (1u<<W) - 1u`

## <a name="members"></a>Elementy członkowskie

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed` jest elementem członkowskim stałą, definiowany jako `5489u`, który jest używany jako wartość domyślna parametru `mersenne_twister_engine::seed` i konstruktora pojedynczej wartości.

Aby uzyskać więcej informacji na temat elementów członkowskich aparatu zobacz [ \<losowy >](../standard-library/random.md).

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje losowego silnika liczb, zwracanie wartości w zamkniętym przedziale [ `0`, `2` <sup>W</sup> - `1`]. Przechowuje dużą wartość całkowitą z `W * (N - 1) + R` usługi bits. Wyodrębnia *W* bitów jednorazowo z tej dużej wartości, a kiedy zużyje wszystkie bity, skręca dużą wartość przez przesunięcie i zmieszanie bitów, tak aby mieć nowy zestaw bitów w celu wyodrębnienia z. Stan aparatu to ostatnie `N` `W`-bit używane, jeśli wartości `operator()` została wywołana co najmniej *N* czas, w przeciwnym razie `M` `W`-bitowe wartości, które zostały użyte, a ostatni `N - M` wartości inicjatora.

Generator skręca dużą wartość, która przechowuje, za pomocą rejestru shift skręconych opinii uogólniony, zdefiniowane przez wartości przesunięcia *N* i *M*, wartość akcentem *R*, a warunkowe maska XOR *A*. Ponadto bity rejestru shift pierwotne są zaszyfrowane (UFNOŚĆ), zgodnie z macierzy zaszyfrowanie bit zdefiniowanej przez wartości *U*, *D*, *S*, *B* , *T*, *C*, i *L*.

Argument szablonu `UIntType` musi być wystarczająco duży, aby przechowywać wartości do `2` <sup>W</sup> - `1`. Wartości innych argumentów szablonu muszą spełniać następujące wymagania: `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.

Chociaż można utworzyć generatora z tego aparatu bezpośrednio, zalecane jest korzystanie z jednej z tych definicji wstępnie zdefiniowanych typów:

`mt19937`: 32-bitowe aparatu Mersenne twister (Matsumoto i Nishimura-1998).

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64`: 64-bitowe aparatu Mersenne twister (Matsumoto i Nishimura, 2000).

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

Aby uzyskać szczegółowe informacje na temat algorytmu Mersenne twister Zobacz artykułu w Wikipedii [Mersenne twister](https://go.microsoft.com/fwlink/p/?linkid=402356).

## <a name="example"></a>Przykład

Dla przykładu kodu zobacz [ \<losowy >](../standard-library/random.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<losowy >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<random>](../standard-library/random.md)<br/>
