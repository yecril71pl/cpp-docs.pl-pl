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
ms.openlocfilehash: f377d6079017266630434ce71602a7e70e58ae21
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282308"
---
# <a name="iumsscheduler-structure"></a>Struktura IUMSScheduler

Interfejs abstrakcję harmonogram pracy, który chce ze współbieżności środowiska wykonawczego usługi Resource Manager do ręcznego go wątków (UMS) ustalonych w harmonogramie trybu użytkownika. Menedżer zasobów używa tego interfejsu do komunikacji z harmonogramów wątku UMS. `IUMSScheduler` Interfejs dziedziczy z `IScheduler` interfejsu.

## <a name="syntax"></a>Składnia

```
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Iumsscheduler::setcompletionlist —](#setcompletionlist)|Przypisuje `IUMSCompletionList` interfejsu do harmonogramu UMS wątku.|

## <a name="remarks"></a>Uwagi

Jeśli w przypadku wdrażania Niestandardowy harmonogram, który komunikuje się z usługą Resource Manager i chcesz, aby UMS wątki były przekazywane do harmonogramu zamiast zwykłych wątków Win32, należy podać implementacja `IUMSScheduler` interfejsu. Ponadto należy ustawić wartość klucza zasad harmonogramu `SchedulerKind` jako `UmsThreadDefault`. Jeśli zasady określają wątku UMS `IScheduler` interfejsu, który jest przekazywany jako parametr do [iresourcemanager::registerscheduler —](iresourcemanager-structure.md#registerscheduler) metoda musi być `IUMSScheduler` interfejsu.

Menedżer zasobów jest w stanie do ręcznego przypadku wątków UMS tylko w systemach operacyjnych, z funkcją UMS. 64-bitowych systemach operacyjnych z wersji Windows 7 lub nowszej obsługują UMS wątków. Jeśli tworzysz zasadę harmonogramu za pomocą `SchedulerKind` klucz ustawiony na wartość `UmsThreadDefault` i podstawowej platformy nie obsługuje UMS, wartość `SchedulerKind` klucz te zasady zostaną zmienione na wartość `ThreadScheduler`. Należy zawsze przeczytać ponownie tę wartość zasad przed oczekuje UMS wątków.

`IUMSScheduler` Interfejs jest jeden z punktów końcowych dwukierunkowy kanał komunikacji między harmonogramu i Menedżera zasobów. Drugi punkt końcowy jest reprezentowany przez `IResourceManager` i `ISchedulerProxy` interfejsów, które są implementowane przez Menedżera zasobów.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

**Namespace:** współbieżności

##  <a name="setcompletionlist"></a>  Iumsscheduler::setcompletionlist — metoda

Przypisuje `IUMSCompletionList` interfejsu do harmonogramu UMS wątku.

```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parametry

*pCompletionList*<br/>
Interfejs listy uzupełniania dla harmonogramu. Brak jednej liście według harmonogramu.

### <a name="remarks"></a>Uwagi

Menedżer zasobów spowoduje wywołanie tej metody w harmonogramie, określający, że chce wątków UMS po harmonogram zażądał początkowej alokacji zasobów. Harmonogram można użyć `IUMSCompletionList` interfejsu, aby określić, kiedy serwery proxy wątku UMS ma odblokowany. Jest on prawidłowy tylko dostęp do tego interfejsu z serwera proxy wątku działającego w głównym procesorze wirtualnym, przypisany do harmonogramu UMS.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[IScheduler, struktura](ischeduler-structure.md)<br/>
[IUMSCompletionList, struktura](iumscompletionlist-structure.md)<br/>
[IResourceManager, struktura](iresourcemanager-structure.md)
