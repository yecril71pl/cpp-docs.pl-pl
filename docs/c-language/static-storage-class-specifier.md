---
title: Specyfikator statycznej klasy magazynowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1a58a8c7ab6eeb7d304d84cef15beb9046184fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079495"
---
# <a name="static-storage-class-specifier"></a>Specyfikator statycznej klasy magazynowania

Zmienna zadeklarowana na poziomie wewnętrznym za pomocą **statyczne** Specyfikator klasy magazynowania ma globalny okres istnienia, ale jest widoczny tylko w bloku, w którym jest zdeklarowana. Dla stałych ciągów przy użyciu **statyczne** jest przydatne, ponieważ jego eliminuje koszty związane z częstych inicjowania w funkcjach często nazywane.

## <a name="remarks"></a>Uwagi

Jeśli nie jawnie zainicjować **statyczne** zmiennej, jest on inicjowany 0 domyślnie. Wewnątrz funkcji **statyczne** powoduje, że magazynu do przydzielenia i stanowi definicję. Wewnętrzne zmienne statyczne magazynowanie prywatnych, stałe widoczne dla tylko jednej funkcji.

## <a name="see-also"></a>Zobacz też

[Klasy magazynu w języku C](c-storage-classes.md)<br/>
[Klasy magazynu (C++)](../cpp/storage-classes-cpp.md)