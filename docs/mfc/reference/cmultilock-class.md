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
ms.openlocfilehash: ebcfda85c82d10f2493234bb340a68129f779a28
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198115"
---
# <a name="cmultilock-class"></a>Klasa CMultiLock
Przedstawia mechanizm kontroli dostępu wykorzystywany w kontrolowaniu dostępu do zasobów w programie wielowątkowym.  
  
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
|[CMultiLock::IsLocked](#islocked)|Określa obiekt synchronizacji określone w tablicy jest zablokowany.|  
|[CMultiLock::Lock](#lock)|W tym czasie czeka na tablicę obiektów synchronizacji.|  
|[CMultiLock::Unlock](#unlock)|Zwalnia wszelkie obiektów należących do synchronizacji.|  
  
## <a name="remarks"></a>Uwagi  
 `CMultiLock` nie ma klasy bazowej.  
  
 Aby używać klas synchronizacji [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), i [CEvent](../../mfc/reference/cevent-class.md), można utworzyć `CMultiLock` lub [CSingleLock](../../mfc/reference/csinglelock-class.md)obiekt, aby czekać na i zwolnić obiekt synchronizacji. Użyj `CMultiLock` w przypadku wielu obiektów, których można używać w danym momencie. Użyj `CSingleLock` gdy wystarczy poczekać na jednym obiekcie w danym momencie.  
  
 Aby użyć `CMultiLock` obiektów, należy najpierw utworzyć tablicę obiektów synchronizacji, które chcesz czekać na. Następnie wywołaj `CMultiLock` konstruktora obiektu wewnątrz funkcji składowej klasy zasobów kontrolowany. Następnie wywołaj [blokady](#lock) funkcja elementu członkowskiego, aby ustalić, czy zasób jest dostępny (sygnalizowane). Jeśli jest, przejdź do końca funkcji elementu członkowskiego. Jeśli żaden zasób jest dostępny, poczekaj, aż określony przedział czasu dla zasobu mogą być wprowadzane lub zwraca błąd. Po zakończeniu korzystania z zasobem albo wywołaj [Unlock](#unlock) działać, jeśli `CMultiLock` obiekt ma być ponownie używane lub zezwalać na `CMultiLock` zniszczenia obiektu.  
  
 `CMultiLock` obiekty są najbardziej przydatne, gdy wątek ma dużą liczbę `CEvent` obiektów, które można odpowiedzieć. Utwórz tablicę zawierającą wszystkie `CEvent` wskaźników i wywołania `Lock`. Spowoduje to wątku do odczekania aż do jednego ze zdarzeń jest sygnalizowane.  
  
 Aby uzyskać więcej informacji na temat sposobu użycia `CMultiLock` obiektów, zobacz artykuł [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CMultiLock`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmt.h  
  
##  <a name="cmultilock"></a>  CMultiLock::CMultiLock  
 Konstruuje `CMultiLock` obiektu.  
  
```  
CMultiLock(
    CSyncObject* ppObjects [ ],  
    DWORD dwCount,  
    BOOL bInitialLock = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 *ppObjects*  
 Tablica wskaźników do obiektów synchronizacji, aby być oczekiwany. Nie może mieć wartości NULL.  
  
 *dwCount*  
 Liczba obiektów w *ppObjects*. Musi być większa niż 0.  
  
 *bInitialLock*  
 Określa, czy próby początkowo ma dostęp do wszystkich obiektów podane.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana po utworzeniu tablicy obiektów synchronizacji, aby być oczekiwany. Jest zwykle wywoływane z wewnątrz wątku, który należy poczekać jeden z obiektów synchronizacji staną się dostępne.  
  
##  <a name="islocked"></a>  CMultiLock::IsLocked  
 Określa, czy określony obiekt jest nonsignaled (niedostępna).  
  
```  
BOOL IsLocked(DWORD dwItem);
```  
  
### <a name="parameters"></a>Parametry  
 *dwItem*  
 Indeks w tablicy obiektów odpowiadającego obiektu, którego stan jest odpytywane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli określony obiekt jest zablokowany; w przeciwnym razie 0.  
  
##  <a name="lock"></a>  CMultiLock::Lock  
 Wywołaj tę funkcję, aby uzyskać dostęp do jednego lub większej liczby zasobów, w wartości clientauthtrustmode dla obiektów synchronizacji dostarczony do `CMultiLock` konstruktora.  
  
```  
DWORD Lock(
    DWORD dwTimeOut = INFINITE,  
    BOOL bWaitForAll = TRUE,  
    DWORD dwWakeMask = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *dwTimeOut*  
 Określa ilość czasu oczekiwania dla obiektu synchronizacji, które mają być dostępne (sygnalizowane). Jeśli jest to NIESKOŃCZONĄ, `Lock` będzie czekać do momentu zasygnalizowania obiektu przed zwróceniem.  
  
 *bWaitForAll*  
 Określa, czy wszystkie obiekty oczekiwany muszą zostać sygnalizowane, w tym samym czasie przed zwróceniem. W przypadku wartości FAŁSZ `Lock` zwróci, gdy jeden z obiektów, oczekiwany jest sygnalizowane.  
  
 *dwWakeMask*  
 Określa inne warunki, które mogą przerwać czas oczekiwania. Aby uzyskać pełną listę dostępnych opcji dla tego parametru zobacz [MsgWaitForMultipleObjects](/windows/desktop/api/winuser/nf-winuser-msgwaitformultipleobjects) w zestawie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli `Lock` nie powiedzie się, zwraca - 1. Jeśli to się powiedzie, zwraca jedną z następujących wartości:  
  
-   Pomiędzy WAIT_OBJECT_0 i WAIT_OBJECT_0 + (liczba obiektów - 1)  
  
     Jeśli *bWaitForAll* ma wartość TRUE, wszystkie obiekty są sygnalizowane (dostępne). Jeśli *bWaitForAll* ma wartość FALSE, zwracana wartość - WAIT_OBJECT_0 jest indeks w tablicy obiektów, obiektu, który jest sygnalizowane (dostępne).  
  
- WAIT_OBJECT_0 + (liczba obiektów)  
  
     Zdarzenie określone w *dwWakeMask* znajduje się w kolejce wejściowej wątku.  
  
-   Pomiędzy WAIT_ABANDONED_0 i WAIT_ABANDONED_0 + (liczba obiektów - 1)  
  
     Jeśli *bWaitForAll* ma wartość TRUE, wszystkie obiekty są sygnalizowane i co najmniej jeden z obiektów jest obiektem porzuconego elementu mutex. Jeśli *bWaitForAll* ma wartość FALSE, zwracana wartość - WAIT_ABANDONED_0 jest indeks w tablicy obiektów obiektu mutex porzucone, spełniającego oczekiwania.  
  
- WAIT_TIMEOUT  
  
     Interwał limitu czasu określonego w *dwTimeOut* wygasła bez pomyślnego oczekiwania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *bWaitForAll* ma wartość PRAWDA, `Lock` zwróci pomyślnie tak szybko, jak dla obiektów synchronizacji zasygnalizowane jednocześnie. Jeśli *bWaitForAll* ma wartość FAŁSZ, `Lock` zwróci tak szybko, jak sygnalizowane staje się co najmniej jeden obiekt synchronizacji.  
  
 Jeśli `Lock` nie jest w stanie do zwrócenia natychmiast, po upływie nie większą niż określona w milisekundach czas *dwTimeOut* parametru przed zwróceniem. Jeśli *dwTimeOut* są NIESKOŃCZONE, `Lock` nie będzie zwracać, dopóki nie jest uzyskali dostęp do obiektu, albo warunek określony w *dwWakeMask* została osiągnięta. W przeciwnym razie, jeśli `Lock` został można uzyskać obiektu synchronizacji, to zostanie zwrócona pomyślnie; w przeciwnym razie zwróci błąd.  
  
##  <a name="unlock"></a>  CMultiLock::Unlock  
 Zwalnia obiekt synchronizacji własnością `CMultiLock`.  
  
```  
BOOL Unlock();

 
BOOL Unlock(
    LONG lCount,  
    LPLONG lPrevCount = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lCount*  
 Zlicza liczbę odwołań do wydania. Musi być większa niż 0. Jeśli określona ilość spowodowałoby licznik obiektu przekroczy maksymalną, licznik nie jest zmieniany, a funkcja zwraca wartość FALSE.  
  
 *lPrevCount*  
 Wskazuje zmienną do odbierania liczba w poprzednim obiektu synchronizacji. Jeśli ma wartość NULL, liczba w poprzednim nie są zwracane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana `CMultiLock`przez destruktora.  
  
 Pierwszy formularz `Unlock` podejmie próbę odblokowania obiektu synchronizacji zarządza `CMultiLock`. Drugiej formy `Unlock` podejmie próbę odblokowania `CSemaphore` obiektów należących do `CMultiLock`. Jeśli `CMultiLock` nie posiada zablokowane `CSemaphore` obiektu, funkcja zwraca wartość FAŁSZ; w przeciwnym razie zwraca wartość TRUE. *lCount* i *lpPrevCount* są dokładnie takie same jak parametry [CSingleLock::Unlock](../../mfc/reference/csinglelock-class.md#unlock). Drugiej formy `Unlock` dotyczy rzadko multilock sytuacjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



