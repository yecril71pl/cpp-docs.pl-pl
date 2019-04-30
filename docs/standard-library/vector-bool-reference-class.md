---
title: 'Wektor&lt;bool&gt;:: reference — klasa'
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 7930c1cd93cd05a752d4997b9480c766ee26bd99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407721"
---
# <a name="vectorltboolgtreference-class"></a>Wektor&lt;bool&gt;:: reference — klasa

`vector<bool>::reference` Klasa jest klasą proxy dostarczoną przez [wektor\<bool > klasa](../standard-library/vector-bool-class.md) do symulacji `bool&`.

## <a name="remarks"></a>Uwagi

Symulowane odwołanie jest wymagane, ponieważ C++ nie zezwala natywnie na bezpośrednie odwołania do bitów. `vector<bool>` używa tylko jednego bitu na element, który można odwoływać się za pomocą tej klasy proxy. Jednakże symulacja odwołania nie jest kompletna, ponieważ niektóre przypisania nie są prawidłowe. Na przykład ponieważ adres `vector<bool>::reference` obiektu nie może być przyjęty, następujący kod, który próbuje użyć `vector<bool>::operator&` jest nieprawidłowy:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|Odwraca wartość logiczną elementu wektora.|
|[bool — operator](../standard-library/vector-bool-reference-operator-bool.md)|Dostarcza niejawną konwersję z `vector<bool>::reference` do **bool**.|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|Przypisuje do bitu wartość logiczną lub wartość przechowywaną przez odnośny element.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<wektor >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[\<vector>](../standard-library/vector.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
