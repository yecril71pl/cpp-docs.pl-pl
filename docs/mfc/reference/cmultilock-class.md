---
title: Klasa CMultiLock
ms.date: 11/04/2016
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
ms.openlocfilehash: b2fe3ecf2197b8edb13e89600b16e550deff9af2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504549"
---
# <a name="cmultilock-class"></a>Klasa CMultiLock

Reprezentuje mechanizm kontroli dostępu używany do kontrolowania dostępu do zasobów w programie wielowątkowym.

## <a name="syntax"></a>Składnia

```
class CMultiLock
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMultiLock::CMultiLock](#cmultilock)|Konstruuje `CMultiLock` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMultiLock:: IsLocked](#islocked)|Określa, czy określony obiekt synchronizacji w tablicy jest zablokowany.|
|[CMultiLock::Lock](#lock)|Czeka na tablicę obiektów synchronizacji.|
|[CMultiLock::Unlock](#unlock)|Zwalnia wszystkie należące do siebie obiekty synchronizacji.|

## <a name="remarks"></a>Uwagi

`CMultiLock`nie ma klasy bazowej.

Aby użyć klas synchronizacji [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md)i [CEvent](../../mfc/reference/cevent-class.md), można utworzyć `CMultiLock` obiekt lub [CSingleLock](../../mfc/reference/csinglelock-class.md) , aby czekać i zwolnić obiekt synchronizacji. Użyj `CMultiLock` , gdy istnieje wiele obiektów, których można użyć w określonym czasie. Użyj `CSingleLock` , gdy musisz poczekać na jeden obiekt jednocześnie.

Aby użyć `CMultiLock` obiektu, najpierw Utwórz tablicę obiektów synchronizacji, na które chcesz czekać. Następnie Wywołaj `CMultiLock` konstruktora obiektu wewnątrz funkcji składowej w klasie kontrolowanego zasobu. Następnie wywołaj funkcję [blokowania](#lock) elementu członkowskiego, aby określić, czy zasób jest dostępny (sygnalizujący). Jeśli jest, Kontynuuj z pozostałą częścią funkcji składowej. Jeśli żaden zasób nie jest dostępny, poczekaj, aż upłynie określony czas, lub błąd powrotu. Po zakończeniu korzystania z zasobu wywołaj funkcję [Unlock](#unlock) , jeśli `CMultiLock` obiekt ma być używany ponownie `CMultiLock` , lub Zezwól na zniszczenie obiektu.

`CMultiLock`obiekty są najbardziej przydatne, gdy wątek zawiera dużą liczbę `CEvent` obiektów, na które może odpowiedzieć. Utwórz tablicę zawierającą wszystkie `CEvent` wskaźniki i Wywołaj `Lock`. Spowoduje to odczekanie wątku do momentu zasygnalizowania jednego ze zdarzeń.

Aby uzyskać więcej informacji na temat używania `CMultiLock` obiektów, zobacz wielowątkowość [artykułu: Jak używać klas](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)synchronizacji.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CMultiLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt. h

##  <a name="cmultilock"></a>CMultiLock::CMultiLock

Konstruuje `CMultiLock` obiekt.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parametry

*ppObjects*<br/>
Tablica wskaźników do obiektów synchronizacji, które mają być oczekiwane. Nie może mieć wartości NULL.

*dwCount*<br/>
Liczba obiektów w *ppObjects*. Musi być większa niż 0.

*bInitialLock*<br/>
Określa, czy początkowo próbować uzyskać dostęp do dowolnych podanych obiektów.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana po utworzeniu tablicy obiektów synchronizacji, które mają być oczekiwane. Jest on zazwyczaj wywoływany z wewnątrz wątku, który musi czekać na udostępnienie jednego z obiektów synchronizacji.

##  <a name="islocked"></a>CMultiLock:: IsLocked

Określa, czy określony obiekt jest Niesygnalizowane (niedostępne).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Parametry

*dwItem*<br/>
Indeks tablicy obiektów odpowiadający obiektowi, którego stan jest wysyłany do zapytania.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli określony obiekt jest zablokowany; w przeciwnym razie 0.

##  <a name="lock"></a>CMultiLock:: Lock

Wywołaj tę funkcję, aby uzyskać dostęp do co najmniej jednego zasobu kontrolowanego przez obiekty synchronizacji dostarczone do `CMultiLock` konstruktora.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Określa czas oczekiwania na udostępnienie obiektu synchronizacji (sygnalizowanego zasygnalizowaniem). Jeśli nieskończoność `Lock` , czeka na zasygnalizowanie obiektu przed zwróceniem.

*bWaitForAll*<br/>
Określa, czy wszystkie obiekty, które oczekują, muszą być sygnalizowane w tym samym czasie przed zwróceniem. W przypadku wartości `Lock` false program zwróci wartość, gdy jeden z obiektów oczekiwał na zasygnalizowanie.

*dwWakeMask*<br/>
Określa inne warunki, które mogą przerwać oczekiwania. Aby zapoznać się z pełną listą opcji dostępnych dla tego parametru, zobacz [MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Jeśli `Lock` to się nie powiedzie, zwraca wartość-1. Jeśli to się powiedzie, zwraca jedną z następujących wartości:

- Między WAIT_OBJECT_0 i WAIT_OBJECT_0 + (liczba obiektów — 1)

   Jeśli *bWaitForAll* ma wartość true, wszystkie obiekty są sygnalizowane (dostępne). Jeśli *bWaitForAll* ma wartość false, zwracana wartość-WAIT_OBJECT_0 jest indeksem w tablicy obiektów obiektu, który jest zasygnalizowani (dostępny).

- WAIT_OBJECT_0 + (liczba obiektów)

   Zdarzenie określone w *dwWakeMask* jest dostępne w kolejce wejściowej wątku.

- Między WAIT_ABANDONED_0 i WAIT_ABANDONED_0 + (liczba obiektów — 1)

   Jeśli *bWaitForAll* ma wartość true, wszystkie obiekty są sygnalizowane, a co najmniej jeden z obiektów jest porzuconym obiektem mutex. Jeśli *bWaitForAll* ma wartość false, zwracana wartość-WAIT_ABANDONED_0 jest indeksem w tablicy obiektów porzuconego obiektu mutex, który zaoczekiwał oczekiwania.

- WAIT_TIMEOUT

   Interwał limitu czasu określony w *dwTimeOut* utracił ważność bez powodzenia oczekiwania.

### <a name="remarks"></a>Uwagi

Jeśli *bWaitForAll* ma wartość true `Lock` , zwróci się pomyślnie zaraz po tym, jak tylko obiekty synchronizacji będą sygnalizowane jednocześnie. Jeśli *bWaitForAll* ma wartość false `Lock` , zwróci się zaraz po zasygnalizowaniu co najmniej jednego obiektu synchronizacji.

Jeśli `Lock` program nie może zwrócić natychmiast, odczeka przez nie więcej niż liczbę milisekund określony w parametrze *dwTimeOut* przed zwróceniem. Jeśli *dwTimeOut* jest nieskończona `Lock` , nie będzie zwracana do momentu uzyskania dostępu do obiektu lub spełnienia warunku określonego w *dwWakeMask* . W przeciwnym razie `Lock` , jeśli program mógł uzyskać obiekt synchronizacji, zostanie zwrócony pomyślnie; Jeśli nie, zostanie zwrócony błąd.

##  <a name="unlock"></a>CMultiLock:: Unlock

Zwalnia obiekt synchronizacji posiadany przez `CMultiLock`.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Liczba odwołań do zwolnienia. Musi być większa niż 0. Jeśli określona ilość spowodowałaby przekroczenie maksymalnej liczby obiektów, liczba nie zostanie zmieniona, a funkcja zwróci wartość FALSE.

*lPrevCount*<br/>
Wskazuje zmienną, która ma otrzymać poprzednią liczbę dla obiektu synchronizacji. Jeśli wartość jest równa NULL, Poprzednia liczba nie jest zwracana.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana przez `CMultiLock`destruktor.

Pierwsza `Unlock` z nich próbuje odblokować obiekt synchronizacji zarządzany przez `CMultiLock`program. Druga forma `Unlock` prób odblokowania obiektów należących `CMultiLock`do programu `CSemaphore` . Jeśli `CMultiLock` nie jest on obiektem `CSemaphore` zablokowanym, funkcja zwraca wartość false; w przeciwnym razie zwraca wartość true. *lCount* i *lpPrevCount* są dokładnie takie same, jak parametry [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock). Druga forma `Unlock` jest rzadko stosowana w sytuacjach wieloblokowanych.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
