---
title: DeferrableEventArgs — klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
ms.openlocfilehash: bae2472a75ab77f138fcee0951a6b869cc7c8e82
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372565"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs — klasa

Klasa szablonu używana dla typów argumentów zdarzeń dla odroczeń.

## <a name="syntax"></a>Składnia

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>Parametry

*TEventArgsInterface*<br/>
Typ interfejsu, który deklaruje argumenty dla zdarzenia odroczonego.

*Klasa TEventArgs*<br/>
Klasa, która implementuje *TEventArgsInterface*.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                         | Opis
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[DeferrableEventArgs::GetDeferral](#getdeferral)             | Pobiera odwołanie do [Odroczenie](/uwp/api/windows.foundation.deferral) obiektu, który reprezentuje odroczone zdarzenie.
[DeferrableEventArgs::InvokeAllFinished](#invokeallfinished) | Wywołano, aby wskazać, że wszystkie przetwarzanie do obsługi odroczonego zdarzenia jest zakończona.

## <a name="remarks"></a>Uwagi

Wystąpienia tej klasy są przekazywane do programów obsługi zdarzeń dla zdarzeń odroczonych. Parametry szablonu reprezentują interfejs, który definiuje szczegóły argumentów zdarzenia dla określonego typu zdarzenia odroczonego i klasy, która implementuje ten interfejs.

Klasa pojawia się jako pierwszy argument do obsługi zdarzeń dla odroczonego zdarzenia. Można wywołać [GetDeferral](#getdeferral) metody, aby uzyskać [Odroczenie obiektu,](/uwp/api/windows.foundation.deferral) z którego można uzyskać wszystkie informacje o odroczone zdarzenie. Po zakończeniu obsługi zdarzeń, należy wywołać Complete na Odroczenie obiektu. Następnie należy wywołać [InvokeAllFinished](#invokeallfinished) na końcu metody obsługi zdarzeń, co zapewnia, że zakończenie wszystkich odroczonych zdarzeń jest komunikowany poprawnie.

## <a name="requirements"></a>Wymagania

**Nagłówek:** event.h

**Obszar nazw:** Microsoft::WRL

## <a name="deferrableeventargsgetdeferral"></a><a name="getdeferral"></a>DeferrableEventArgs::GetDeferral

Pobiera odwołanie do [Odroczenie](/uwp/api/windows.foundation.deferral) obiektu, który reprezentuje odroczone zdarzenie.

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>Parametry

*Wynik*<br/>
Wskaźnik, który odwołuje się do [odroczenia](/uwp/api/windows.foundation.deferral) obiektu po zakończeniu wywołania.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

## <a name="deferrableeventargsinvokeallfinished"></a><a name="invokeallfinished"></a>DeferrableEventArgs::InvokeAllFinished

Wywołano, aby wskazać, że wszystkie przetwarzanie do obsługi odroczonego zdarzenia jest zakończona.

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>Uwagi

Tę metodę należy wywołać po wywołaniu źródła zdarzeń [InvokeAll](eventsource-class.md#invokeall). Wywołanie tej metody zapobiega dalsze odroczenia z podejmowane i wymusza obsługi zakończenia do wykonania, jeśli nie odroczenia zostały podjęte.
