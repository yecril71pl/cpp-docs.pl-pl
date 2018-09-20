---
title: DeferrableEventArgs, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 082cae10bbd01c4c46fcfaa84bfd94ba6178bc1a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401787"
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

*TEventArgsInterface*<br/>
Typ interfejsu, który deklaruje argumenty dla zdarzenia odroczone.

*TEventArgsClass*<br/>
Klasa, która implementuje *TEventArgsInterface*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                         | Opis
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[DeferrableEventArgs::GetDeferral](#getdeferral)             | Pobiera odwołanie do [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiektu, który reprezentuje odroczonego zdarzenie.
[DeferrableEventArgs::InvokeAllFinished](#invokeallfinished) | Wywołuje się, by wskazać zakończeniu całego procesu przetwarzania do obsługi zdarzeń odroczone.

## <a name="remarks"></a>Uwagi

Wystąpienia tej klasy są przekazywane do obsługi zdarzeń dla zdarzeń z opóźnieniem. Parametry szablonu reprezentuje interfejs, który definiuje szczegóły argumentów zdarzenia dla określonego typu zdarzeń z opóźnieniem, a klasa, która implementuje ten interfejs.

Klasa jest wyświetlany jako pierwszy argument procedury obsługi zdarzeń dla zdarzenia odroczone. Możesz wywołać [GetDeferral](#getdeferral) metodę, aby uzyskać [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiektu, z którego można uzyskać wszystkie informacje o odroczonym zdarzeń. Po zakończeniu obsługi zdarzeń, należy wywołać Complete obiektu opóźnienia. Następnie należy wywołać [InvokeAllFinished](#invokeallfinished) na końcu metody obsługi zdarzeń, co zapewnia, że wykonania odroczonego wszystkie zdarzenia są przekazywane prawidłowo.

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Namespace:** Microsoft::WRL

## <a name="getdeferral"></a>DeferrableEventArgs::GetDeferral

Pobiera odwołanie do [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiektu, który reprezentuje odroczonego zdarzenie.

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```

### <a name="parameters"></a>Parametry

*wynik*<br/>
Wskaźnik, który będzie odwoływać się [odroczenia](http://go.microsoft.com/fwlink/p/?linkid=526520) obiektu po zakończeniu wywołanie.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="invokeallfinished"></a>DeferrableEventArgs::InvokeAllFinished

Wywołuje się, by wskazać zakończeniu całego procesu przetwarzania do obsługi zdarzeń odroczone.
  
```cpp
void InvokeAllFinished()  
```
  
### <a name="remarks"></a>Uwagi

Powinna wywołać tę metodę po wywołań źródła zdarzeń [invokeall —](../windows/eventsource-invokeall-method.md). Wywołanie tej metody uniemożliwia dalsze odroczenia podjęcie i wymusza procedury obsługi zakończenia wykonywania odroczenia, nie zostały wykonane.
