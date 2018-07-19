---
title: Klasa CEvent | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
dev_langs:
- C++
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f31d5d04638685b6d7636f40108b7e95bbd5d37
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338828"
---
# <a name="cevent-class"></a>Klasa CEvent
Przedstawia zdarzenie, które jest obiektem synchronizacji umożliwiającym jednemu wątkowi na powiadomienie drugiego o zdarzeniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CEvent : public CSyncObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CEvent::CEvent](#cevent)|Konstruuje `CEvent` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CEvent::PulseEvent](#pulseevent)|Zestawy zdarzenia w celu dostępne (sygnalizowane) zwalnia wątków oczekujących i ustawia zdarzenie niedostępne (nonsignaled).|  
|[CEvent::ResetEvent](#resetevent)|Ustawia zdarzenie niedostępne (nonsignaled).|  
|[CEvent::SetEvent](#setevent)|Ustawia zdarzenia dostępne (sygnałowego) i zwalnia żadnych wątków oczekujących.|  
|[CEvent::Unlock](#unlock)|Zwalnia z obiektem zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Zdarzenia są przydatne, gdy wątek musi wiedzieć, kiedy trzeba wykonać swoje zadania. Na przykład wątku, który kopiuje dane do archiwum danych musi być powiadomiony, gdy nowe dane są dostępne. Za pomocą `CEvent` obiektowi powiadomić wątku Kopiuj, jeśli nowe dane są dostępne, wątek zadanie można wykonać jego tak szybko, jak to możliwe.  
  
 `CEvent` obiekty mają dwa typy: ręczne i automatyczne.  
  
 Automatyczne `CEvent` obiektu automatycznie powróci do stanu (niedostępna) zasygnalizowane po wydaniu co najmniej jeden wątek. Domyślnie `CEvent` obiekt jest automatycznie, chyba że przyjmie `TRUE` dla *bManualReset* parametru podczas konstruowania.  
  
 Podręcznik `CEvent` obiektu pozostaje w stanie ustawione przez [SetEvent](#setevent) lub [ResetEvent](#resetevent) do momentu wywołania innych funkcji. Do ręcznego utworzenia `CEvent` obiektu, przekazać `TRUE` dla `bManualReset` parametru podczas konstruowania.  
  
 Aby użyć `CEvent` obiektów, konstruowania `CEvent` obiektu, gdy jest to wymagane. Określ nazwę zdarzenia, które chcesz czekać na, a także określić aplikacji należy go początkowo właścicielem. Mogą uzyskiwać dostęp do zdarzeń, gdy Konstruktor zwraca. Wywołanie [SetEvent](#setevent) sygnału (udostępnianie) obiektu zdarzenia i następnie wywołaniu [Unlock](#unlock) po zakończeniu dostęp do zasobu kontrolowany.  
  
 Alternatywna metoda przy użyciu `CEvent` obiektów jest dodanie do zmiennej typu `CEvent` jako element członkowski danych do tej klasy, które użytkownik chce kontrolować. Podczas konstruowania obiektu kontrolowanego, należy wywołać konstruktora `CEvent` element członkowski danych i określ, czy zdarzenie jest sygnalizowane początkowo oraz specifythe typ obiektu zdarzenia, należy nazwę zdarzenia (Jeśli zostanie on użyty w całym procesie granice) oraz wszelkie atrybuty zabezpieczeń, które chcesz.  
  
 Do uzyskania dostępu do zasobu w wartości clientauthtrustmode `CEvent` obiektu w ten sposób, najpierw Utwórz zmienną typu albo [CSingleLock](../../mfc/reference/csinglelock-class.md) lub typ [CMultiLock](../../mfc/reference/cmultilock-class.md) w metodzie dostępu do zasobu. Następnie wywołaj `Lock` metody obiektu blokady (na przykład [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). W tym momencie wątek będzie albo uzyskania dostępu do zasobów, zaczekaj, aż zasób zwolnione i uzyskać dostęp lub poczekaj, aż zasobów, które mogą być wprowadzane, limit czasu i nie można uzyskać dostęp do zasobu. W każdym przypadku zasobu uzyskano dostęp w sposób bezpieczny dla wątków. Do zwolnienia zasobu, należy wywołać `SetEvent` zasygnalizowania obiektu zdarzenia, a następnie użyć `Unlock` metody obiektu blokady (na przykład [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), lub pozwól, aby zablokować obiektu wykraczać poza zakres.  
  
 Aby uzyskać więcej informacji o sposobie używania `CEvent` obiekty, zobacz [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmt.h  
  
##  <a name="cevent"></a>  CEvent::CEvent  
 Konstruuje nazwane i nienazwane `CEvent` obiektu.  
  
```  
CEvent(
    BOOL bInitiallyOwn = FALSE,  
    BOOL bManualReset = FALSE,  
    LPCTSTR lpszName = NULL,  
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *bInitiallyOwn*  
 W przypadku opcji TRUE wątku dla `CMultilock` lub `CSingleLock` obiektu jest włączona. W przeciwnym razie oczekiwania przez wszystkie wątki, które chcą uzyskać dostęp do zasobu.  
  
 *bManualReset*  
 W przypadku opcji TRUE Określa, czy obiekt zdarzenia jest zdarzenie ręczne, w przeciwnym razie z obiektem zdarzenia to zdarzenie automatycznej.  
  
 *lpszName*  
 Nazwa `CEvent` obiektu. Należy podać, jeśli obiekt ma być używany przez granice procesu. Jeśli nazwa pasuje do istniejącego zdarzenia, Konstruktor tworzy nową `CEvent` obiektu, który odwołuje się zdarzenie o takiej nazwie. Jeśli nazwa jest zgodna z istniejącym obiektem synchronizacji nie jest zdarzeniem, konstrukcja nie powiedzie się. Jeśli ma wartość NULL, nazwa będzie mieć wartości null.  
  
 *lpsaAttribute*  
 Atrybuty zabezpieczeń dla obiektu zdarzenia. Aby uzyskać pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Dostęp i zwalniania `CEvent` obiektu, Utwórz [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) obiektu, a następnie wywołać jej [blokady](../../mfc/reference/csinglelock-class.md#lock) i [Unlock](../../mfc/reference/csinglelock-class.md#unlock) Funkcje Członkowskie.  
  
 Aby zmienić stan `CEvent` obiektu sygnalizowane (wątków musi czekać), wywołania [SetEvent](#setevent) lub [PulseEvent](#pulseevent). Można ustawić stanu `CEvent` obiektu nonsignaled (wątków musi czekać), wywołaj [ResetEvent](#resetevent).  
  
> [!IMPORTANT]
>  Po utworzeniu `CEvent` obiektu, należy użyć [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) aby upewnić się, że element mutex nie istnieje. Jeśli element mutex istniał nieoczekiwanie, może to oznaczać, nieautoryzowany proces zajmowanie i może zamierza użyć obiektu mutex złośliwie. W tym przypadku zalecaną procedurą zabezpieczenia jest zamknąć dojścia i kontynuować tak, jakby wystąpił błąd podczas tworzenia obiektu.  
  
##  <a name="pulseevent"></a>  CEvent::PulseEvent  
 Ustawia stan zdarzenia w celu sygnalizowane (dostępne), zwalnia żadnych wątków oczekujących i resetuje ją do nonsignaled (niedostępna) automatycznie.  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli zdarzenie dotyczy ręcznej, wszystkie wątki oczekiwania są zwalniane, zdarzenie jest ustawione na nonsignaled i `PulseEvent` zwraca. Jeśli zdarzenie jest automatyczne, pojedynczy wątek jest zwalniany, zdarzenie jest ustawione na nonsignaled i `PulseEvent` zwraca.  
  
 Jeśli żadne wątki oczekują lub żadne wątki nie może być zwolnione natychmiast, `PulseEvent` ustawia stan zdarzenia w celu nonsignaled i zwraca.  
  
 `PulseEvent` używa podstawowej Win32 `PulseEvent` funkcji, która może chwilowo usunięte ze stanu oczekiwania przez wywołanie asynchroniczne procedury trybu jądra. W związku z tym `PulseEvent` jest zawodne i nie powinny być używane przez nowych aplikacji. Aby uzyskać więcej informacji, zobacz [funkcja PulseEvent](http://msdn.microsoft.com/library/windows/desktop/ms684914).  
  
##  <a name="resetevent"></a>  CEvent::ResetEvent  
 Ustawia stan zdarzenia w celu, nonsignaled do momentu, jawnie ustawione do sygnalizowanego przez [SetEvent](#setevent) funkcja elementu członkowskiego.  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 To powoduje, że wszystkie wątki, które chcą dostęp do tego zdarzenia oczekiwania.  
  
 Ta funkcja elementu członkowskiego nie jest używany przez automatyczne zdarzenia.  
  
##  <a name="setevent"></a>  CEvent::SetEvent  
 Ustawia stan zdarzenia w celu sygnalizowane, zwalniając żadnych wątków oczekujących.  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie, w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli zdarzenie jest ręczne, zdarzenia będą nadal sygnałowego aż do [ResetEvent](#resetevent) jest wywoływana. W takim przypadku może być zwolnione więcej niż jeden wątek. Jeśli zdarzenie jest automatyczne, zdarzenia będą nadal sygnałowego aż zwolnieniu jednego wątku. System będzie następnie ustaw stan zdarzenia nonsignaled. Żadne wątki oczekujące, stan pozostaje sygnałowego aż do chwili zwolnienia jest jeden wątek.  
  
##  <a name="unlock"></a>  CEvent::Unlock  
 Zwalnia z obiektem zdarzenia.  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli wątek należące do obiektu zdarzenia i zdarzenia to zdarzenie automatyczne; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest wywoływana przez wątki, które obecnie właścicielem zdarzenie automatyczne zwolnienie go po są wykonywane tylko, jeśli ich blokady obiektu ma być ponownie używane. Jeśli obiekt blokady nie będzie można użyć ponownie, ta funkcja zostanie wywołana przez destruktora obiektu blokady.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)

