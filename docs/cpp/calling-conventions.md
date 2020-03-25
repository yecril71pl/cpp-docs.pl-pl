---
title: Konwencje wywoływania
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: 432cb1b6910db5ea735288edfbf6aa9e10f0a486
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190290"
---
# <a name="calling-conventions"></a>Konwencje wywoływania

Kompilator Visual C/C++ Compiler oferuje kilka różnych konwencji do wywoływania funkcji wewnętrznych i zewnętrznych. Zrozumienie tych różnych metod może ułatwić debugowanie programu i połączenie kodu z procedurami języka asemblera.

W tematach w tym temacie wyjaśniono różnice między konwencjami wywoływania, sposób przekazywania argumentów oraz jak wartości są zwracane przez funkcje. Omawiają one również wywołane wywołania funkcji, zaawansowaną funkcję, która umożliwia pisanie własnego kodu prologu i epilogu.

Aby uzyskać informacje na temat konwencji wywoływania dla procesorów x64, zobacz [konwencję wywoływania](../build/x64-calling-convention.md).

## <a name="topics-in-this-section"></a>Tematy w tej sekcji

- [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md) (`__cdecl`, `__stdcall`, `__fastcall`i inne)

- [Przykład wywołania: prototyp funkcji i wywołanie](../cpp/calling-example-function-prototype-and-call.md)

- [Używanie wywołań funkcji wychodzących w celu pisania niestandardowego kodu prologu/epilogu](../cpp/naked-function-calls.md)

- [Koprocesor zmiennoprzecinkowy i konwencje wywoływania](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [Przestarzałe konwencje wywoływania](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>Zobacz też

[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)
