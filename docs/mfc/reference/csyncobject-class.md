---
title: Klasa CSyncObject
ms.date: 11/04/2016
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
ms.openlocfilehash: ebfbc185cdca2effc96ce2e6d96d05f997c52bf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365969"
---
# <a name="csyncobject-class"></a>Klasa CSyncObject

Czysta klasa wirtualna, która zapewnia funkcje wspólne dla obiektów synchronizacji w win32.

## <a name="syntax"></a>Składnia

```
class CSyncObject : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|Konstruuje `CSyncObject` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSyncObject::Zablokuj](#lock)|Uzyskuje dostęp do obiektu synchronizacji.|
|[CSyncObject::Odblokuj](#unlock)|Uzyskuje dostęp do obiektu synchronizacji.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSyncObject::operator HANDLE](#operator_handle)|Zapewnia dostęp do obiektu synchronizacji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|Dojście do obiektu synchronizacji podstawowej.|

## <a name="remarks"></a>Uwagi

Biblioteka klas Programu Microsoft Foundation `CSyncObject`zawiera kilka klas pochodzących z programu . Są to [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)i [CSemaphore](../../mfc/reference/csemaphore-class.md).

Aby uzyskać informacje na temat używania obiektów synchronizacji, zobacz artykuł [Wielowątkowość: Jak korzystać z klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

## <a name="csyncobjectcsyncobject"></a><a name="csyncobject"></a>CSyncObject::CSyncObject

Konstruuje obiekt synchronizacji o podanej nazwie.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Parametry

*pstrName (nazwa pstrname)*<br/>
Nazwa obiektu. Jeśli null, *pstrName* będzie null.

## <a name="csyncobjectlock"></a><a name="lock"></a>CSyncObject::Zablokuj

Wywołanie tej funkcji, aby uzyskać dostęp do zasobu kontrolowanego przez obiekt synchronizacji.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Określa czas oczekiwania na udostępnienie obiektu synchronizacji (sygnalizowany). Jeśli INFINITE, `Lock` będzie czekać, aż obiekt jest sygnalizowany przed zwróceniem.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli obiekt synchronizacji jest `Lock` sygnalizowany, zwróci pomyślnie i wątek jest teraz właścicielem obiektu. Jeśli obiekt synchronizacji jest niesygnatowany (niedostępny), `Lock` będzie czekać na obiekt synchronizacji, aby stać się sygnalizowane do liczby milisekund określonych w *dwTimeOut* parametru. Jeśli obiekt synchronizacji nie został zasygnalizowany `Lock` w określonym czasie, zwraca błąd.

## <a name="csyncobjectm_hobject"></a><a name="m_hobject"></a>CSyncObject::m_hObject

Dojście do obiektu synchronizacji podstawowej.

```
HANDLE m_hObject;
```

## <a name="csyncobjectoperator-handle"></a><a name="operator_handle"></a>CSyncObject::operator HANDLE

Ten operator służy do uzyskania `CSyncObject` uchwytu obiektu.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, dojście obiektu synchronizacji; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Dojścia można używać do bezpośredniego wywoływania interfejsów API systemu Windows.

## <a name="csyncobjectunlock"></a><a name="unlock"></a>CSyncObject::Odblokuj

Deklaracja `Unlock` bez parametrów jest czystą funkcją wirtualną i musi być `CSyncObject`zastąpiona przez wszystkie klasy wynikające z .

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lLicza*<br/>
Nie jest używana domyślnie implementacji.

*lpPrevCount*<br/>
Nie jest używana domyślnie implementacji.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zawsze zwraca wartość TRUE.

### <a name="remarks"></a>Uwagi

Domyślna implementacja deklaracji z dwoma parametrami zawsze zwraca wartość TRUE. Ta funkcja jest wywoływana do zwalniania dostępu do obiektu synchronizacji należącego do wątku wywołującego. Druga deklaracja jest dostępna dla obiektów synchronizacji, takich jak semafory, które umożliwiają więcej niż jeden dostęp do kontrolowanego zasobu.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
