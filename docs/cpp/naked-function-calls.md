---
title: Wywołania funkcji naked | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ca1913376ef4b1e6afc19be81ce7814ce92699c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071942"
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