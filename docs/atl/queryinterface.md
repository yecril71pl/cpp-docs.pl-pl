---
title: QueryInterface
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, pointers
- interfaces, availability
- QueryInterface method
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
ms.openlocfilehash: 37bb7a8c7fef963f340704561e24e33cc36707f3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298639"
---
# <a name="queryinterface"></a>QueryInterface

Chociaż istnieją mechanizmy, za pomocą których obiekt może wyrazić funkcjonalność, którą zapewnia statycznie (przed utworzeniem wystąpienia), podstawowy mechanizm COM ma używać metody `IUnknown` o nazwie [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)).

Każdy interfejs pochodzi od `IUnknown`, więc każdy interfejs ma implementację `QueryInterface`. Niezależnie od implementacji ta metoda wysyła zapytanie do obiektu przy użyciu identyfikatora IID interfejsu, do którego obiekt wywołujący chce wskaźnik. Jeśli obiekt obsługuje ten interfejs, `QueryInterface` Pobiera wskaźnik do interfejsu, a także wywołuje `AddRef`. W przeciwnym razie zwraca E_NOINTERFACE kod błędu.

Należy pamiętać, że w każdej chwili należy przestrzegać reguł [zliczania odwołań](../atl/reference-counting.md) . Jeśli wywołasz `Release` na wskaźniku interfejsu, aby zmniejszyć liczbę odwołań do zera, nie należy używać tego wskaźnika ponownie. Czasami może być konieczne uzyskanie słabego odwołania do obiektu (to oznacza, że można uzyskać wskaźnik do jednego z jego interfejsów bez zwiększania liczby odwołań), ale nie jest to możliwe do wykonania przez wywołanie `QueryInterface` po którym następuje `Release`. Wskaźnik uzyskany w taki sposób jest nieprawidłowy i nie należy go używać. Jest to bardziej łatwo widoczne, gdy [_ATL_DEBUG_INTERFACES](reference/debugging-and-error-reporting-macros.md#_atl_debug_interfaces) jest zdefiniowana, więc zdefiniowanie tego makra jest przydatnym sposobem znajdowania usterek zliczania odwołań.

## <a name="see-also"></a>Zobacz także

[Wprowadzenie do modelu COM](../atl/introduction-to-com.md)<br/>
[QueryInterface: nawigowanie w obiekcie](/windows/win32/com/queryinterface--navigating-in-an-object)
