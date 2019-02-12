---
title: Specyfikator statycznej klasy magazynowania
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: ef85ee4d757cb9579431427fba7b46a0e5ac905f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148234"
---
# <a name="static-storage-class-specifier"></a>Specyfikator statycznej klasy magazynowania

Zmienna zadeklarowana na poziomie wewnętrznym za pomocą **statyczne** Specyfikator klasy magazynowania ma globalny okres istnienia, ale jest widoczny tylko w bloku, w którym jest zdeklarowana. Dla stałych ciągów przy użyciu **statyczne** jest przydatne, ponieważ jego eliminuje koszty związane z częstych inicjowania w funkcjach często nazywane.

## <a name="remarks"></a>Uwagi

Jeśli nie jawnie zainicjować **statyczne** zmiennej, jest on inicjowany 0 domyślnie. Wewnątrz funkcji **statyczne** powoduje, że magazynu do przydzielenia i stanowi definicję. Wewnętrzne zmienne statyczne magazynowanie prywatnych, stałe widoczne dla tylko jednej funkcji.

## <a name="see-also"></a>Zobacz także

[Klasy magazynu w języku C](c-storage-classes.md)<br/>
[Klasy magazynu (C++)](../cpp/storage-classes-cpp.md)
