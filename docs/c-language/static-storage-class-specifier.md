---
title: Specyfikator statycznej klasy magazynowania
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: 2596e257ae6e22e207451b97b0361aecdfffba03
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594041"
---
# <a name="static-storage-class-specifier"></a>Specyfikator statycznej klasy magazynowania

Zmienna zadeklarowana na poziomie wewnętrznym za pomocą **statyczne** Specyfikator klasy magazynowania ma globalny okres istnienia, ale jest widoczny tylko w bloku, w którym jest zdeklarowana. Dla stałych ciągów przy użyciu **statyczne** jest przydatne, ponieważ jego eliminuje koszty związane z częstych inicjowania w funkcjach często nazywane.

## <a name="remarks"></a>Uwagi

Jeśli nie jawnie zainicjować **statyczne** zmiennej, jest on inicjowany 0 domyślnie. Wewnątrz funkcji **statyczne** powoduje, że magazynu do przydzielenia i stanowi definicję. Wewnętrzne zmienne statyczne magazynowanie prywatnych, stałe widoczne dla tylko jednej funkcji.

## <a name="see-also"></a>Zobacz też

[Klasy magazynu w języku C](c-storage-classes.md)<br/>
[Klasy magazynu (C++)](../cpp/storage-classes-cpp.md)