---
title: Konwencje wywoływania
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: d351ae064b8c9bdd0599a1d6981166371a62af58
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216612"
---
# <a name="calling-conventions"></a>Konwencje wywoływania

Kompilator języka Visual C/C++ udostępnia kilka różnych konwencji do wywoływania funkcji wewnętrznych i zewnętrznych. Zrozumienie tych różnych metod może ułatwić debugowanie programu i połączenie kodu z procedurami języka asemblera.

W tematach w tym temacie wyjaśniono różnice między konwencjami wywoływania, sposób przekazywania argumentów oraz jak wartości są zwracane przez funkcje. Omawiają one również wywołane wywołania funkcji, zaawansowaną funkcję, która umożliwia pisanie własnego kodu prologu i epilogu.

Aby uzyskać informacje na temat konwencji wywoływania dla procesorów x64, zobacz [konwencję wywoływania](../build/x64-calling-convention.md).

## <a name="topics-in-this-section"></a>Tematy w tej sekcji

- [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md) ( **`__cdecl`** , **`__stdcall`** ,, **`__fastcall`** i inne)

- [Przykład wywołania: prototyp funkcji i wywołanie](../cpp/calling-example-function-prototype-and-call.md)

- [Używanie wywołań funkcji wychodzących w celu pisania niestandardowego kodu prologu/epilogu](../cpp/naked-function-calls.md)

- [Współprocesor zmiennoprzecinkowy i konwencje wywoływania](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>Zobacz także

[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)
