---
title: Klasa CMultiLock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiLock
- AFXMT/CMultiLock
- AFXMT/CMultiLock::CMultiLock
- AFXMT/CMultiLock::IsLocked
- AFXMT/CMultiLock::Lock
- AFXMT/CMultiLock::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CMultiLock [MFC], CMultiLock
- CMultiLock [MFC], IsLocked
- CMultiLock [MFC], Lock
- CMultiLock [MFC], Unlock
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5c5424018c3863ce64435bcc09d2d539560285e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmultilock-class"></a>Klasa CMultiLock
Reprezentuje mechanizm kontroli dostępu, używany w kontrolowania dostępu do zasobów w programie wielowątkowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMultiLock  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMultiLock::CMultiLock](#cmultilock)|Konstruuje `CMultiLock` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMultiLock::IsLocked](#islocked)|Określa, czy obiekt synchronizacji określone w tablicy jest zablokowany.|  
|[CMultiLock::Lock](#lock)|Czeka na tablicę obiektów synchronizacji.|  
|[CMultiLock::Unlock](#unlock)|Zwalnia wszelkie obiekty należących do synchronizacji.|  
  
## <a name="remarks"></a>Uwagi  
 `CMultiLock` nie ma klasy podstawowej.  
  
 Aby używać klas synchronizacji [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), i [CEvent](../../mfc/reference/cevent-class.md), można utworzyć **CMultiLock** lub [CSingleLock](../../mfc/reference/csinglelock-class.md) obiektu na oczekiwanie na i zwolnij obiekt synchronizacji. Użyj **CMultiLock** , gdy istnieje wiele obiektów, których można używać w określonym czasie. Użyj `CSingleLock` po tylko należy zaczekać na jeden obiekt na raz.  
  
 Aby użyć **CMultiLock** obiektów, najpierw Utwórz tablicę obiektów synchronizacji, które chcesz czekać na. Następnie wywołaj **CMultiLock** konstruktora obiektu wewnątrz funkcji członkowskiej klasy kontrolowane zasobów. Następnie wywołaj [blokady](#lock) funkcji członkowskiej, aby określić, czy zasób jest dostępny (sygnalizowane). Jeśli jest, nadal pozostałych funkcji członkowskiej. Jeśli żaden zasób jest dostępny, poczekaj na określoną ilość czasu dla zasobu do zwolnienia lub zwracany błąd. Po zakończeniu korzystania z zasobów, albo wywoływać [Unlock](#unlock) działać, jeśli **CMultiLock** obiekt ma być ponownie używane, lub zezwolić **CMultiLock** obiektów, które mają zostać zniszczone.  
  
 **CMultiLock** obiekty są najbardziej przydatne, gdy wątek ma dużą liczbę `CEvent` mogą odpowiadać na obiekty. Utworzyć tablicę zawierającą wszystkie `CEvent` wskaźniki i wywołania `Lock`. To spowoduje, że wątek poczekać, aż zostanie zasygnalizowane jednego zdarzenia.  
  
 Aby uzyskać więcej informacji na temat sposobu użycia **CMultiLock** obiektów, zobacz artykuł [Multithreading: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CMultiLock`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmt.h  
  
##  <a name="cmultilock"></a>  CMultiLock::CMultiLock  
 Konstruuje **CMultiLock** obiektu.  
  
```  
CMultiLock(
    CSyncObject* ppObjects [ ],  
    DWORD dwCount,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 `ppObjects`  
 Tablicy wskaźników do obiektów synchronizacji, aby być obsługiwane. Nie może być **NULL**.  
  
 `dwCount`  
 Liczba obiektów w `ppObjects`. Musi być większa niż 0.  
  
 `bInitialLock`  
 Określa, czy początkowo próbują uzyskać dostęp wszystkich obiektów dostarczony.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana po utworzeniu tablicę obiektów synchronizacji jest obsługiwane. Jest zazwyczaj wywoływana z w wątku, który musi czekać, aż jeden z obiektów synchronizacji dostępności.  
  
##  <a name="islocked"></a>  CMultiLock::IsLocked  
 Określa, czy określony obiekt jest nonsignaled (niedostępny).  
  
```  
BOOL IsLocked(DWORD dwItem);
```  
  
### <a name="parameters"></a>Parametry  
 *dwItem*  
 Indeks w tablicy obiektów odpowiadającego obiektowi stanu, którego dotyczy zapytanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli określony obiekt jest zablokowany; w przeciwnym razie 0.  
  
##  <a name="lock"></a>  CMultiLock::Lock  
 Wywołanie tej funkcji, aby uzyskać dostęp do co najmniej jeden z zasobów kontrolowane przez obiekt synchronizacji dostarczony do **CMultiLock** konstruktora.  
  
```  
DWORD Lock(
    DWORD dwTimeOut = INFINITE,  
    BOOL bWaitForAll = TRUE,  
    DWORD dwWakeMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *dwTimeOut*  
 Określa ilość czasu oczekiwania na obiekt synchronizacji mają być dostępne (sygnalizowane). Jeśli **NIESKOŃCZONE**, `Lock` będzie czekał na obiekt zostanie zasygnalizowane przed zwróceniem.  
  
 `bWaitForAll`  
 Określa, czy wszystkie obiekty oczekiwanie na musi się sygnalizowane w tym samym czasie przed zwróceniem. Jeśli **FALSE**, `Lock` zwracanie jeden z obiektów, obsługiwane jest sygnalizowane.  
  
 `dwWakeMask`  
 Określa inne warunki, które mogą przerwać czas oczekiwania. Aby uzyskać pełną listę dostępnych opcji dla tego parametru, zobacz [MsgWaitForMultipleObjects](http://msdn.microsoft.com/library/windows/desktop/ms684242) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli `Lock` nie powiedzie się, zwraca - 1. Jeśli to się powiedzie, zwraca jedną z następujących wartości:  
  
-   Między **WAIT_OBJECT_0** i **WAIT_OBJECT_0** + (liczba obiektów - 1)  
  
     Jeśli `bWaitForAll` jest **TRUE**, wszystkie obiekty są sygnalizowane (dostępny). Jeśli `bWaitForAll` jest **FALSE**, wartość zwracana - **WAIT_OBJECT_0** jest indeks w tablicy obiektów obiektu sygnalizowane (dostępny).  
  
- **WAIT_OBJECT_0** + (liczba obiektów)  
  
     Zdarzenie określone w `dwWakeMask` jest dostępna w kolejce wejściowej wątku.  
  
-   Między **WAIT_ABANDONED_0** i **WAIT_ABANDONED_0** + (liczba obiektów - 1)  
  
     Jeśli `bWaitForAll` jest **TRUE**, wszystkie obiekty są sygnalizowane i co najmniej jeden z obiektów jest obiektem porzuconego elementu mutex. Jeśli `bWaitForAll` jest **FALSE**, wartość zwracana - **WAIT_ABANDONED_0** jest indeks w tablicy obiektów obiektu porzuconego elementu mutex, który spełnia czas oczekiwania.  
  
- **WAIT_TIMEOUT**  
  
     Limit czasu określony w *dwTimeOut* ważność bez pomyślne oczekiwania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bWaitForAll` jest **TRUE**, `Lock` zwróci pomyślnie jak wszystkich obiektów synchronizacji stają się sygnalizowane jednocześnie. Jeśli `bWaitForAll` jest **FALSE**, `Lock` zwróci jak sygnalizowane staje się co najmniej jeden z obiektów synchronizacji.  
  
 Jeśli `Lock` nie będzie mógł zwrócić natychmiast, będzie czekać do nie więcej niż liczba określona w milisekundach *dwTimeOut* parametru przed zwróceniem. Jeśli *dwTimeOut* jest **NIESKOŃCZONE**, `Lock` nie zwróci aż jest uzyskuje dostęp do obiektu lub warunek określony w `dwWakeMask` została osiągnięta. W przeciwnym razie, jeśli `Lock` została można uzyskać obiektu synchronizacji, zwróci pomyślnie; w przeciwnym razie zwróci błąd.  
  
##  <a name="unlock"></a>  CMultiLock::Unlock  
 Zwalnia obiekt synchronizacji własnością `CMultiLock`.  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lCount`  
 Zlicza liczbę odwołania do zwolnienia. Musi być większa niż 0. Jeśli określonym spowodowałoby obiektu liczba przekroczy maksymalną, licznik nie ulega zmianie, a funkcja zwraca **FALSE**.  
  
 `lPrevCount`  
 Wskazuje zmiennej liczba w poprzednim dla obiekt synchronizacji. Jeśli **NULL**, liczba w poprzednim nie są zwracane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana `CMultiLock`przez destruktor.  
  
 Pierwszy formę `Unlock` podejmuje próbę odblokowania obiektu synchronizacji zarządzanego przez `CMultiLock`. Drugiej formy `Unlock` podejmuje próbę odblokowania `CSemaphore` obiektów należących do `CMultiLock`. Jeśli `CMultiLock` nie ma żadnego zablokowanym `CSemaphore` obiektu, funkcja zwraca **FALSE**; w przeciwnym razie zwraca **TRUE**. `lCount` i `lpPrevCount` są dokładnie takie same jak parametry [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). Drugiej formy `Unlock` rzadko dotyczy sytuacji multilock.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



