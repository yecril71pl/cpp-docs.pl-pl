---
title: QueryInterface | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cde92ee56e51a86acbfb7e459571291bc3cae76c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356964"
---
# <a name="queryinterface"></a>QueryInterface
Mimo że istnieją mechanizmy, które obiektu można wyrazić funkcji zapewnia statycznie (zanim zostanie on uruchomiony), podstawowe mechanizmu COM jest użycie **IUnknown** wywołano metodę [QueryInterface ](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 Każdy interfejs jest pochodną **IUnknown**, więc każdy interfejs ma implementację elementu `QueryInterface`. Niezależnie od implementacji ta metoda wysyła zapytanie do obiektu przy użyciu identyfikatora IID interfejsu, do którego element wywołujący chce wskaźnik. Jeśli obiekt obsługuje ten interfejs `QueryInterface` pobiera wskaźnik do interfejsu, podczas wywoływania również `AddRef`. W przeciwnym razie zwraca **E_NOINTERFACE** kod błędu.  
  
 Należy pamiętać, że należy przestrzegać [liczenie odwołań w](../atl/reference-counting.md) reguł przez cały czas. Jeśli należy wywołać **wersji** na wskaźnika interfejsu, aby zmniejszyć liczbę odwołania do zera, nie należy używać tego wskaźnika ponownie. Może od czasu do czasu może być konieczne uzyskanie słabe odwołanie do obiektu (oznacza to, że możesz uzyskać wskaźnik do jednego z interfejsów bez zwiększania liczba odwołań), ale nie jest dopuszczalne, aby to zrobić przez wywołanie metody `QueryInterface` następuje  **Wersja**. Wskaźnik uzyskane w taki sposób, jest nieprawidłowy i nie powinna być używana. To łatwiej stała się oczywista kiedy [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) , jest zdefiniowana, określenie to makro jest to wygodny sposób znajdowania zliczanie błędów.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do COM](../atl/introduction-to-com.md)   
 [QueryInterface: Nawigowanie w obiekcie](http://msdn.microsoft.com/library/windows/desktop/ms687230)

