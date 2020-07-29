---
title: 'Vector &lt; bool &gt; :: Reference — Klasa'
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 3dde17522c05a05bda04c338682b4b3f9920a972
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228105"
---
# <a name="vectorltboolgtreference-class"></a>Vector &lt; bool &gt; :: Reference — Klasa

`vector<bool>::reference`Klasa jest klasą serwera proxy dostarczoną przez [ \<bool> klasę Vector](../standard-library/vector-bool-class.md) do symulowania `bool&` .

## <a name="remarks"></a>Uwagi

Symulowane odwołanie jest wymagane, ponieważ C++ nie zezwala natywnie na bezpośrednie odwołania do bitów. `vector<bool>`wykorzystuje tylko jeden bit na element, do którego można odwoływać się za pomocą tej klasy proxy. Jednakże symulacja odwołania nie jest kompletna, ponieważ niektóre przypisania nie są prawidłowe. Na przykład, ponieważ nie można wykonać adresu `vector<bool>::reference` obiektu, następujący kod, który próbuje użyć, `vector<bool>::operator&` jest niepoprawny:

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
|[wartość logiczna operatora](../standard-library/vector-bool-reference-operator-bool.md)|Zapewnia niejawną konwersję z `vector<bool>::reference` na **`bool`** .|
|[operator =](../standard-library/vector-bool-reference-operator-assign.md)|Przypisuje do bitu wartość logiczną lub wartość przechowywaną przez odnośny element.|

## <a name="requirements"></a>Wymagania

**Nagłówek**:\<vector>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[\<vector>](../standard-library/vector.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
