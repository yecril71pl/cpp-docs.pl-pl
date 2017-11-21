---
title: "Deferrableeventargs — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27107c794dfd4987eb0519dfeaa9762f47d0417c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs — klasa
Klasy szablonów używane dla typów argumentów zdarzenia dla odroczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `TEventArgsInterface`  
 Typ interfejsu, który deklaruje argumenty dla zdarzenia opóźnieniem.  
  
 `TEventArgsClass`  
 Klasa implementująca `TEventArgsInterface`.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[DeferrableEventArgs::GetDeferral — metoda](../windows/deferrableeventargs-getdeferral-method.md)|Pobiera odwołanie do [odroczenia](http://go.microsoft.com/fwlink/?LinkId=526520) obiekt, który reprezentuje odroczonego zdarzeń.|  
|[DeferrableEventArgs::InvokeAllFinished — metoda](../windows/deferrableeventargs-invokeallfinished-method.md)|Wywołuje się, by wskazać, że przetwarzania obsługi zdarzenia odroczone jest pełny.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienia tej klasy są przekazywane do obsługi zdarzeń dla zdarzenia odłożone. Parametry szablonu reprezentuje interfejs, który definiuje szczegóły argumenty zdarzenia dla określonego typu zdarzenia odroczonego i klasy, która implementuje ten interfejs.  
  
 Klasa jest wyświetlany jako pierwszy argument funkcji programu obsługi zdarzeń dla zdarzenia odroczone. Możesz wywołać [GetDeferral](../windows/deferrableeventargs-getdeferral-method.md) metody, aby uzyskać [odroczenia](http://go.microsoft.com/fwlink/?LinkId=526520) obiektu, z którego można uzyskać wszystkie informacje o zdarzeniu opóźnieniem. Po zakończeniu obsługi zdarzeń, należy wywołać Complete obiektu opóźnienia. Następnie należy wywołać [InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md) na końcu metoda obsługi zdarzeń, zapewnia prawidłowo przesyłane ukończenia wszystkich odroczonego zdarzeń.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)