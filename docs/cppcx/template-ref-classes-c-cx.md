---
title: Szablon klasy ref (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 91e039f3154d7b459e3bde9804604218b5ce1c4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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