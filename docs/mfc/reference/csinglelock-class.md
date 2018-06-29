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
ms.openlocfilehash: 65e969607e4017191539a0b0301b0c27ccb9f1ae
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078987"
---
# <a name="csinglelock-class"></a>Klasa CSingleLock
Reprezentuje mechanizm kontroli dostępu, używany w kontroli dostępu do zasobów w programie wielowątkowych.  
  
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
|[CSingleLock::IsLocked](#islocked)|Określa, czy obiekt jest zablokowany.|  
|[CSingleLock::Lock](#lock)|Czeka na obiekt synchronizacji.|  
|[CSingleLock::Unlock](#unlock)|Udostępnia obiekt synchronizacji.|  
  
## <a name="remarks"></a>Uwagi  
 `CSingleLock` nie ma klasy podstawowej.  
  
 Aby można było używać klas synchronizacji [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), i [CEvent](../../mfc/reference/cevent-class.md), należy utworzyć `CSingleLock` lub [CMultiLock](../../mfc/reference/cmultilock-class.md) obiektu na oczekiwanie na i zwolnij obiekt synchronizacji. Użyj `CSingleLock` po tylko należy zaczekać na jeden obiekt na raz. Użyj `CMultiLock` gdy istnieje wiele obiektów, których można używać w określonym czasie.  
  
 Aby użyć `CSingleLock` obiektów, wywołaj jego konstruktora wewnątrz funkcji członkowskiej klasy kontrolowane zasobów. Następnie wywołaj [IsLocked](#islocked) funkcji członkowskiej, aby określić, czy zasób jest dostępny. Jeśli tak jest, nadal pozostałych funkcji członkowskiej. Jeśli zasób jest niedostępny, poczekaj na określoną ilość czasu dla zasobu do zwolnienia lub zwracany błąd. Po zakończeniu korzystania z zasobów, albo wywoływać [Unlock](#unlock) działać, jeśli `CSingleLock` obiekt ma być ponownie używane, lub zezwolić `CSingleLock` obiektów, które mają zostać zniszczone.  
  
 `CSingleLock` obiekty wymagają obecności obiekt pochodzący od [CSyncObject](../../mfc/reference/csyncobject-class.md). Jest to zazwyczaj element członkowski danych klasy kontrolowany przez zasób. Aby uzyskać więcej informacji na temat sposobu użycia `CSingleLock` obiektów, zobacz artykuł [Multithreading: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
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
 *pObject*  
 Wskazuje obiektu synchronizacji, aby można było uzyskać dostęp. Nie może być **NULL**.  
  
 *bInitialLock*  
 Określa, czy początkowo próbują uzyskać dostęp dostarczonego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana z w funkcji członkowskiej dostępu do kontrolowanego zasobu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]  
  
##  <a name="islocked"></a>  CSingleLock::IsLocked  
 Określa, czy obiekt jest skojarzony z `CSingleLock` obiekt jest nonsignaled (niedostępny).  
  
```  
BOOL IsLocked();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt jest zablokowany; w przeciwnym razie 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]  
  
##  <a name="lock"></a>  CSingleLock::Lock  
 Wywołanie tej funkcji w celu uzyskania dostępu do zasobów kontrolowane przez obiekt synchronizacji dostarczony do `CSingleLock` konstruktora.  
  
```  
BOOL Lock(DWORD dwTimeOut = INFINITE);
```  
  
### <a name="parameters"></a>Parametry  
 *dwTimeOut*  
 Określa ilość czasu oczekiwania na obiekt synchronizacji mają być dostępne (sygnalizowane). Jeśli **NIESKOŃCZONE**, `Lock` będzie czekał na obiekt zostanie zasygnalizowane przed zwróceniem.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli obiekt synchronizacji jest sygnalizowane, `Lock` zwróci pomyślnie i Wątek jest właścicielem obiektu. Jeśli obiekt synchronizacji jest nonsignaled (niedostępny), `Lock` będzie oczekiwał na obiekt synchronizacji, aby stać się sygnalizowane maksymalnie wyrażony w milisekundach czas określony w *dwTimeOut* parametru. Jeśli obiekt synchronizacji stają się nie sygnalizowano w określonym czasie, `Lock` zwraca błąd.  
  
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
 *lCount*  
 Liczba operacji uzyskania dostępu do wersji. Musi być większa niż 0. Jeśli określonym spowodowałoby obiektu liczba przekroczy maksymalną, licznik nie ulega zmianie, a funkcja zwraca **FALSE**.  
  
 *lPrevCount*  
 Wskazuje zmiennej, aby odbierać liczbę poprzednich obiekt synchronizacji. Jeśli **NULL**, liczba w poprzednim nie są zwracane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana `CSingleLock`przez destruktor.  
  
 Jeśli musisz zwolnić więcej niż jeden licznik semafora dostępu, należy użyć drugiej formy `Unlock` i określ liczbę dostępów do zwolnienia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMultiLock](../../mfc/reference/cmultilock-class.md)
