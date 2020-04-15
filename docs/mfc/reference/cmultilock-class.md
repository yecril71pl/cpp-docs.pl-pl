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
ms.openlocfilehash: a051c6a510c53ac0c7c0a6efd8b4b5720080b264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319710"
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
|[CMultiLock::Jest zablokowany](#islocked)|Określa, czy określony obiekt synchronizacji w tablicy jest zablokowany.|
|[CMultiLock::Blokada](#lock)|Czeka na tablicy obiektów synchronizacji.|
|[CMultiLock::Odblokuj](#unlock)|Zwalnia wszystkie posiadane obiekty synchronizacji.|

## <a name="remarks"></a>Uwagi

`CMultiLock`nie ma klasy podstawowej.

Aby użyć klas synchronizacji [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md)i [CEvent](../../mfc/reference/cevent-class.md) `CMultiLock` , można utworzyć obiekt lub [CSingleLock,](../../mfc/reference/csinglelock-class.md) aby poczekać i zwolnić obiekt synchronizacji. Użyj, `CMultiLock` gdy istnieje wiele obiektów, które można użyć w określonym czasie. Używaj, `CSingleLock` gdy trzeba tylko czekać na jeden obiekt naraz.

Aby użyć `CMultiLock` obiektu, należy najpierw utworzyć tablicę obiektów synchronizacji, na które chcesz poczekać. Następnie wywołać `CMultiLock` konstruktora obiektu wewnątrz funkcji elementu członkowskiego w klasie kontrolowanego zasobu. Następnie [wywołaj](#lock) lock funkcji elementu członkowskiego, aby ustalić, czy zasób jest dostępny (sygnalizowane). Jeśli tak jest, kontynuuj z pozostałą częścią funkcji elementu członkowskiego. Jeśli żaden zasób nie jest dostępny, poczekaj na określoną ilość czasu na zwolnienie zasobu lub błąd zwracany. Po zakończeniu korzystania z zasobu, albo [wywołać Unlock](#unlock) funkcji, jeśli `CMultiLock` obiekt `CMultiLock` ma być używany ponownie lub zezwolić na zniszczenie obiektu.

`CMultiLock`obiekty są najbardziej przydatne, gdy wątek ma dużą liczbę `CEvent` obiektów, na które może odpowiedzieć. Utwórz tablicę zawierającą `CEvent` wszystkie wskaźniki `Lock`i wywołaj . Spowoduje to, że wątek czekać, aż jedno ze zdarzeń jest sygnalizowane.

Aby uzyskać więcej informacji `CMultiLock` na temat używania obiektów, zobacz artykuł [Wielowątkowość: Jak korzystać z klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CMultiLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

## <a name="cmultilockcmultilock"></a><a name="cmultilock"></a>CMultiLock::CMultiLock

Konstruuje `CMultiLock` obiekt.

```
CMultiLock(
    CSyncObject* ppObjects [ ],
    DWORD dwCount,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parametry

*ppObiekty*<br/>
Tablica wskaźników do obiektów synchronizacji, na które należy czekać. Nie może być null.

*dwCount (licz)*<br/>
Liczba obiektów w *ppObjects*. Musi być większa niż 0.

*bInitialLock*<br/>
Określa, czy początkowo ma być podejmowana próba uzyskania dostępu do do któregokolwiek z dostarczonych obiektów.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana po utworzeniu tablicy obiektów synchronizacji, na które należy czekać. Zwykle jest wywoływana z wewnątrz wątku, który musi czekać na jeden z obiektów synchronizacji stają się dostępne.

## <a name="cmultilockislocked"></a><a name="islocked"></a>CMultiLock::Jest zablokowany

Określa, czy określony obiekt jest niepodpisany (niedostępny).

```
BOOL IsLocked(DWORD dwItem);
```

### <a name="parameters"></a>Parametry

*dwItem (np.*<br/>
Indeks w tablicy obiektów odpowiadających obiektowi, którego stan jest badany.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli określony obiekt jest zablokowany; w przeciwnym razie 0.

## <a name="cmultilocklock"></a><a name="lock"></a>CMultiLock::Blokada

Wywołanie tej funkcji, aby uzyskać dostęp do jednego lub więcej `CMultiLock` zasobów kontrolowanych przez obiekty synchronizacji dostarczone do konstruktora.

```
DWORD Lock(
    DWORD dwTimeOut = INFINITE,
    BOOL bWaitForAll = TRUE,
    DWORD dwWakeMask = 0);
```

### <a name="parameters"></a>Parametry

*dwTimeOut (Np.*<br/>
Określa czas oczekiwania na udostępnienie obiektu synchronizacji (sygnalizowane). Jeśli INFINITE, `Lock` będzie czekać, aż obiekt jest sygnalizowany przed zwróceniem.

*Bwaitforall*<br/>
Określa, czy wszystkie obiekty, na które czekały, muszą zostać zasygnalizowane w tym samym czasie przed zwróceniem. Jeśli FALSE, powróci, `Lock` gdy którykolwiek z obiektów czeka na jest sygnalizowane.

*dwWakeMask (Maseczka)*<br/>
Określa inne warunki, które mogą przerwać oczekiwania. Aby uzyskać pełną listę dostępnych opcji dla tego parametru, zobacz [MsgWaitForMultipleObjects](/windows/win32/api/winuser/nf-winuser-msgwaitformultipleobjects) w zestawie Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Jeśli `Lock` się nie powiedzie, zwraca - 1. Jeśli się powiedzie, zwraca jedną z następujących wartości:

- Od WAIT_OBJECT_0 do WAIT_OBJECT_0 + (liczba obiektów - 1)

   Jeśli *bWaitForAll* jest TRUE, wszystkie obiekty są sygnalizowane (dostępne). Jeśli *bWaitForAll* jest FALSE, zwracana wartość - WAIT_OBJECT_0 jest indeksem w tablicy obiektów obiektu, który jest sygnalizowany (dostępne).

- WAIT_OBJECT_0 + (liczba obiektów)

   Zdarzenie określone w *dwWakeMask* jest dostępne w kolejce wejściowej wątku.

- Od WAIT_ABANDONED_0 do WAIT_ABANDONED_0 + (liczba obiektów - 1)

   Jeśli *bWaitForAll* jest TRUE, wszystkie obiekty są sygnalizowane, a co najmniej jeden z obiektów jest opuszczony obiekt mutex. Jeśli *bWaitForAll* jest FALSE, zwracana wartość - WAIT_ABANDONED_0 jest indeksem w tablicy obiektów opuszczonego obiektu mutex, który spełnił oczekiwania.

- WAIT_TIMEOUT

   Interwał limitu czasu określony w *dwTimeOut* wygasł bez oczekiwania po pomyślnym.

### <a name="remarks"></a>Uwagi

Jeśli *bWaitForAll* jest `Lock` TRUE, powróci pomyślnie, jak tylko wszystkie obiekty synchronizacji stają się sygnalizowane jednocześnie. Jeśli *bWaitForAll* jest `Lock` FALSE, zwróci tak szybko, jak jeden lub więcej obiektów synchronizacji staje się sygnalizowane.

Jeśli `Lock` nie jest w stanie zwrócić natychmiast, będzie czekać na nie więcej niż liczba milisekund określony w *dwTimeOut* parametr przed zwróceniem. Jeśli *dwTimeOut* jest `Lock` INFINITE, nie powróci, dopóki dostęp do obiektu zostanie uzyskany lub warunek określony w *dwWakeMask* został spełniony. W przeciwnym `Lock` razie, jeśli był w stanie uzyskać obiekt synchronizacji, zwróci pomyślnie; jeśli nie, zwróci awarię.

## <a name="cmultilockunlock"></a><a name="unlock"></a>CMultiLock::Odblokuj

Zwalnia obiekt synchronizacji `CMultiLock`należący do obiektu .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lLicza*<br/>
Liczba odwołań do wydania. Musi być większa niż 0. Jeśli określona kwota spowodowałaby, że liczba obiektu przekroczy jego maksimum, liczba nie zostanie zmieniona, a funkcja zwraca wartość FAŁSZ.

*lPowik ł.*<br/>
Wskazuje zmienną, aby otrzymać poprzednią liczbę dla obiektu synchronizacji. Jeśli null, poprzednia liczba nie jest zwracana.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest `CMultiLock`wywoływana przez 's destruktora.

Pierwsza forma `Unlock` próbuje odblokować obiekt synchronizacji `CMultiLock`zarządzany przez program . Druga forma `Unlock` próbuje odblokować `CSemaphore` obiekty `CMultiLock`należące do . Jeśli `CMultiLock` nie jest właścicielem `CSemaphore` żadnego zablokowanego obiektu, funkcja zwraca wartość FAŁSZ; w przeciwnym razie zwraca wartość TRUE. *lCount* i *lpPrevCount* są dokładnie takie same jak parametry [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). Druga forma `Unlock` rzadko ma zastosowanie do sytuacji wielobloowych.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
