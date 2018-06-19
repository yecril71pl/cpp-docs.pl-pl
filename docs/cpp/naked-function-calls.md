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
ms.openlocfilehash: b9d7b42f08d68af9838bf908efdbcc59a0540b91
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32419797"
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