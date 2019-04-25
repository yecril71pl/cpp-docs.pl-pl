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
ms.openlocfilehash: f9d8a8747d4a808d040b814005782ed8187bf274
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301581"
---
# <a name="naked-function-calls"></a>Wywołania funkcji Naked

## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft

Funkcje zadeklarowane za pomocą **"naked"** atrybutu są emitowane bez konieczności pisania kodu prologu i epilogu, dzięki któremu można napisać własne sekwencje niestandardowego kodu prologu/epilogu przy użyciu [asemblera wbudowanego](../assembler/inline/inline-assembler.md). Funkcje naked są dostarczane jako to zaawansowana funkcja. Umożliwiają deklarowanie funkcji, która jest wywoływana w kontekście innej niż C/C++ i dlatego zakładają różnych gdzie parametry są lub rejestrujący zostaną zachowane. Przykłady obejmują procedury, takich jak programy obsługi przerwań. Ta funkcja jest szczególnie użyteczna w przypadku autorzy sterowniki urządzeń wirtualnych (urządzenia vxd).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [naked](../cpp/naked-cpp.md)

- [Reguły i ograniczenia dotyczące używania funkcji Naked](../cpp/rules-and-limitations-for-naked-functions.md)

- [Zagadnienia dotyczące pisania kodu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Konwencje wywoływania](../cpp/calling-conventions.md)