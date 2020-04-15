---
title: Klasa CSingleLock
ms.date: 11/04/2016
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
ms.openlocfilehash: 231397228d94e58665602453b5d377571e24a967
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318269"
---
# <a name="csinglelock-class"></a>Klasa CSingleLock

Reprezentuje mechanizm kontroli dostępu używany do kontrolowania dostępu do zasobu w programie wielowątkowym.

## <a name="syntax"></a>Składnia

```
class CSingleLock
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|Konstruuje `CSingleLock` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSingleLock::Jest zablokowany](#islocked)|Określa, czy obiekt jest zablokowany.|
|[CSingleLock::Blokada](#lock)|Czeka na obiekt synchronizacji.|
|[CSingleLock::Odblokuj](#unlock)|Zwalnia obiekt synchronizacji.|

## <a name="remarks"></a>Uwagi

`CSingleLock`nie ma klasy podstawowej.

Aby użyć klas synchronizacji [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)i [CEvent](../../mfc/reference/cevent-class.md) `CSingleLock` , należy utworzyć obiekt lub [CMultiLock,](../../mfc/reference/cmultilock-class.md) aby poczekać i zwolnić obiekt synchronizacji. Używaj, `CSingleLock` gdy trzeba tylko czekać na jeden obiekt naraz. Użyj, `CMultiLock` gdy istnieje wiele obiektów, które można użyć w określonym czasie.

Aby użyć `CSingleLock` obiektu, wywołać jego konstruktora wewnątrz funkcji elementu członkowskiego w klasie kontrolowanego zasobu. Następnie wywołaj funkcję elementu członkowskiego [IsLocked,](#islocked) aby ustalić, czy zasób jest dostępny. Jeśli tak, kontynuuj z pozostałą częścią funkcji elementu członkowskiego. Jeśli zasób jest niedostępny, poczekaj na określoną ilość czasu dla zasobu do zwolnienia lub zwraca błąd. Po zakończeniu korzystania z zasobu, albo [wywołać Unlock](#unlock) funkcji, jeśli `CSingleLock` obiekt `CSingleLock` ma być używany ponownie lub zezwolić na zniszczenie obiektu.

`CSingleLock`obiekty wymagają obecności obiektu pochodzącego z [CSyncObject](../../mfc/reference/csyncobject-class.md). Zazwyczaj jest to element członkowski danych klasy kontrolowanego zasobu. Aby uzyskać więcej informacji `CSingleLock` na temat używania obiektów, zobacz artykuł [Wielowątkowość: Jak korzystać z klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CSingleLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

## <a name="csinglelockcsinglelock"></a><a name="csinglelock"></a>CSingleLock::CSingleLock

Konstruuje `CSingleLock` obiekt.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parametry

*Pobject*<br/>
Wskazuje obiekt synchronizacji, do który ma zostać dozony. Nie może być null.

*bInitialLock*<br/>
Określa, czy początkowo ma być podejmowana próba uzyskania dostępu do dostarczonego obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana z funkcji elementu członkowskiego dostępu kontrolowanego zasobu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

## <a name="csinglelockislocked"></a><a name="islocked"></a>CSingleLock::Jest zablokowany

Określa, czy obiekt skojarzony `CSingleLock` z obiektem jest niepodpisany (niedostępny).

```
BOOL IsLocked();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obiekt jest zablokowany; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

## <a name="csinglelocklock"></a><a name="lock"></a>CSingleLock::Blokada

Wywołanie tej funkcji, aby uzyskać dostęp do zasobu `CSingleLock` kontrolowanego przez obiekt synchronizacji dostarczony do konstruktora.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Parametry

*dwTimeOut (Np.*<br/>
Określa czas oczekiwania na udostępnienie obiektu synchronizacji (sygnalizowane). Jeśli INFINITE, `Lock` będzie czekać, aż obiekt jest sygnalizowany przed zwróceniem.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli obiekt synchronizacji jest `Lock` sygnalizowany, zwróci pomyślnie i wątek jest teraz właścicielem obiektu. Jeśli obiekt synchronizacji jest niesygnatowany (niedostępny), `Lock` będzie czekać na obiekt synchronizacji, aby stać się sygnalizowane do liczby milisekund określonych w *dwTimeOut* parametru. Jeśli obiekt synchronizacji nie został zasygnalizowany `Lock` w określonym czasie, zwraca błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="csinglelockunlock"></a><a name="unlock"></a>CSingleLock::Odblokuj

Zwalnia obiekt synchronizacji `CSingleLock`należący do obiektu .

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lLicza*<br/>
Liczba dostępów do wydania. Musi być większa niż 0. Jeśli określona kwota spowodowałaby, że liczba obiektu przekroczy jego maksimum, liczba nie zostanie zmieniona, a funkcja zwraca wartość FAŁSZ.

*lPowik ł.*<br/>
Wskazuje zmienną, aby otrzymać poprzednią liczbę obiektu synchronizacji. Jeśli null, poprzednia liczba nie jest zwracana.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest `CSingleLock`wywoływana przez 's destruktora.

Jeśli chcesz zwolnić więcej niż jedną liczbę dostępu semafora, `Unlock` użyj drugiej formy i określ liczbę dostępów do wydania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMultiLock](../../mfc/reference/cmultilock-class.md)
