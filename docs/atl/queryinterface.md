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
ms.openlocfilehash: b3227ebd4767bd7639bb5e5d8d5a1c73e26079dc
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953424"
---
# <a name="queryinterface"></a>QueryInterface
Mimo że istnieją mechanizmy, według których obiekt można wyrazić funkcjonalność zapewnia statycznie (zanim zostanie on uruchomiony), podstawowe mechanizm COM jest użycie `IUnknown` metodę o nazwie [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521).  
  
 Każdy interfejs jest tworzony na podstawie `IUnknown`, dzięki czemu każdy interfejs jest implementacją `QueryInterface`. Niezależnie od implementacji ta metoda wysyła zapytanie do obiektu przy użyciu identyfikatora IID interfejsu, do którego obiekt wywołujący chce wskaźnika. Jeśli obiekt obsługuje ten interfejs `QueryInterface` pobiera wskaźnik do interfejsu, podczas wywoływania również `AddRef`. W przeciwnym razie zwraca kod błędu E_NOINTERFACE.  
  
 Należy zauważyć, że należy przestrzegać [zliczanie odwołań](../atl/reference-counting.md) reguły przez cały czas. Jeśli wywołasz `Release` na wskaźnik interfejsu do liczbę odwołań do zera, nie należy używać tego wskaźnika ponownie. Może od czasu do czasu może być konieczne uzyskanie słabe odwołanie do obiektu (oznacza to, że możesz uzyskać wskaźnik do jednego z jego interfejsów bez zwiększania licznika odwołań), ale nie jest dopuszczalne, aby to zrobić, wywołując `QueryInterface` następuje `Release`. Wskaźnik uzyskane w taki sposób, jest nieprawidłowy i nie powinna być używana. To bardziej łatwo staje się jasne, kiedy [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) jest zdefiniowana, więc Definiowanie to makro jest to wygodny sposób wyszukiwania zliczanie błędów.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do modelu COM](../atl/introduction-to-com.md)   
 [QueryInterface: Nawigacja w obiekcie](http://msdn.microsoft.com/library/windows/desktop/ms687230)

