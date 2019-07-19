---
title: '&lt;cstdalign&gt;'
ms.date: 07/11/2019
f1_keywords:
- <cstdalign>
- cstdalign
- __alignas_is_defined
- __alignof_is_defined
helpviewer_keywords:
- cstdalign header
- __alignas_is_defined
- __alignof_is_defined
ms.assetid: 9d570924-d299-4225-9a58-8c4c820f5903
ms.openlocfilehash: 603a590190c50495aa80f1b41a574149eb8f760a
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68342249"
---
# <a name="ltcstdaligngt"></a>&lt;cstdalign&gt;

W niektórych C++ implementacjach biblioteki standardowej ten nagłówek zawiera nagłówek \<standardowej biblioteki C stdalign. h > i dodaje `std` skojarzone nazwy do przestrzeni nazw. Ponieważ ten nagłówek nie jest zaimplementowany w MSVC, \<nagłówek > cstdalign definiuje makra `__alignas_is_defined` zgodności i `__alignof_is_defined`.

> [!NOTE]
> Ponieważ nagłówek stdalign. h > definiuje makra, które są słowami C++kluczowymi, w tym nie ma żadnego wpływu. \< Nagłówek > stdalign. h jest przestarzały w programie C++ \< Nagłówek \<> cstdalign jest przestarzały w języku c++ 17 i został usunięty z wersji Standard c++ 20.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<cstdalign >

**Przestrzeń nazw:** std

## <a name="macros"></a>Makra

| Macro | Opis |
| - | - |
| `__alignas_is_defined` | Makro zgodności C, które rozwija się do stałej całkowitej 1. |
| `__alignof_is_defined` | Makro zgodności C, które rozwija się do stałej całkowitej 1. |

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](cpp-standard-library-header-files.md)\
[C++Omówienie biblioteki standardowej](cpp-standard-library-overview.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](thread-safety-in-the-cpp-standard-library.md)
