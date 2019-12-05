---
title: Wywołania funkcji Naked
ms.date: 11/04/2016
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
ms.openlocfilehash: 242fe83807c6608a09492d0f1f817e3b6e50e530
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857401"
---
# <a name="naked-function-calls"></a>Wywołania funkcji Naked

**Microsoft Specific**

Funkcje zadeklarowane z atrybutem " **owies** " są emitowane bez kodu prologu lub epilogu, dzięki czemu można pisać własne niestandardowe sekwencje Prolog/epilogu przy użyciu [wbudowanego asemblera](../assembler/inline/inline-assembler.md). Funkcje wykorzystające są dostępne jako funkcja zaawansowana. Umożliwiają one zadeklarować funkcję, która jest wywoływana z kontekstu innego niż C/C++, i w ten sposób wprowadzić różne założenia dotyczące lokalizacji parametrów lub rejestrów, które są zachowywane. Przykłady obejmują procedury, takie jak programy obsługi przerwań. Ta funkcja jest szczególnie przydatna w przypadku składników zapisywania sterowników urządzeń wirtualnych (VxDs).

## <a name="what-do-you-want-to-know-more-about"></a>O czym chcesz się dowiedzieć więcej?

- [naked](../cpp/naked-cpp.md)

- [Reguły i ograniczenia dotyczące używania funkcji Naked](../cpp/rules-and-limitations-for-naked-functions.md)

- [Zagadnienia dotyczące pisania kodu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)