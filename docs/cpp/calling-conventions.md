---
title: Konwencje wywoływania
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: cc79a0636f900aa49e31f0dc35ee19657c3e1ccb
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345118"
---
# <a name="calling-conventions"></a>Konwencje wywoływania

Kompilator Visual C/C++ udostępnia kilka różnych konwencji wywoływania funkcji wewnętrznych i zewnętrznych. Zrozumienie tych różnych rozwiązań może ułatwić debugowania programu i połącz swój kod za pomocą procedury języka zestawu.

Tematy w tej sprawie wyjaśniono różnice między konwencji wywoływania, jak argumenty są przekazywane, a także sposób wartości są zwracane przez funkcje. Rozmawiają oni również o tym wywołania funkcji naked to zaawansowana funkcja, która umożliwia pisania własnego kodu prologu i epilogu.

Aby uzyskać informacji na temat konwencji wywoływania x64 procesorów, zobacz [konwencji wywoływania](../build/x64-calling-convention.md).

## <a name="topics-in-this-section"></a>Tematy w tej sekcji

- [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md) (`__cdecl`, `__stdcall`, `__fastcall`i inne)

- [Przykład wywołania: prototyp funkcji i wywołanie](../cpp/calling-example-function-prototype-and-call.md)

- [Pisanie kodu prologu/epilogu niestandardowych przy użyciu wywołania funkcji naked](../cpp/naked-function-calls.md)

- [Koprocesor zmiennoprzecinkowy i konwencje wywoływania](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [Przestarzałe Konwencje wywoływania](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>Zobacz także

[Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)