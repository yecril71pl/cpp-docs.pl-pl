---
title: QueryInterface | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: QueryInterface
dev_langs: C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b269ed51cc9a1648de7a52f9c250919c9ef4c1c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="queryinterface"></a>QueryInterface
Mimo że istnieją mechanizmy, które obiektu można wyrazić funkcji zapewnia statycznie (zanim zostanie on uruchomiony), podstawowe mechanizmu COM jest użycie **IUnknown** wywołano metodę [QueryInterface ](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 Każdy interfejs jest pochodną **IUnknown**, więc każdy interfejs ma implementację elementu `QueryInterface`. Niezależnie od implementacji ta metoda wysyła zapytanie do obiektu przy użyciu identyfikatora IID interfejsu, do którego element wywołujący chce wskaźnik. Jeśli obiekt obsługuje ten interfejs `QueryInterface` pobiera wskaźnik do interfejsu, podczas wywoływania również `AddRef`. W przeciwnym razie zwraca **E_NOINTERFACE** kod błędu.  
  
 Należy pamiętać, że należy przestrzegać [liczenie odwołań w](../atl/reference-counting.md) reguł przez cały czas. Jeśli należy wywołać **wersji** na wskaźnika interfejsu, aby zmniejszyć liczbę odwołania do zera, nie należy używać tego wskaźnika ponownie. Może od czasu do czasu może być konieczne uzyskanie słabe odwołanie do obiektu (oznacza to, że możesz uzyskać wskaźnik do jednego z interfejsów bez zwiększania liczba odwołań), ale nie jest dopuszczalne, aby to zrobić przez wywołanie metody `QueryInterface` następuje  **Wersja**. Wskaźnik uzyskane w taki sposób, jest nieprawidłowy i nie powinna być używana. To łatwiej stała się oczywista kiedy [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) , jest zdefiniowana, określenie to makro jest to wygodny sposób znajdowania zliczanie błędów.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do COM](../atl/introduction-to-com.md)   
 [QueryInterface: Nawigowanie w obiekcie](http://msdn.microsoft.com/library/windows/desktop/ms687230)

