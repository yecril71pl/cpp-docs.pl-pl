---
title: bidirectional_iterator_tag — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::bidirectional_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 108397f6c3c3c088839230f2b48b505300149345
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844396"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag — Struktura

Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje iteratora dwukierunkowego.

## <a name="syntax"></a>Składnia

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>Uwagi

Klasy tag kategorii są używane jako kompilacji znaczników dla algorytmu zaznaczenia. Funkcja szablonu musi znaleźć najbardziej określonej kategorii argumentu iteratora, dzięki czemu najbardziej efektywny algorytm może użyć w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` <  `Iterator`>:: **iterator_category** musi być zdefiniowany jako najbardziej konkretny tag kategorii, który określa zachowanie iteratora.

Typ jest taki sam jak **iterator** \< **Iter**>:: **iterator_category** podczas **Iter** opisuje obiekt, który można służyć jako iterator dwukierunkowego.

## <a name="example"></a>Przykład

Zobacz [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) przykład sposobu użycia `bidirectional_iterator_tag`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iteratora >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[forward_iterator_tag, struktura](../standard-library/forward-iterator-tag-struct.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
