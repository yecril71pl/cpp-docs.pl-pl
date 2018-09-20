---
title: Klasa CSyncObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5fea49ab46f55f4236194ebb811032d9351402d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430283"
---
# <a name="csyncobject-class"></a>Klasa CSyncObject

Czysty klasa wirtualnego zapewnia funkcje wspólne dla obiektów synchronizacji w systemie Win32.

## <a name="syntax"></a>Składnia

```
class CSyncObject : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|Konstruuje `CSyncObject` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSyncObject::Lock](#lock)|Uzyskuje dostęp do obiektu synchronizacji.|
|[CSyncObject::Unlock](#unlock)|Uzyskuje dostęp do obiektu synchronizacji.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSyncObject::operator UCHWYTU](#operator_handle)|Zapewnia dostęp do obiektu synchronizacji.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|Dojście do bazowego obiektu synchronizacji.|

## <a name="remarks"></a>Uwagi

Biblioteki klas Microsoft Foundation dostarcza kilka klas pochodnych `CSyncObject`. Są to [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), i [CSemaphore](../../mfc/reference/csemaphore-class.md).

Aby uzyskać informacje dotyczące sposobu używania dla obiektów synchronizacji, zobacz artykuł [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

##  <a name="csyncobject"></a>  CSyncObject::CSyncObject

Tworzy obiekt synchronizacji o podanej nazwie.

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>Parametry

*pstrName*<br/>
Nazwa obiektu. Jeśli ma wartość NULL, *pstrName* będzie miał wartość null.

##  <a name="lock"></a>  CSyncObject::Lock

Wywołaj tę funkcję, aby uzyskać dostęp do zasobów, kontrolowane przez obiekt synchronizacji.

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
Określa ilość czasu (w milisekundach) oczekiwania na obiekt synchronizacji mają być dostępne (sygnalizowane). Jeśli jest to NIESKOŃCZONĄ, `Lock` będzie czekać do momentu zasygnalizowania obiektu przed zwróceniem.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli obiekt synchronizacji jest sygnalizowane, `Lock` zwróci się pomyślnie i Wątek jest właścicielem obiektu. Jeśli obiekt synchronizacji jest nonsignaled (niedostępna), `Lock` będzie czekać na obiekt synchronizacji zostało zasygnalizowane maksymalnie wyrażony w milisekundach czas określony w *dwTimeOut* parametru. Jeśli obiekt synchronizacji nie zasygnalizowane w określonym czasie, `Lock` zwraca błąd.

##  <a name="m_hobject"></a>  CSyncObject::m_hObject

Dojście do bazowego obiektu synchronizacji.

```
HANDLE m_hObject;
```

##  <a name="operator_handle"></a>  CSyncObject::operator UCHWYTU

Użyj tego operatora, aby uzyskać dojście `CSyncObject` obiektu.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, uchwyt obiektu synchronizacji; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Dojście służy do wywoływania interfejsów API Windows bezpośrednio.

##  <a name="unlock"></a>  CSyncObject::Unlock

Deklaracja `Unlock` bez parametrów jest czysta funkcja wirtualna i musi zostać zastąpiona przez wszystkie klasy wywodzące się z `CSyncObject`.

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>Parametry

*lCount*<br/>
Nie używany przez domyślną implementację.

*lpPrevCount*<br/>
Nie używany przez domyślną implementację.

### <a name="return-value"></a>Wartość zwracana

Domyślna implementacja zawsze zwraca wartość PRAWDA.

### <a name="remarks"></a>Uwagi

Domyślna implementacja deklaracji z dwoma parametrami zawsze zwraca wartość PRAWDA. Ta funkcja jest wywoływana, aby zwolnić dostępu do obiektu synchronizacji własnością wątku wywołującego. Drugi deklaracji jest udostępniana dla synchronizacji obiektów, takich jak semaforów zezwalające na dostęp więcej niż jednego zasobu kontrolowany.

## <a name="see-also"></a>Zobacz też

[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)



