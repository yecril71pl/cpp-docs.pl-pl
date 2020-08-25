---
title: Funkcje globalne obsługi zdarzeń
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: fde93415640ef7fa460bb363af4c3cb14b356061
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833455"
---
# <a name="event-handling-global-functions"></a>Funkcje globalne obsługi zdarzeń

Ta funkcja udostępnia procedurę obsługi zdarzeń.

> [!IMPORTANT]
> Funkcja wymieniona w poniższej tabeli nie może być używana w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

|Nazwa|Opis|
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Czeka na zasygnalizowanie obiektu, w tym czasie wysyła komunikaty okna zgodnie z wymaganiami.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a> AtlWaitWithMessageLoop

Czeka na obiekt, który ma być zasygnalizowany, jednocześnie wysyłając komunikaty okien w razie potrzeby.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Parametry

*hEvent*<br/>
podczas Uchwyt obiektu, dla którego ma zostać odczekanie.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli obiekt został zasygnalizowani.

### <a name="remarks"></a>Uwagi

Jest to przydatne, jeśli chcesz poczekać na zdarzenie obiektu i powiadomić go o stanie, ale Zezwalaj na wysyłanie komunikatów okna podczas oczekiwania.

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
