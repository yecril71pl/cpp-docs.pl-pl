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
ms.openlocfilehash: 9b49d34d7276d3c9260488f23d1821b9708d2481
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227325"
---
# <a name="naked-function-calls"></a>Wywołania funkcji Naked

**Specyficzne dla firmy Microsoft**

Funkcje zadeklarowane z **`naked`** atrybutem są emitowane bez kodu prologu lub epilogu, dzięki czemu można napisać własne niestandardowe sekwencje Prolog/epilogu przy użyciu [wbudowanego asemblera](../assembler/inline/inline-assembler.md). Funkcje wykorzystające są dostępne jako funkcja zaawansowana. Umożliwiają one zadeklarować funkcję, która jest wywoływana z kontekstu innego niż C/C++, i w ten sposób wprowadzić różne założenia dotyczące lokalizacji parametrów lub rejestrów, które są zachowywane. Przykłady obejmują procedury, takie jak programy obsługi przerwań. Ta funkcja jest szczególnie przydatna w przypadku składników zapisywania sterowników urządzeń wirtualnych (VxDs).

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [naked](../cpp/naked-cpp.md)

- [Reguły i ograniczenia dotyczące funkcji wypełniania](../cpp/rules-and-limitations-for-naked-functions.md)

- [Zagadnienia dotyczące pisania kodu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)
