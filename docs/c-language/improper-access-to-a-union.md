---
title: Niewłaściwy dostęp do złożenia
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: 9fd7bdc753f6359a8760e58813f9009411c1bf44
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326134"
---
# <a name="improper-access-to-a-union"></a>Niewłaściwy dostęp do złożenia

**ANSI 3.3.2.3** składowej Unii obiektu odbywa się przy użyciu członkiem innego typu

Jeśli zadeklarowano sumę dwóch typów jednej wartości są przechowywane, ale Unii odbywa się przy użyciu innego typu, wyniki są nieprzewidywalne.

Na przykład sumę **float** i `int` jest zadeklarowana. A **float** wartości są przechowywane, ale program później dostęp do wartości jako `int`. W takiej sytuacji wartość będzie zależeć od pamięci wewnętrznej **float** wartości. Wartość całkowitą nie być wiarygodne.

## <a name="see-also"></a>Zobacz także

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)
