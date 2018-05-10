---
title: EventSource::Remove — Metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Remove
dev_langs:
- C++
helpviewer_keywords:
- Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bbf0480252fca342b8a690e93f92ae14ca5e84c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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