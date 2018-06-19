---
title: DeferrableEventArgs::InvokeAllFinished — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1aaaf8c6849b30e26463810ff353234319960048
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883371"
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished — metoda
Wywołuje się, by wskazać, że przetwarzania obsługi zdarzenia odroczone jest pełny.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void InvokeAllFinished()  
```  
  
## <a name="remarks"></a>Uwagi  
 Tej metody należy wywołać po wywołań źródła zdarzeń [InvokeAll](../windows/eventsource-invokeall-method.md). Wywołanie tej metody uniemożliwia dalsze odroczenia podjęcie i wymusza programu obsługi zakończenia wykonywania odroczenia nie zostały pobrane.  
  
 Na przykład kod, zobacz [deferrableeventargs — klasa](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Deferrableeventargs — klasa](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll, metoda](../windows/eventsource-invokeall-method.md)