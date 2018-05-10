---
title: 'Wektor&lt;bool&gt;:: klasę referencyjną | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- vector/vector<bool>::reference
dev_langs:
- C++
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 149b43f0485d3717ad2f413d2519e435f0da0562
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="vectorltboolgtreference-class"></a>Wektor&lt;bool&gt;:: klasę referencyjną

`vector<bool>::reference` Klasa jest klasą proxy dostarczonych przez [wektor\<bool > klasy](../standard-library/vector-bool-class.md) do symulowania `bool&`.

## <a name="remarks"></a>Uwagi

Symulowane odwołanie jest wymagane, ponieważ C++ nie zezwala natywnie na bezpośrednie odwołania do bitów. `vector<bool>` używa tylko jeden bit na element, który można odwoływać się za pomocą tej klasy serwera proxy. Jednakże symulacja odwołania nie jest kompletna, ponieważ niektóre przypisania nie są prawidłowe. Na przykład ponieważ adres `vector<bool>::reference` obiektu nie można wykonywać, następujący kod, który używa [wektor\<bool >:: operator&#91; &#93; ](http://msdn.microsoft.com/Library/97738633-690d-4069-b2d9-8c54104fbfdd) jest nieprawidłowy:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Przerzuć](../standard-library/vector-bool-reference-flip.md)|Odwraca wartość logiczną elementu wektora.|
|[bool — operator](../standard-library/vector-bool-reference-operator-bool.md)|Udostępnia niejawna konwersja z `vector<bool>::reference` do `bool`.|
|[operator=](../standard-library/vector-bool-reference-operator-assign.md)|Przypisuje do bitu wartość logiczną lub wartość przechowywaną przez odnośny element.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<wektor >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[\<Wektor >](../standard-library/vector.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
