---
title: Specyfikator statycznej klasy magazynowania
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: e84e2745c6077f038f47295119936a1ad6431bdd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229496"
---
# <a name="static-storage-class-specifier"></a>Specyfikator statycznej klasy magazynowania

Zmienna zadeklarowana na poziomie wewnętrznym ze **`static`** specyfikatorem klasy magazynu ma globalny okres istnienia, ale jest widoczna tylko w bloku, w którym jest zadeklarowana. W przypadku ciągów stałych użycie **`static`** jest przydatne, ponieważ zmniejsza obciążenie częstej inicjalizacji w często wywoływanych funkcjach.

## <a name="remarks"></a>Uwagi

Jeśli zmienna nie zostanie jawnie zainicjowana **`static`** , domyślnie zostanie ona zainicjowana przez 0. Wewnątrz funkcji program **`static`** powoduje przydzielenie magazynu i służy jako definicja. Wewnętrzne zmienne statyczne zapewniają prywatny, stały magazyn widoczny tylko dla jednej funkcji.

## <a name="see-also"></a>Zobacz także

[Klasy magazynu w języku C](c-storage-classes.md)<br/>
[Klasy magazynu (C++)](../cpp/storage-classes-cpp.md)
