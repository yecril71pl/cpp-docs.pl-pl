---
title: Klasa CSemaphore
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: f2a05963f39393bcc73650beb44c5dbb8e5535ee
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274222"
---
# <a name="csemaphore-class"></a>Klasa CSemaphore

Obiekt klasy `CSemaphore` reprezentuje "semafor" — obiektem synchronizacji umożliwiającym ograniczonej liczbę wątków w jednym lub więcej procesach na utrzymanie dostęp do liczbę wątków, często uzyskują dostęp do określonego zasobu.

## <a name="syntax"></a>Składnia

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|Konstruuje `CSemaphore` obiektu.|

## <a name="remarks"></a>Uwagi

Semaforów są przydatne w kontrolowaniu dostępu do udostępnionego zasobu, który może obsługiwać tylko ograniczoną liczbę użytkowników. Bieżąca liczba `CSemaphore` obiekt jest liczby dodatkowych użytkowników. Jeśli licznik osiągnie zero, wszystkie podejmują próbę użycia zasobów w wartości clientauthtrustmode `CSemaphore` obiekt zostanie wstawiony do kolejki systemu i poczekaj, aż do ich, albo limit czasu lub liczba wzrośnie powyżej 0. Maksymalna liczba użytkowników, którzy mogą uzyskiwać dostęp w tym samym czasie kontrolowanego zasobów jest określana podczas tworzenia `CSemaphore` obiektu.

Aby użyć `CSemaphore` obiektów, konstruowania `CSemaphore` obiektu, kiedy jest to konieczne. Określ nazwę semafora czekać, a aplikacja początkowo powinny odpowiadać. Następnie można uzyskać dostęp semafora zwrócona konstruktora. Wywołaj [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) po zakończeniu dostęp do zasobu kontrolowany.

Alternatywna metoda przy użyciu `CSemaphore` obiektów jest dodanie do zmiennej typu `CSemaphore` jako element członkowski danych do klasy, do kontroli. Podczas konstruowania obiektu kontrolowanego, należy wywołać konstruktora `CSemaphore` element członkowski danych określający początkowej dostępu, count, dostępu maksymalnej liczby, nazwa semafora (Jeśli zostanie on użyty przez granice procesu) i żądane atrybuty zabezpieczeń.

Dostęp do zasobów w wartości clientauthtrustmode `CSemaphore` obiektów w ten sposób, najpierw Utwórz zmienną typu albo [CSingleLock](../../mfc/reference/csinglelock-class.md) lub typ [CMultiLock](../../mfc/reference/cmultilock-class.md) w funkcji składowej dostępu do zasobu. Następnie wywołaj zablokować obiektu `Lock` funkcja elementu członkowskiego (na przykład [CSingleLock::Lock](../../mfc/reference/csinglelock-class.md#lock)). W tym momencie wątek będzie albo uzyskania dostępu do zasobu, poczekaj, aż zasób zwolnione i uzyskać dostęp lub poczekaj, aż zasób, które mogą być wprowadzane i limit czasu, w których nie można uzyskać dostęp do zasobu. W każdym przypadku zasobu uzyskano dostęp w sposób bezpieczny dla wątków. Do zwolnienia zasobu, użyj obiektu blokady `Unlock` funkcja elementu członkowskiego (na przykład [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock)), lub zezwalać na obiekt blokady do wykraczać poza zakres.

Alternatywnie można utworzyć `CSemaphore` obiektu autonomiczny i do niego dostęp jawnie przed podjęciem próby dostępu do kontrolowanego zasobu. Ta metoda, podczas przejrzyste komuś czytanie kodu źródłowego, jest bardziej podatne na błędy.

Aby uzyskać więcej informacji na temat sposobu użycia `CSemaphore` obiektów, zobacz artykuł [wielowątkowość: Jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

##  <a name="csemaphore"></a>  CSemaphore::CSemaphore

Konstruuje nazwane i nienazwane `CSemaphore` obiektu.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Parametry

*lInitialCount*<br/>
Licznik użycia początkowej semaforów. Musi być większa lub równa 0 i mniejsza niż lub równa *lMaxCount*.

*lMaxCount*<br/>
Liczba maksymalne wykorzystanie semaforów. Musi być większa niż 0.

*pstrName*<br/>
Nazwa semafora. Należy podać w przypadku semafora będzie dostępna przez granice procesu. Jeśli `NULL`, obiekt zostanie bez nazwy. Jeśli nazwa pasuje do istniejącego semafor, Konstruktor tworzy nową `CSemaphore` obiektu, który odwołuje się semafora o takiej nazwie. Jeśli nazwa pasuje do istniejącego obiektu synchronizacji, który nie jest semafor, konstrukcja nie powiedzie się.

*lpsaAttributes*<br/>
Atrybuty zabezpieczeń dla obiektu semafora. Aby uzyskać pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Dostęp i zwalniania `CSemaphore` obiektu, Utwórz [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) obiektu, a następnie wywołać jej [blokady](../../mfc/reference/csinglelock-class.md#lock) i [Unlock](../../mfc/reference/csinglelock-class.md#unlock) Funkcje Członkowskie.

> [!IMPORTANT]
>  Po utworzeniu `CSemaphore` obiektu, należy użyć [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) aby upewnić się, że element mutex już nie istnieje. Jeśli element mutex istniał nieoczekiwanie, może to oznaczać, nieautoryzowany proces zajmowanie i może zamierza użyć obiektu mutex złośliwie. W tym przypadku zalecaną procedurą zabezpieczenia jest zamknąć dojścia i kontynuować tak, jakby wystąpił błąd podczas tworzenia obiektu.

## <a name="see-also"></a>Zobacz także

[Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
