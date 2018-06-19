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
ms.openlocfilehash: 1da3dc6df825988794481795ca7e47e72b5736bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33367506"
---
# <a name="cevent-class"></a>Klasa CEvent
Reprezentuje zdarzenia jest obiekt synchronizacji, który umożliwia jeden wątek, aby powiadomić innego wystąpienia zdarzenia.  
  
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
|[CEvent::PulseEvent](#pulseevent)|Zestawy dostępne zdarzenia (sygnalizowane) zwalnia wątków oczekujących i ustawia zdarzenie niedostępny (nonsignaled).|  
|[CEvent::ResetEvent](#resetevent)|Ustawia zdarzenie niedostępny (nonsignaled).|  
|[CEvent::SetEvent](#setevent)|Ustawia zdarzenie dostępne (sygnałowego) i zwalnia wszystkie wątków oczekujących.|  
|[CEvent::Unlock](#unlock)|Udostępnia obiekt zdarzenia.|  
  
## <a name="remarks"></a>Uwagi  
 Zdarzenia są przydatne, gdy wątek musi wiedzieć, kiedy wykonania tego zadania. Na przykład wątku, który kopiuje dane do archiwum danych musi być powiadamiani o nowe dane są dostępne. Za pomocą `CEvent` obiektu powiadomiono wątku kopii, jeśli nowe dane są dostępne, wątek zadanie można wykonać jego tak szybko, jak to możliwe.  
  
 `CEvent` obiekty mają dwa typy: ręczna i automatyczna.  
  
 Automatyczne `CEvent` obiektu automatycznie powróci do stanu (niedostępne)-sygnalizowane po wydaniu co najmniej jeden wątek. Domyślnie `CEvent` obiektu jest automatycznie, chyba że przekazujesz `TRUE` dla `bManualReset` parametru podczas tworzenia.  
  
 Podręcznik `CEvent` obiektu pozostaje w stanie ustawione przez [SetEvent](#setevent) lub [ResetEvent](#resetevent) do momentu wywołania innych funkcji. Aby utworzyć ręcznego `CEvent` obiektów należy przekazać `TRUE` dla `bManualReset` parametru podczas tworzenia.  
  
 Aby użyć `CEvent` obiektów, utworzyć `CEvent` obiektów, kiedy to wymagane. Określ nazwę zdarzenia, które chcesz czekać na, a także określić aplikacji należy go początkowo właścicielem. Można następnie uzyskać dostępu do zdarzeń po powrocie z konstruktora. Wywołania [SetEvent](#setevent) sygnału (udostępnianie) obiektu zdarzenia, a następnie wywołania [Unlock](#unlock) po zakończeniu dostępu do kontrolowanego zasobu.  
  
 Alternatywna metoda przy użyciu `CEvent` obiektów jest dodanie do zmiennej typu `CEvent` jako element członkowski danych klasy kontroli. Podczas konstruowania obiektu kontrolowanego, należy wywołać konstruktora z `CEvent` element członkowski danych i określ, czy zdarzenie jest sygnalizowane początkowo oraz specifythe typ obiektu zdarzenia, należy nazwę zdarzenia (jeśli będzie on używany przez proces granice) lub atrybutów zabezpieczeń ma.  
  
 Do uzyskania dostępu do zasobu kontrolowane przez `CEvent` obiektów w ten sposób, najpierw Utwórz zmienną obu typów [CSingleLock](../../mfc/reference/csinglelock-class.md) lub typ [CMultiLock](../../mfc/reference/cmultilock-class.md) w metodzie dostępu do zasobu. Następnie wywołaj `Lock` metody blokady obiektu (na przykład [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). W tym momencie z wątku zostanie albo uzyskać dostęp do zasobu, poczekaj na zwolnione i uzyskać dostęp lub zaczekaj zasobów do zwolnienia zasobu, limit czasu i nie można uzyskać dostęp do zasobu. W każdym przypadku zasobu uzyskaniu w sposób wątkowo. Do zwolnienia zasobu, należy wywołać `SetEvent` sygnału obiektu zdarzenia, a następnie użyć `Unlock` metody blokady obiektu (na przykład [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), lub pozwolić, aby zablokować obiektu wykraczać poza zakresem.  
  
 Aby uzyskać więcej informacji o sposobie używania `CEvent` obiekty, zobacz [Multithreading: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
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
 `bInitiallyOwn`  
 Jeśli **TRUE**, wątku dla **CMultilock** lub `CSingleLock` obiektu jest włączone. W przeciwnym razie należy poczekać wszystkie wątki chcą uzyskać dostęp do zasobu.  
  
 *bManualReset*  
 Jeśli **TRUE**, określa, że obiekt zdarzenia jest zdarzenie ręczne, w przeciwnym razie obiekt zdarzenia jest automatyczne zdarzenia.  
  
 `lpszName`  
 Nazwa `CEvent` obiektu. Musi być dostarczona, jeśli obiekt będzie można użyć poza granicami procesu. Jeśli nazwa pasuje do zdarzenia istniejącego, konstruktora tworzy nową `CEvent` obiektu, który odwołuje się zdarzenie o tej nazwie. Jeśli nazwa jest zgodna z istniejącym obiektem synchronizacji nie jest zdarzeniem, konstrukcji zakończy się niepowodzeniem. Jeśli **NULL**, nazwa będzie miała wartość null.  
  
 `lpsaAttribute`  
 Atrybuty zabezpieczeń dla obiekt zdarzenia. Pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Dostęp, lub zwolnij `CEvent` obiektów, Utwórz [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) obiekt i wywołanie jego [blokady](../../mfc/reference/csinglelock-class.md#lock) i [Unlock](../../mfc/reference/csinglelock-class.md#unlock) Funkcje elementów członkowskich.  
  
 Aby zmienić stan `CEvent` obiektu sygnalizowane (wątków nie ma czekać), wywołaj [SetEvent](#setevent) lub [PulseEvent](#pulseevent). Można ustawić stan `CEvent` obiektu nonsignaled (wątki oczekiwania), wywołaj [ResetEvent](#resetevent).  
  
> [!IMPORTANT]
>  Po utworzeniu `CEvent` obiektów, użyj [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) aby upewnić się, że obiektu mutex nie został już istnieje. Nieoczekiwanie istniał obiektu mutex, może oznaczać nieautoryzowanego zajmowanie i procesu może zamierza użyć obiektu mutex złośliwie. W takim przypadku zalecaną procedurą zabezpieczenia jest zamknąć dojścia i kontynuować tak, jakby wystąpił błąd podczas tworzenia obiektu.  
  
##  <a name="pulseevent"></a>  CEvent::PulseEvent  
 Ustawia stan zdarzenia sygnalizuje (dostępne), zwalnia wszelkie wątków oczekujących, a ponadto resetuje go do nonsignaled (niedostępne) automatycznie.  
  
```  
BOOL PulseEvent();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku ręcznego zdarzenia są wydawane wszystkich wątków oczekujących, zdarzenie jest ustawiony na nonsignaled i `PulseEvent` zwraca. Jeśli zdarzenie jest automatyczne, zwolnieniu pojedynczego wątku, zdarzenia jest ustawiona na nonsignaled i `PulseEvent` zwraca.  
  
 Jeśli nie ma wątków oczekujących lub wątków nie może być zwolnione, `PulseEvent` ustawia stan zdarzenia do nonsignaled i zwraca.  
  
 `PulseEvent` używa podstawowej Win32 `PulseEvent` funkcji, które mogą na chwilę usunięte ze stanu oczekiwania przez wywołanie asynchroniczne procedury trybu jądra. W związku z tym `PulseEvent` jest tymczasowy i nie powinny być używane przez nowych aplikacji. Aby uzyskać więcej informacji, zobacz [funkcja PulseEvent](http://msdn.microsoft.com/library/windows/desktop/ms684914).  
  
##  <a name="resetevent"></a>  CEvent::ResetEvent  
 Ustawia stan zdarzenia, nonsignaled do momentu, jawnie ustawiona na sygnałowego przez [SetEvent](#setevent) funkcję elementu członkowskiego.  
  
```  
BOOL ResetEvent();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Powoduje to, że wszystkie wątki chcą uzyskać dostępu do tego zdarzenia oczekiwania.  
  
 Ta funkcja członkowska nie jest używany przez automatyczne zdarzenia.  
  
##  <a name="setevent"></a>  CEvent::SetEvent  
 Ustawia stan zdarzenia sygnalizuje, udostępnia wszystkie wątków oczekujących.  
  
```  
BOOL SetEvent();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie, w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku ręcznego zdarzenia zdarzenia pozostanie sygnałowego do [ResetEvent](#resetevent) jest wywoływana. W takim przypadku można można zwolnić więcej niż jeden wątek. Jeśli zdarzenie jest automatyczne, zdarzenie pozostanie sygnałowego do czasu zwolnienia jest jednego wątku. System zostanie następnie ustawioną stan zdarzenia nonsignaled. Nie wątków oczekujących, stan pozostaje sygnałowego do czasu zwolnienia jest jeden wątek.  
  
##  <a name="unlock"></a>  CEvent::Unlock  
 Udostępnia obiekt zdarzenia.  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli wątek należące do obiektu zdarzenia i zdarzenia jest automatyczne zdarzeń; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego jest wywoływana przez wątki, których aktualnie należą automatyczne zdarzenia zwolnienia go po ich zakończeniu, jeśli ich obiekt blokady jest zostanie ponownie. Jeśli obiekt blokad nie będzie można użyć ponownie, ta funkcja zostanie wywołana przez destruktor obiektu blokady.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)

