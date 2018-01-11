---
title: Wprowadzenie do ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs: C++
helpviewer_keywords:
- COM objects, creating in ATL
- ATL
ms.assetid: 77f565e8-c4ec-4a80-af4b-7278fcfe5c98
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1c84074eae22e4263646abc1623ff96a374c04d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="introduction-to-atl"></a>Wprowadzenie do ATL
ATL jest biblioteki Active Template Library, zbiór C++ na podstawie szablonu klasy, z którego można łatwo utworzyć małe, szybko obiektów składnika modelu COM (Object). Ma specjalną obsługę dla klucza funkcje COM w tym: podstawowa implementacje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509), [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364), [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720), i `IDispatch`; podwójne interfejsy; interfejsy modułu wyliczającego standardowe COM; punkty połączenia; interfejsy oderwania; i formantów ActiveX.  
  
 Kod ATL może być używany do tworzenia jednowątkowych obiektów, obiekty modelu typu apartment, wątki modelu obiektów lub obiekty bezwątkowe i modelu typu apartment.  
  
 Tematy w tej sekcji obejmują:  
  
-   Jak [Biblioteka szablonów](../atl/using-a-template-library.md) różni się od standardowej biblioteki.  
  
-   Które [można i nie można wykonać za pomocą biblioteki ATL](../atl/scope-of-atl.md).  
  
-   [Zalecenia dotyczące wybierania pomiędzy ATL i MFC](../atl/recommendations-for-choosing-between-atl-and-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do modelu COM i ATL](../atl/introduction-to-com-and-atl.md)

