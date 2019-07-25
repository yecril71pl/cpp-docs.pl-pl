---
title: 'Vector&lt;bool&gt;:: Reference — Klasa'
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 65bfc91cf5dc79fb1e5151a6f62c394b4579883b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453214"
---
# <a name="vectorltboolgtreference-class"></a>Vector&lt;bool&gt;:: Reference — Klasa

Klasa jest klasą proxy dostarczoną przez `bool&` [klasę >\<bool wektorowego](../standard-library/vector-bool-class.md) do symulowania. `vector<bool>::reference`

## <a name="remarks"></a>Uwagi

Symulowane odwołanie jest wymagane, ponieważ C++ nie zezwala natywnie na bezpośrednie odwołania do bitów. `vector<bool>`wykorzystuje tylko jeden bit na element, do którego można odwoływać się za pomocą tej klasy proxy. Jednakże symulacja odwołania nie jest kompletna, ponieważ niektóre przypisania nie są prawidłowe. Na przykład, ponieważ nie można wykonać adresu `vector<bool>::reference` obiektu, następujący kod, który próbuje użyć `vector<bool>::operator&` , jest niepoprawny:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[stosowane](../standard-library/vector-bool-reference-flip.md)|Odwraca wartość logiczną elementu wektora.|
|[wartość logiczna operatora](../standard-library/vector-bool-reference-operator-bool.md)|Zapewnia niejawną konwersję z `vector<bool>::reference` na wartość **logiczną**.|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|Przypisuje do bitu wartość logiczną lub wartość przechowywaną przez odnośny element.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<wektor >

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<> wektora](../standard-library/vector.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
