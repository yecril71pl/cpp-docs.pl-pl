---
title: DeferrableEventArgs, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8dd9452133267021effd307734b5c5cf55922720
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642305"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs — klasa
Klasa szablonu, używane dla typów argumentów zdarzenia dla odroczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
```  
  
### <a name="parameters"></a>Parametry  
 *TEventArgsInterface*  
 Typ interfejsu, który deklaruje argumenty dla zdarzenia odroczone.  
  
 *TEventArgsClass*  
 Klasa, która implementuje *TEventArgsInterface*.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[DeferrableEventArgs::GetDeferral, metoda](../windows/deferrableeventargs-getdeferral-method.md)|Pobiera odwołanie do [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiektu, który reprezentuje odroczonego zdarzenie.|  
|[DeferrableEventArgs::InvokeAllFinished, metoda](../windows/deferrableeventargs-invokeallfinished-method.md)|Wywołuje się, by wskazać zakończeniu całego procesu przetwarzania do obsługi zdarzeń odroczone.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienia tej klasy są przekazywane do obsługi zdarzeń dla zdarzeń z opóźnieniem. Parametry szablonu reprezentuje interfejs, który definiuje szczegóły argumentów zdarzenia dla określonego typu zdarzeń z opóźnieniem, a klasa, która implementuje ten interfejs.  
  
 Klasa jest wyświetlany jako pierwszy argument procedury obsługi zdarzeń dla zdarzenia odroczone. Możesz wywołać [GetDeferral](../windows/deferrableeventargs-getdeferral-method.md) metodę, aby uzyskać [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiektu, z którego można uzyskać wszystkie informacje o odroczonym zdarzeń. Po zakończeniu obsługi zdarzeń, należy wywołać Complete obiektu opóźnienia. Następnie należy wywołać [InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md) na końcu metody obsługi zdarzeń, co zapewnia, że wykonania odroczonego wszystkie zdarzenia są przekazywane prawidłowo.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)