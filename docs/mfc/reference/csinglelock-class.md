---
title: Klasa CSingleLock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 063ad23a9d356af0cac6c5b9dd8903e81530d2df
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061342"
---
# <a name="csinglelock-class"></a>Klasa CSingleLock

Przedstawia mechanizm kontroli dostępu wykorzystywany w kontrolowaniu dostępu do zasobu w programie wielowątkowym.

## <a name="syntax"></a>Składnia

```
class CSingleLock
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|Konstruuje `CSingleLock` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSingleLock::IsLocked](#islocked)|Określa, jeśli obiekt jest zablokowany.|
|[CSingleLock::Lock](#lock)|W tym czasie czeka na obiekt synchronizacji.|
|[CSingleLock::Unlock](#unlock)|Zwalnia obiektu synchronizacji.|

## <a name="remarks"></a>Uwagi

`CSingleLock` nie ma klasy bazowej.

Aby można było używać klas synchronizacji [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), i [CEvent](../../mfc/reference/cevent-class.md), należy utworzyć `CSingleLock` lub [CMultiLock](../../mfc/reference/cmultilock-class.md) obiekt, aby czekać na i zwolnić obiekt synchronizacji. Użyj `CSingleLock` gdy wystarczy poczekać na jednym obiekcie w danym momencie. Użyj `CMultiLock` w przypadku wielu obiektów, których można używać w danym momencie.

Aby użyć `CSingleLock` obiektu, wywołaj jej konstruktora wewnątrz funkcji składowej klasy zasobów kontrolowany. Następnie wywołaj [IsLocked](#islocked) funkcja elementu członkowskiego, aby ustalić, czy zasób jest dostępny. Jeśli tak jest, przejdź do końca funkcji elementu członkowskiego. Jeśli zasób jest niedostępny, poczekaj, aż określony przedział czasu dla zasobu, które mogą być wprowadzane lub zwraca błąd. Po zakończeniu korzystania z zasobów albo wywołaj [Unlock](#unlock) działać, jeśli `CSingleLock` obiekt ma być ponownie używane lub zezwalać na `CSingleLock` zniszczenia obiektu.

`CSingleLock` obiekty wymagają obecności obiektu wywodzącego się z [CSyncObject](../../mfc/reference/csyncobject-class.md). Jest to zazwyczaj element członkowski danych klasy zasobów kontrolowany. Aby uzyskać więcej informacji na temat sposobu użycia `CSingleLock` obiektów, zobacz artykuł [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CSingleLock`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

##  <a name="csinglelock"></a>  CSingleLock::CSingleLock

Konstruuje `CSingleLock` obiektu.

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>Parametry

*Obiekt*<br/>
Wskazuje obiekt synchronizacji, można uzyskać dostęp. Nie może mieć wartości NULL.

*bInitialLock*<br/>
Określa, czy próby początkowo dostępu do dostarczonego obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest ogólnie jest wywoływana z funkcji elementu członkowskiego dostępu do kontrolowanego zasobu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

##  <a name="islocked"></a>  CSingleLock::IsLocked

Określa, jeśli obiekt skojarzony z `CSingleLock` obiekt jest nonsignaled (niedostępna).

```
BOOL IsLocked();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt jest zablokowany; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

##  <a name="lock"></a>  CSingleLock::Lock

Wywołaj tę funkcję, aby uzyskać dostęp do zasobów, kontrolowane przez obiekt synchronizacji dostarczony do `CSingleLock` konstruktora.

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Określa ilość czasu oczekiwania dla obiektu synchronizacji, które mają być dostępne (sygnalizowane). Jeśli jest to NIESKOŃCZONĄ, `Lock` będzie czekać do momentu zasygnalizowania obiektu przed zwróceniem.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli obiekt synchronizacji jest sygnalizowane, `Lock` zwróci się pomyślnie i Wątek jest właścicielem obiektu. Jeśli obiekt synchronizacji jest nonsignaled (niedostępna), `Lock` będzie czekać na obiekt synchronizacji zostało zasygnalizowane maksymalnie wyrażony w milisekundach czas określony w *dwTimeOut* parametru. Jeśli obiekt synchronizacji nie zasygnalizowane w określonym czasie, `Lock` zwraca błąd.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

##  <a name="unlock"></a>  CSingleLock::Unlock

Zwalnia obiekt synchronizacji własnością `CSingleLock`.

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Liczba do wydania. Musi być większa niż 0. Jeśli określona ilość spowodowałoby licznik obiektu przekroczy maksymalną, licznik nie jest zmieniany, a funkcja zwraca wartość FALSE.

*lPrevCount*<br/>
Wskazuje zmienną do odbierania liczba obiektów synchronizacji w poprzednim. Jeśli ma wartość NULL, liczba w poprzednim nie są zwracane.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana `CSingleLock`przez destruktora.

Jeśli musisz zwolnić więcej niż jeden licznik dostępu semafor, należy użyć drugiej formy `Unlock` i określ liczbę dostępów do wydania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMultiLock](../../mfc/reference/cmultilock-class.md)
