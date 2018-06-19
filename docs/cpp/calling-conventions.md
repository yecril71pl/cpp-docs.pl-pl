---
title: Konwencje wywoływania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9e65dfd7f7cff25debd8eb0d00a7e3bb0397692
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410895"
---
# <a name="calling-conventions"></a>Konwencje wywoływania
Kompilator Visual C/C++ udostępnia kilka różnych konwencji wywoływania funkcji wewnętrznych i zewnętrznych. Opis tych różne podejścia może ułatwić debugowania programu, a następnie połącz kodu za pomocą procedury języka zestawu.  
  
 W tematach w tej sprawie opisano różnice między konwencji wywoływania, jak argumenty są przekazywane i jak wartości są zwracane przez funkcje. Ponadto omówiono w nich wywołania funkcji naked zaawansowana funkcja, która umożliwia napisać własny kod prolog i epilog.  
  
 Aby uzyskać informacje o Konwencje wywoływania dla x64 procesorów, zobacz [konwencji wywoływania](../build/calling-convention.md).  
  
## <a name="topics-in-this-section"></a>Tematy w tej sekcji  
  
-   [Przekazywanie argumentów i konwencje nazewnictwa](../cpp/argument-passing-and-naming-conventions.md) (`__cdecl`, `__stdcall`, `__fastcall`i inne)  
  
-   [Przykład wywołania: prototyp funkcji i wywołanie](../cpp/calling-example-function-prototype-and-call.md)  
  
-   [Pisanie kodu niestandardowego kodu prologu/epilogu przy użyciu wywołania funkcji naked](../cpp/naked-function-calls.md)  
  
-   [Koprocesor zmiennoprzecinkowy i konwencje wywoływania](../cpp/floating-point-coprocessor-and-calling-conventions.md)  
  
-   [Przestarzałe Konwencje wywoływania](../cpp/obsolete-calling-conventions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md)