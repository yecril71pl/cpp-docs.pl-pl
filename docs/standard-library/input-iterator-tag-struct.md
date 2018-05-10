---
title: input_iterator_tag — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::input_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 797bc6353bd7396d409de073cc412480a803117f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="inputiteratortag-struct"></a>input_iterator_tag — Struktura

Klasa, która zawiera typ zwracany dla **iterator_category** funkcja, która reprezentuje wejściowych iteratora.

## <a name="syntax"></a>Składnia

input_iterator_tag — struktura {};

## <a name="remarks"></a>Uwagi

Klasy tag kategorii są używane jako kompilacji znaczników dla algorytmu zaznaczenia. Funkcja szablonu musi znaleźć najbardziej określonej kategorii argumentu iteratora tak, aby najbardziej efektywny algorytm może użyć w czasie kompilacji. Dla każdego iteratora typu `Iterator`, `iterator_traits` <  `Iterator` >  **:: iterator_category** musi być zdefiniowany jako najbardziej konkretny tag kategorii, który określa zachowanie iteratora.

Typ jest taki sam jak **iterator** \< **Iter**> **:: iterator_category** podczas **Iter** opisuje obiekt, który może służyć jako wejściowych iteratora.

## <a name="example"></a>Przykład

Zobacz [iterator_traits](../standard-library/iterator-traits-struct.md) lub [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) przykład sposobu użycia **iterator_tag**s.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<iteratora >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
