---
title: Niewłaściwy dostęp do złożenia
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: a08f2c9aa76d0d2f2370dd45f9eb9ace77ceb76c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642961"
---
# <a name="improper-access-to-a-union"></a>Niewłaściwy dostęp do złożenia

**ANSI 3.3.2.3** składowej Unii obiektu odbywa się przy użyciu członkiem innego typu

Jeśli zadeklarowano sumę dwóch typów jednej wartości są przechowywane, ale Unii odbywa się przy użyciu innego typu, wyniki są nieprzewidywalne.

Na przykład sumę **float** i `int` jest zadeklarowana. A **float** wartości są przechowywane, ale program później dostęp do wartości jako `int`. W takiej sytuacji wartość będzie zależeć od pamięci wewnętrznej **float** wartości. Wartość całkowitą nie być wiarygodne.

## <a name="see-also"></a>Zobacz też

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)