---
title: Funkcje globalne obsługi zdarzeń
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: bb109c63b497420ad6e797cd8e0b366ce4dc0475
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292227"
---
# <a name="event-handling-global-functions"></a>Funkcje globalne obsługi zdarzeń

Ta funkcja udostępnia program obsługi zdarzeń.

> [!IMPORTANT]
>  Nie można użyć funkcji wymienionych w poniższej tabeli w aplikacjach korzystających ze środowiska wykonawczego Windows.

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Czeka, aż obiekt ma być zasygnalizowany, jednocześnie wysyłając komunikaty okien, zgodnie z potrzebami.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop

Czeka na obiekt, który ma być zasygnalizowany, jednocześnie wysyłając komunikaty okien w razie potrzeby.

> [!IMPORTANT]
>  Ta funkcja nie może służyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Parametry

*hEvent*<br/>
[in] Uchwyt obiektu oczekiwania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli obiekt zostały zasygnalizowane.

### <a name="remarks"></a>Uwagi

Jest to przydatne, jeśli chcesz czekać na obiekt zdarzenie, aby się zdarzyć i otrzymywać powiadomienia o wykonywane, ale zezwalaj na okna komunikatów wysyłanych podczas oczekiwania.

## <a name="see-also"></a>Zobacz także

[Funkcje](../../atl/reference/atl-functions.md)
