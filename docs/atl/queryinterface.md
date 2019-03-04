---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- QueryInterface
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: a3ec3c6e0d2b534c3af49000202461a43a65dae9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261469"
---
# <a name="queryinterface"></a>QueryInterface

Mimo że istnieją mechanizmy, według których obiekt można wyrazić funkcjonalność zapewnia statycznie (zanim zostanie on uruchomiony), podstawowe mechanizm COM jest użycie `IUnknown` metodę o nazwie [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)).

Każdy interfejs jest tworzony na podstawie `IUnknown`, dzięki czemu każdy interfejs jest implementacją `QueryInterface`. Niezależnie od implementacji ta metoda wysyła zapytanie do obiektu przy użyciu identyfikatora IID interfejsu, do którego obiekt wywołujący chce wskaźnika. Jeśli obiekt obsługuje ten interfejs `QueryInterface` pobiera wskaźnik do interfejsu, podczas wywoływania również `AddRef`. W przeciwnym razie zwraca kod błędu E_NOINTERFACE.

Należy zauważyć, że należy przestrzegać [zliczanie odwołań](../atl/reference-counting.md) reguły przez cały czas. Jeśli wywołasz `Release` na wskaźnik interfejsu do liczbę odwołań do zera, nie należy używać tego wskaźnika ponownie. Może od czasu do czasu może być konieczne uzyskanie słabe odwołanie do obiektu (oznacza to, że możesz uzyskać wskaźnik do jednego z jego interfejsów bez zwiększania licznika odwołań), ale nie jest dopuszczalne, aby to zrobić, wywołując `QueryInterface` następuje `Release`. Wskaźnik uzyskane w taki sposób, jest nieprawidłowy i nie powinna być używana. To bardziej łatwo staje się jasne, kiedy [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) jest zdefiniowana, więc Definiowanie to makro jest to wygodny sposób wyszukiwania zliczanie błędów.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[QueryInterface: Nawigowanie w obiekcie](/windows/desktop/com/queryinterface--navigating-in-an-object)
