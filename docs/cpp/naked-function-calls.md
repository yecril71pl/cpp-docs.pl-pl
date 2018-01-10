---
title: "Wywołania funkcji naked | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eed53718d211ac2152978c2a4d36e6a82c5c8024
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="naked-function-calls"></a>Wywołania funkcji Naked
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Funkcje deklarowane z `naked` atrybutu są emitowane bez prolog i epilog kodu, dzięki któremu można napisać własny sekwencji niestandardowego kodu prologu/epilogu przy użyciu [asemblera wbudowanego](../assembler/inline/inline-assembler.md). Gołe funkcje są dostarczane jako funkcja zaawansowana. Można zadeklarować funkcji, która jest wywoływana w kontekście innym niż C/C++ i w związku z tym zakładają różnych gdzie parametry są lub rejestrujący zostaną zachowane. Przykładami procedury, takich jak programy obsługi przerwań. Ta funkcja jest szczególnie przydatne w przypadku zapisywania sterowniki urządzeń wirtualnych (urządzenia vxd).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [Reguły i ograniczenia dotyczące używania funkcji Naked](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [Zagadnienia dotyczące pisania kodu prologu/epilogu](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje wywoływania](../cpp/calling-conventions.md)