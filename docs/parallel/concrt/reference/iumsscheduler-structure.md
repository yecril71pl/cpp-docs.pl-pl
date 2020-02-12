---
title: Struktura IUMSScheduler
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: 45df744a9850510006e4bf887c8ed61b000a8e5c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139995"
---
# <a name="iumsscheduler-structure"></a>Struktura IUMSScheduler

Interfejs służący do abstrakcji harmonogramu pracy, który chce, aby środowisko uruchomieniowe współbieżności Menedżer zasobów do harmonogramie wątków w trybie użytkownika (UMS). Menedżer zasobów używa tego interfejsu do komunikowania się z harmonogramami wątków UMS. Interfejs `IUMSScheduler` dziedziczy po interfejsie `IScheduler`.

## <a name="syntax"></a>Składnia

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[IUMSScheduler:: SetCompletionList —](#setcompletionlist)|Przypisuje interfejs `IUMSCompletionList` do harmonogramu wątków UMS.|

## <a name="remarks"></a>Uwagi

W przypadku wdrażania niestandardowego harmonogramu, który komunikuje się z Menedżer zasobów, i chcesz, aby wątki UMS były przekazywane do harmonogramu zamiast zwykłych wątków Win32, należy zapewnić implementację interfejsu `IUMSScheduler`. Ponadto należy ustawić wartość zasad dla klucza zasad usługi Scheduler, `SchedulerKind` ma być `UmsThreadDefault`. Jeśli zasady określają wątek UMS, interfejs `IScheduler`, który jest przesyłany jako parametr do metody [IResourceManager:: RegisterScheduler —](iresourcemanager-structure.md#registerscheduler) , musi być interfejsem `IUMSScheduler`.

Menedżer zasobów jest w stanie UMS wątki tylko w systemach operacyjnych, które mają funkcję UMS. 64-bitowe systemy operacyjne z wersją Windows 7 i nowsze obsługują wątki UMS. Jeśli utworzysz zasady harmonogramu z ustawionym kluczem `SchedulerKind` wartość `UmsThreadDefault` a bazowa platforma nie obsługuje UMS, wartość klucza `SchedulerKind` dla tych zasad zostanie zmieniona na `ThreadScheduler`wartość. Należy zawsze odczytać tę wartość zasad przed oczekiwaniem na otrzymywanie wątków UMS.

Interfejs `IUMSScheduler` jest jednym końcem dwukierunkowego kanału komunikacji między harmonogramem i Menedżer zasobów. Druga końcowa jest reprezentowana przez `IResourceManager` i `ISchedulerProxy` interfejsów, które są implementowane przez Menedżer zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

**Przestrzeń nazw:** współbieżność

## <a name="setcompletionlist"></a>IUMSScheduler:: SetCompletionList —, Metoda

Przypisuje interfejs `IUMSCompletionList` do harmonogramu wątków UMS.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parametry

*pCompletionList*<br/>
Interfejs listy uzupełniania dla harmonogramu. Istnieje jedna lista na harmonogram.

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywoła tę metodę zgodnie z harmonogramem, który określa, że chce UMS wątki, po zażądaniu przez harmonogram początkowej alokacji zasobów. Harmonogram może użyć interfejsu `IUMSCompletionList`, aby określić, kiedy serwery proxy wątków UMS zostały odblokowane. Jest on prawidłowy tylko w celu uzyskania dostępu do tego interfejsu z serwera proxy wątku działającego w katalogu głównym wirtualnego procesora przypisanego do usługi UMS Scheduler.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[PolicyElementKey —](concurrency-namespace-enums.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)<br/>
[IUMSCompletionList, struktura](iumscompletionlist-structure.md)<br/>
[IResourceManager, struktura](iresourcemanager-structure.md)
