---
title: numeric (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/numeric>
- cliext::accumulate
- cliext::adjacent_difference
- cliext::inner_product
- cliext::partial_sum
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
- accumulate function [STL/CLR]
- adjacent_difference function [STL/CLR]
- inner_product function [STL/CLR]
- partial_sum function [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
ms.openlocfilehash: 1939a6dd9b6d8186eb278623f3b0a5a3d851f4d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208484"
---
# <a name="numeric-stlclr"></a>numeric (STL/CLR)

Definiuje funkcje szablonu kontenera, które wykonują algorytmy przeznaczone do przetwarzania liczbowego.

## <a name="syntax"></a>Składnia

```
#include <cliext/numeric>
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cliext/> liczbowej

**Przestrzeń nazw:** cliext

## <a name="declarations"></a>Deklaracje

|Funkcja|Opis|
|--------------|-----------------|
|[accumulate (STL/CLR)](#accumulate)|Oblicza sumę wszystkich elementów w określonym zakresie, w tym pewną wartość początkową przez Obliczanie kolejnych sum częściowych lub oblicza wynik kolejnych częściowe wyniki, podobnie jak w przypadku użycia określonej operacji binarnej innej niż suma.|
|[adjacent_difference (STL/CLR)](#adjacent_difference)|Oblicza kolejne różnice między każdym elementem i jego poprzednikiem w zakresie wejściowym i generuje wyjściowe wyniki do zakresu docelowego lub oblicza wynik ogólnej procedury, gdzie operacja różnicy zostaje zastąpiona przez inną, określoną operację binarną.|
|[inner_product (STL/CLR)](#inner_product)|Oblicza sumę iloczynów elementów z dwóch zakresów i dodaje ją do określonej wartości początkowej lub oblicza wynik ogólnej procedury, gdzie operacje sum i danych binarnych produktu są zastępowane przez inne określone operacje binarne.|
|[partial_sum (STL/CLR)](#partial_sum)|Oblicza serię sum w zakresie wejściowym od pierwszego elementu za pośrednictwem `i`ego elementu i zapisuje wynik każdej takiej sumy w `i`tym elemencie zakresu docelowego lub oblicza wynik ogólnej procedury, gdzie operacja sum jest zastępowana przez inną określoną operację binarną.|

## <a name="members"></a>Members

## <a name="accumulate-stlclr"></a><a name="accumulate"></a>Akumulacja (STL/CLR)

Oblicza sumę wszystkich elementów w określonym zakresie, w tym pewną wartość początkową przez Obliczanie kolejnych sum częściowych lub oblicza wynik kolejnych częściowe wyniki, podobnie jak w przypadku użycia określonej operacji binarnej innej niż suma.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _Ty> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);
template<class _InIt, class _Ty, class _Fn2> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak w C++ przypadku standardowej funkcji numerycznej `accumulate`. Aby uzyskać więcej informacji, zobacz [gromadzenie](../standard-library/numeric-functions.md#accumulate).

## <a name="adjacent_difference-stlclr"></a><a name="adjacent_difference"></a>adjacent_difference (STL/CLR)

Oblicza kolejne różnice między każdym elementem i jego poprzednikiem w zakresie wejściowym i generuje wyjściowe wyniki do zakresu docelowego lub oblicza wynik ogólnej procedury, gdzie operacja różnicy zostaje zastąpiona przez inną, określoną operację binarną.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak w C++ przypadku standardowej funkcji numerycznej `adjacent_difference`. Aby uzyskać więcej informacji, zobacz [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference).

## <a name="inner_product-stlclr"></a><a name="inner_product"></a>inner_product (STL/CLR)

Oblicza sumę iloczynów elementów z dwóch zakresów i dodaje ją do określonej wartości początkowej lub oblicza wynik ogólnej procedury, gdzie operacje sum i danych binarnych produktu są zastępowane przez inne określone operacje binarne.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt1, class _InIt2, class _Ty> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val);
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,
       class _Fn22> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak w C++ przypadku standardowej funkcji numerycznej `inner_product`. Aby uzyskać więcej informacji, zobacz [inner_product](../standard-library/numeric-functions.md#inner_product).

## <a name="partial_sum-stlclr"></a><a name="partial_sum"></a>partial_sum (STL/CLR)

Oblicza serię sum w zakresie wejściowym od pierwszego elementu za pośrednictwem `i`ego elementu i zapisuje wynik każdej takiej sumy w `i`tym elemencie zakresu docelowego lub oblicza wynik ogólnej procedury, gdzie operacja sum jest zastępowana przez inną określoną operację binarną.

### <a name="syntax"></a>Składnia

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Uwagi

Ta funkcja zachowuje się tak samo jak w C++ przypadku standardowej funkcji numerycznej `partial_sum`. Aby uzyskać więcej informacji, zobacz [partial_sum](../standard-library/numeric-functions.md#partial_sum).
