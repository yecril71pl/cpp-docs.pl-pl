---
title: "mersenne_twister_engine — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: random/std::mersenne_twister_engine
dev_langs: C++
helpviewer_keywords: mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 58a777a049b270702e63391ebc7bd4c1addc3b32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mersennetwisterengine-class"></a>mersenne_twister_engine — Klasa
Generuje losowe sekwencji liczb całkowitych na podstawie algorytmu — trąba powietrzna w ramach projektu Mersenne wysokiej jakości.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class UIntType,   
    size_t W, size_t N, size_t M, size_t R,  
    UIntType A, size_t U, UIntType D, size_t S,  
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>  
class mersenne_twister_engine;  
```  
  
#### <a name="parameters"></a>Parametry  
 `UIntType`  
 Typ wyniku liczbę całkowitą bez znaku. Dla typów możliwych [ \<losowe >](../standard-library/random.md).  
  
 `W`  
 **Word rozmiar**. Rozmiar każdego wyrazu w bitach sekwencji stanu. **Warunek wstępny**:`2u < W ≤ numeric_limits<UIntType>::digits`  
  
 `N`  
 **Stan: rozmiar**. Liczba elementów (wartości) w sekwencji stanu.  
  
 `M`  
 **Wielkość przesunięcia**. Liczba elementów, aby pominąć podczas każdego dołączony. **Warunek wstępny**:`0 < M ≤ N`  
  
 `R`  
 **Bity maski**. **Warunek wstępny**:`R ≤ W`  
  
 `A`  
 **Maska XOR**. **Warunek wstępny**:`A ≤ (1u<<W) - 1u`  
  
 `U`, `S`, `T`, `L`  
 **Parametry przesunięcia jej**. Używane jako wartości shift podczas zaszyfrowanie (jej). Warunek wstępny:`U,S,T,L ≤ W`  
  
 `D`, `B`, `C`  
 **Jej bit maski parametry**. Używane jako wartości maski bitowej podczas zaszyfrowanie (jej). Warunek wstępny:`D,B,C ≤ (1u<<W) - 1u`  
  
 `F`  
 **Mnożnik inicjowania**. Używane z inicjalizacją sekwencji. Warunek wstępny:`F ≤ (1u<<W) - 1u`  
  
## <a name="members"></a>Elementy członkowskie  
  
||||  
|-|-|-|  
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|  
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|  
  
 `default_seed`jest elementem członkowskim stałej, zdefiniowanej jako `5489u`, używana jako domyślna wartość parametru `mersenne_twister_engine::seed` i Konstruktor pojedynczej wartości.  
  
 Aby uzyskać więcej informacji na temat aparatu członków zobacz [ \<losowe >](../standard-library/random.md).  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa szablonu opisuje losowe aparat numer, zwracanie wartości w interwale zamknięte [ `0`, `2` <sup>W</sup> - `1`]. Przechowuje duża wartość całkowitą z `W * (N - 1) + R` usługi bits. Plik `W` bitów w czasie z tym duża wartość, a jeśli został użyty wszystkie bity go twists duża wartość przesunięciu i łączenie usługi bits, aby miała nowego zestawu usługi bits do wyodrębniania. Stan aparatu jest ostatni `N` `W`-bit wartości użyte, jeśli `operator()` została wywołana w co najmniej `N` czas, w przeciwnym razie `M` `W`-bit wartości, które zostały już użyte oraz za ostatni `N - M` wartości z inicjatora.  
  
 Generator twists duża wartość, która przechowuje za pomocą rejestru shift skręconych opinii uogólniony zdefiniowanych przez wartości przesunięcia `N` i `M`, wartość dołączony `R`i warunkowego maska XOR `A`. Ponadto usługi bits rejestru shift nieprzetworzone są zaszyfrowane (ograniczony) zgodnie z macierzy zaszyfrowanie z bitowego zdefiniowanej przez wartości `U`, `D`, `S`, `B`, `T`, `C`, i `L`.  
  
 Argument szablonu `UIntType` musi być wystarczająco duży, aby pomieścić wartości do `2` <sup>W</sup> - `1`. Wartości do argumentów szablonu musi spełniać następujące wymagania: `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.  
  
 Mimo że można bezpośrednio utworzyć generator z tym aparatem, zaleca się, że używany jest jeden z tych wstępnie zdefiniowanych definicje typów:  
  
 `mt19937`: aparat — trąba powietrzna w ramach projektu Mersenne 32-bitowych (Matsumoto i Nishimura, 1998).  
  
```  
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,   
    31, 0x9908b0df,   
    11, 0xffffffff,   
    7, 0x9d2c5680,   
    15, 0xefc60000,   
    18, 1812433253> mt19937;  
```  
  
 `mt19937_64`: aparat — trąba powietrzna w ramach projektu Mersenne 64-bitowych (Matsumoto i Nishimura, 2000).  
  
```  
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,   
    31, 0xb5026f5aa96619e9ULL,   
    29, 0x5555555555555555ULL,   
    17, 0x71d67fffeda60000ULL,   
    37, 0xfff7eee000000000ULL,   
    43, 6364136223846793005ULL> mt19937_64;  
```  
  
 Aby uzyskać szczegółowe informacje na temat algorytm — trąba powietrzna w ramach projektu Mersenne, zobacz artykuł Wikipedia [— trąba powietrzna w ramach projektu Mersenne](http://go.microsoft.com/fwlink/LinkId=402356).  
  
## <a name="example"></a>Przykład  
 Na przykład kod, zobacz [ \<losowe >](../standard-library/random.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<losowe >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<losowe >](../standard-library/random.md)

