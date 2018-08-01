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
ms.openlocfilehash: e395bcb32858bc63b3e848f20a7d794156876e26
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402032"
---
# <a name="naked-function-calls"></a>Wywołania funkcji Naked
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Funkcje zadeklarowane za pomocą **"naked"** atrybutu są emitowane bez konieczności pisania kodu prologu i epilogu, dzięki któremu można napisać własne sekwencje niestandardowego kodu prologu/epilogu przy użyciu [asemblera wbudowanego](../assembler/inline/inline-assembler.md). Funkcje naked są dostarczane jako to zaawansowana funkcja. Umożliwiają deklarowanie funkcji, która jest wywoływana w kontekście innej niż C/C++ i dlatego zakładają różnych gdzie parametry są lub rejestrujący zostaną zachowane. Przykłady obejmują procedury, takich jak programy obsługi przerwań. Ta funkcja jest szczególnie użyteczna w przypadku autorzy sterowniki urządzeń wirtualnych (urządzenia vxd).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [Reguły i ograniczenia dotyczące używania funkcji Naked](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [Zagadnienia dotyczące pisania kodu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Konwencje wywoływania](../cpp/calling-conventions.md)