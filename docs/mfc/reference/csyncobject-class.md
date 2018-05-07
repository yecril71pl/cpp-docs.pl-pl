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
ms.openlocfilehash: 1712f0d26fc0d9ac3dcfb0f2a15a906351f43154
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="csyncobject-class"></a>Klasa CSyncObject
Czysty klasy wirtualnych zapewnia funkcje wspólne dla obiektów synchronizacji Win32.  
  
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
|[CSyncObject::operator dojścia](#operator_handle)|Zapewnia dostęp do obiektu synchronizacji.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSyncObject::m_hObject](#m_hobject)|Dojście do obiektu źródłowego synchronizacji.|  
  
## <a name="remarks"></a>Uwagi  
 Microsoft Foundation Class Library zawiera kilka klas pochodnych `CSyncObject`. Są to [CEvent](../../mfc/reference/cevent-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), i [CSemaphore](../../mfc/reference/csemaphore-class.md).  
  
 Aby uzyskać informacje dotyczące sposobu używania obiektów synchronizacji, zobacz artykuł [Multithreading: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
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
 `pstrName`  
 Nazwa obiektu. Jeśli **NULL**, *pstrName* będzie mieć wartość null.  
  
##  <a name="lock"></a>  CSyncObject::Lock  
 Wywołanie tej funkcji w celu uzyskania dostępu do zasobów kontrolowane przez obiekt synchronizacji.  
  
```  
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 `dwTimeout`  
 Określa ilość czasu w milisekundach czas oczekiwania na obiekt synchronizacji mają być dostępne (sygnalizowane). Jeśli **NIESKOŃCZONE**, `Lock` będzie czekał na obiekt zostanie zasygnalizowane przed zwróceniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt synchronizacji jest sygnalizowane, `Lock` zwróci pomyślnie i Wątek jest właścicielem obiektu. Jeśli obiekt synchronizacji jest nonsignaled (niedostępny), `Lock` będzie oczekiwał na obiekt synchronizacji, aby stać się sygnalizowane maksymalnie wyrażony w milisekundach czas określony w *dwTimeOut* parametru. Jeśli obiekt synchronizacji stają się nie sygnalizowano w określonym czasie, `Lock` zwraca błąd.  
  
##  <a name="m_hobject"></a>  CSyncObject::m_hObject  
 Dojście do obiektu źródłowego synchronizacji.  
  
```  
HANDLE m_hObject;  
```  
  
##  <a name="operator_handle"></a>  CSyncObject::operator dojścia  
 Użyj tego operatora, aby uzyskać dojście `CSyncObject` obiektu.  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia uchwyt obiektu synchronizacji; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Dojście służy do bezpośredniego wywoływania interfejsów API systemu Windows.  
  
##  <a name="unlock"></a>  CSyncObject::Unlock  
 Deklaracja `Unlock` bez parametrów jest czystej funkcji wirtualnej i musi zostać zastąpiona przez wszystkie klasy wywodzące się z `CSyncObject`.  
  
```  
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,  
    LPLONG lpPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lCount`  
 Nie jest używany przez domyślną implementację.  
  
 `lpPrevCount`  
 Nie jest używany przez domyślną implementację.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślna implementacja zawsze zwraca **TRUE**.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja deklaracji z dwoma parametrami zawsze zwraca **TRUE**. Ta funkcja jest wywoływana, aby zwolnić dostępu do obiektu synchronizacji posiadanych przez wątek wywołujący. Druga deklaracja jest dostępna dla obiektów synchronizacji, takich jak semaforów umożliwiających dostęp więcej niż jednego kontrolą zasobu.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



