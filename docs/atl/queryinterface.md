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
ms.openlocfilehash: 5a0f00e9ad0a94aaa96afb3031b57e1c7da703dc
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208192"
---
# <a name="queryinterface"></a>QueryInterface
Mimo że istnieją mechanizmy, według których obiekt można wyrazić funkcjonalność zapewnia statycznie (zanim zostanie on uruchomiony), podstawowe mechanizm COM jest użycie `IUnknown` metodę o nazwie [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).  
  
 Każdy interfejs jest tworzony na podstawie `IUnknown`, dzięki czemu każdy interfejs jest implementacją `QueryInterface`. Niezależnie od implementacji ta metoda wysyła zapytanie do obiektu przy użyciu identyfikatora IID interfejsu, do którego obiekt wywołujący chce wskaźnika. Jeśli obiekt obsługuje ten interfejs `QueryInterface` pobiera wskaźnik do interfejsu, podczas wywoływania również `AddRef`. W przeciwnym razie zwraca kod błędu E_NOINTERFACE.  
  
 Należy zauważyć, że należy przestrzegać [zliczanie odwołań](../atl/reference-counting.md) reguły przez cały czas. Jeśli wywołasz `Release` na wskaźnik interfejsu do liczbę odwołań do zera, nie należy używać tego wskaźnika ponownie. Może od czasu do czasu może być konieczne uzyskanie słabe odwołanie do obiektu (oznacza to, że możesz uzyskać wskaźnik do jednego z jego interfejsów bez zwiększania licznika odwołań), ale nie jest dopuszczalne, aby to zrobić, wywołując `QueryInterface` następuje `Release`. Wskaźnik uzyskane w taki sposób, jest nieprawidłowy i nie powinna być używana. To bardziej łatwo staje się jasne, kiedy [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) jest zdefiniowana, więc Definiowanie to makro jest to wygodny sposób wyszukiwania zliczanie błędów.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do modelu COM](../atl/introduction-to-com.md)   
 [QueryInterface: Nawigacja w obiekcie](/windows/desktop/com/queryinterface--navigating-in-an-object)

