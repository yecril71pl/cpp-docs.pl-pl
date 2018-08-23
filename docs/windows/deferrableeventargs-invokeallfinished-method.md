---
title: DeferrableEventArgs::InvokeAllFinished, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23d521b8373969abdd739b6e4f48eb334284664d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605176"
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished — metoda
Wywołuje się, by wskazać zakończeniu całego procesu przetwarzania do obsługi zdarzeń odroczone.
  
## <a name="syntax"></a>Składnia
  
```cpp
void InvokeAllFinished()  
```
  
## <a name="remarks"></a>Uwagi
 Powinna wywołać tę metodę po wywołań źródła zdarzeń [invokeall —](../windows/eventsource-invokeall-method.md). Wywołanie tej metody uniemożliwia dalsze odroczenia podjęcie i wymusza procedury obsługi zakończenia wykonywania odroczenia, nie zostały wykonane.
  
 Dla przykładu kodu zobacz [DeferrableEventArgs, klasa](../windows/deferrableeventargs-class.md).
  
## <a name="requirements"></a>Wymagania
 **Nagłówek:** event.h
  
 **Namespace:** Microsoft::WRL
  
## <a name="see-also"></a>Zobacz też
 [DeferrableEventArgs, klasa](../windows/deferrableeventargs-class.md)  
 [EventSource::InvokeAll, metoda](../windows/eventsource-invokeall-method.md)