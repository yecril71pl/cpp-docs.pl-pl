---
title: Obsługa zdarzeń funkcje globalne
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: f2f8269dcf0f59a5d0794d3f16d4c4f85d8841ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330133"
---
# <a name="event-handling-global-functions"></a>Obsługa zdarzeń funkcje globalne

Ta funkcja zapewnia program obsługi zdarzeń.

> [!IMPORTANT]
> Funkcji wymienionej w poniższej tabeli nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

|||
|-|-|
|[AtlWaitWithMessageLoop (AtlWaitWithMessageLoop)](#atlwaitwithmessageloop)|Czeka na obiekt do sygnalizowania, w międzyczasie wysyłanie komunikatów okna w razie potrzeby.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop (AtlWaitWithMessageLoop)

Czeka na obiekt, który ma być zasygnalizowany, jednocześnie wysyłając komunikaty okien w razie potrzeby.

> [!IMPORTANT]
> Tej funkcji nie można używać w aplikacjach wykonywanych w czasie wykonywania systemu Windows.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Parametry

*hWentowiny*<br/>
[w] Dojście obiektu, na który należy czekać.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekt został zasygnalizowany.

### <a name="remarks"></a>Uwagi

Jest to przydatne, jeśli chcesz poczekać na zdarzenie obiektu się zdarzyć i otrzymywać powiadomienia o tym dzieje, ale zezwalaj na wiadomości okna, które mają być wysyłane podczas oczekiwania.

## <a name="see-also"></a>Zobacz też

[Funkcje](../../atl/reference/atl-functions.md)
