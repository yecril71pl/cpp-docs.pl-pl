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

**3.3.2.3 ANSI** Do elementu członkowskiego obiektu Union uzyskuje się dostęp przy użyciu elementu członkowskiego innego typu

Jeśli jest zadeklarowana Unia dwóch typów i jest przechowywana jedna wartość, a Unia jest dostępna z innym typem, wyniki są niezawodne.

Na przykład Unia **zmiennoprzecinkowa** i `int` jest zadeklarowana. Wartość **zmiennoprzecinkowa** jest przechowywana, ale program później uzyskuje dostęp do wartości jako `int`. W takiej sytuacji wartość będzie zależeć od wewnętrznego magazynu wartości **zmiennoprzecinkowych** . Wartość całkowita nie będzie godna zaufania.

## <a name="see-also"></a>Zobacz też

[Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)
