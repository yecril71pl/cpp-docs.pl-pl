---
title: Szablon klasy ref (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f135907a4aba473db62734f9370ee82b7113c66d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="template-ref-classes-ccx"></a>Szablon klasy ref (C + +/ CX)
Szablonów języka C++ nie są publikowane w metadanych i dlatego nie może mieć publiczną lub chronioną ułatwień dostępu w programie. W programie, można również używać standardowych szablonów języka C++ wewnętrznie Ponadto można zdefiniować klasy ref prywatnej jako szablon i jawnie specjalne szablonu klasy referencyjnej można zadeklarować jako członek prywatny w klasie ref publicznego.  
  
## <a name="authoring-ref-class-templates"></a>Tworzenie szablonów klasy ref  
 Poniższy przykład pokazuje, jak zadeklarować prywatnej klasy ref jako szablon, a także sposób zadeklarować standardowych szablonów języka C++ i jak zadeklarować ich zarówno jako elementów członkowskich w klasie ref publicznego. Należy pamiętać, że standardowych szablonów języka C++ może być specjalizowany przez typ środowiska uruchomieniowego systemu Windows, w tym przypadku Platform::String ^.  
  
 [!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]  
  
## <a name="see-also"></a>Zobacz też  
 [System typów (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)