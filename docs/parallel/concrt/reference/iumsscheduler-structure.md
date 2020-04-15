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
ms.openlocfilehash: 70954906122c048e5199a801632626d35a8e3f18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368098"
---
# <a name="iumsscheduler-structure"></a>Struktura IUMSScheduler

Interfejs do abstrakcji harmonogramu pracy, który chce Menedżera zasobów środowiska wykonawczego współbieżności do przekazania go w trybie użytkownika schedulable (UMS) wątków. Menedżer zasobów używa tego interfejsu do komunikowania się z harmonogramami wątków UMS. Interfejs `IUMSScheduler` dziedziczy z `IScheduler` interfejsu.

## <a name="syntax"></a>Składnia

```cpp
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Przypisuje `IUMSCompletionList` interfejs do harmonogramu wątków UMS.|

## <a name="remarks"></a>Uwagi

Jeśli implementujesz niestandardowy harmonogram, który komunikuje się z Menedżerem zasobów i chcesz, aby wątki usługi UMS były przekazywane do harmonogramu zamiast zwykłych wątków Systemu Win32, należy podać implementację `IUMSScheduler` interfejsu. Ponadto należy ustawić wartość zasad dla klucza `SchedulerKind` zasad `UmsThreadDefault`harmonogramu. Jeśli zasada określa wątek UMS, `IScheduler` interfejs, który jest przekazywany jako parametr do metody [IResourceManager::RegisterScheduler](iresourcemanager-structure.md#registerscheduler) musi być interfejsem. `IUMSScheduler`

Menedżer zasobów jest w stanie przekazać ci wątki UMS tylko w systemach operacyjnych, które mają funkcję UMS. 64-bitowe systemy operacyjne z wersją Windows 7 i nowszą obsługują wątki UMS. Jeśli utworzysz zasadę `SchedulerKind` harmonogramu z `UmsThreadDefault` kluczem ustawionym na wartość, a podstawowa `SchedulerKind` platforma nie obsługuje usługi UMS, wartość klucza w tej zasadie zostanie zmieniona na wartość `ThreadScheduler`. Należy zawsze odczytać tę wartość zasad przed oczekiwaniem na odbieranie wątków usługi UMS.

Interfejs `IUMSScheduler` jest jednym z końca dwukierunkowego kanału komunikacji między harmonogramem a Menedżerem zasobów. Drugi koniec jest reprezentowany `IResourceManager` `ISchedulerProxy` przez i interfejsy, które są implementowane przez Menedżera zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Ischeduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Przestrzeń nazw:** współbieżność

## <a name="iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a>IUMSScheduler::Metoda SetCompletionList

Przypisuje `IUMSCompletionList` interfejs do harmonogramu wątków UMS.

```cpp
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parametry

*pNa liście*<br/>
Interfejs listy uzupełnień dla harmonogramu. Istnieje jedna lista na harmonogram.

### <a name="remarks"></a>Uwagi

Menedżer zasobów wywoła tę metodę w harmonogramie, który określa, że chce wątków UMS, po harmonogram zażądał początkowej alokacji zasobów. Harmonogram można użyć `IUMSCompletionList` interfejsu, aby określić, kiedy serwery proxy wątku UMS zostały odblokowane. Dostęp do tego interfejsu jest prawidłowy tylko z serwera proxy wątku uruchomionego w katalogu głównym procesora wirtualnego przypisanego do harmonogramu usługi UMS.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)<br/>
[Klawiatura PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)<br/>
[IUMSCompletionList — Struktura](iumscompletionlist-structure.md)<br/>
[IResourceManager — Struktura](iresourcemanager-structure.md)
