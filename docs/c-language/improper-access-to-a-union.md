---
title: Niewłaściwy dostęp do złożenia
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: 5a804ed80c8f1ac2f5dd9a24f12c67e96e199b6b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227832"
---
# <a name="improper-access-to-a-union"></a>Niewłaściwy dostęp do złożenia

**3.3.2.3 ANSI** Do elementu członkowskiego obiektu Union uzyskuje się dostęp przy użyciu elementu członkowskiego innego typu

Jeśli jest zadeklarowana Unia dwóch typów i jest przechowywana jedna wartość, a Unia jest dostępna z innym typem, wyniki są niezawodne.

Na przykład Unia **`float`** i **`int`** jest zadeklarowana. **`float`** Wartość jest przechowywana, ale program później uzyskuje dostęp do wartości jako **`int`** . W takiej sytuacji wartość będzie zależeć od wewnętrznego magazynu **`float`** wartości. Wartość całkowita nie będzie godna zaufania.

## <a name="see-also"></a>Zobacz także

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)
