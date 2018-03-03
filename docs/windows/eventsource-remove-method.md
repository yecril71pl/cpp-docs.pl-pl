---
title: "EventSource::Remove — Metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Remove
dev_langs:
- C++
helpviewer_keywords:
- Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a11bce6d70c70bba2a4e75753c55d83bec32329f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="eventsourceremove-method"></a>EventSource::Remove — Metoda
Usuwa reprezentowanego przez określone zdarzenie tokenu rejestracji z zestawu programów obsługi zdarzeń skojarzonych z bieżącym obiektem EventSource programu obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `token`  
 Dojście, który reprezentuje program obsługi zdarzeń. Ten token został zwrócony podczas obsługi zdarzeń został zarejestrowany przez [Add()](../windows/eventsource-add-method.md) metody.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o strukturze EventRegistrationToken zobacz temat typem Windows::Foundation:: eventregistrationtoken struktury w dokumentacji referencyjnej środowiska wykonawczego systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —
 
 ## <a name="see-also"></a>Zobacz też
 [EventSource, klasa](../windows/eventsource-class.md)