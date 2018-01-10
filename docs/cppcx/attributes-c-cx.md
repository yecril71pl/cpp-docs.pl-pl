---
title: Atrybuty (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6dcd3818d21b644211891ae4779a6b9bf5074e6b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="attributes-ccx"></a>Atrybuty (C + +/ CX)
Atrybut jest specjalnym rodzajem klasy ref, która może dołączony w nawiasach kwadratowych do typów środowiska wykonawczego systemu Windows i metody, aby określić niektórych zachowania podczas tworzenia metadanych. Kilka wstępnie zdefiniowanych atrybutów — na przykład [Windows::Foundation::Metadata::WebHostHidden](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx)— są często używane w języku C + +/ CX kodu. Ten przykład przedstawia, jak atrybut jest stosowany do klasy:  
  
 [!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]  
  
## <a name="custom-attributes"></a>Atrybuty niestandardowe  
 Istnieje również możliwość definiowania atrybutów niestandardowych. Atrybuty niestandardowe musi spełniać te reguły środowiska wykonawczego systemu Windows:  
  
-   Atrybuty niestandardowe może zawierać tylko publiczne pola.  
  
-   Pola atrybutu niestandardowego mogą być inicjowane, gdy jest stosowany atrybut do klasy.  
  
-   Pole może być jednego z następujących typów:  
  
    -   Int32 (int)  
  
    -   UInt32 (unsigned int)  
  
    -   bool  
  
    -   Platform::String ^  
  
    -   Windows::Foundation::HResult  
  
    -   Platform::type ^  
  
    -   Klasa publicznym typie wyliczeniowym (w tym wyliczenia zdefiniowanych przez użytkownika)  
  
 Kolejnym przykładzie pokazano, jak może zdefiniować atrybutu niestandardowego, a następnie zainicjować, gdy jest używany.  
  
 [!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]  
  
## <a name="see-also"></a>Zobacz też  
 [System typów (C + +/ CX)](../cppcx/type-system-c-cx.md)   
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Odwołanie do przestrzeni nazw](../cppcx/namespaces-reference-c-cx.md)