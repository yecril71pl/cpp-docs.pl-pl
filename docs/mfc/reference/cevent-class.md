---
title: Klasa CEvent
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: fbf2d834163199107aae44bd5723ceff79e36f91
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506689"
---
# <a name="cevent-class"></a>Klasa CEvent

Reprezentuje zdarzenie, które jest obiektem synchronizacji umożliwiającym jednemu wątkowi powiadamianie innego o wystąpieniu zdarzenia.

## <a name="syntax"></a>Składnia

```
class CEvent : public CSyncObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEvent::CEvent](#cevent)|Konstruuje `CEvent` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CEvent::P ulseEvent](#pulseevent)|Ustawia dostępne zdarzenie (sygnalizowane), zwalnia oczekujące wątki i ustawia zdarzenie jako niedostępne (Niesygnalizowane).|
|[CEvent::ResetEvent](#resetevent)|Ustawia zdarzenie jako niedostępne (Niesygnalizowane).|
|[CEvent:: SetEvent](#setevent)|Ustawia dostępne dla zdarzenia (sygnalizowane) i zwalnia wszystkie oczekujące wątki.|
|[CEvent:: Unlock](#unlock)|Zwalnia obiekt zdarzenia.|

## <a name="remarks"></a>Uwagi

Zdarzenia są przydatne, gdy wątek musi wiedzieć, kiedy należy wykonać jego zadanie. Na przykład wątek, który kopiuje dane do archiwum danych, musi zostać powiadomiony, gdy dostępne są nowe dane. Za pomocą `CEvent` obiektu do powiadomienia wątku kopiowania, gdy nowe dane są dostępne, wątek może wykonać zadanie tak szybko, jak to możliwe.

`CEvent`obiekty mają dwa typy: ręczne i automatyczne.

Automatyczny `CEvent` obiekt automatycznie powraca do stanu niesygnalizowanego (niedostępny) po wydaniu co najmniej jednego wątku. Domyślnie `CEvent` obiekt jest automatycznie, o ile nie zostanie przekazany `TRUE` parametr *bManualReset* podczas konstruowania.

Obiekt ręczny `CEvent` pozostaje w stanie ustawionym przez [SetEvent](#setevent) lub [ResetEvent](#resetevent) do momentu wywołania innej funkcji. Aby utworzyć obiekt ręczny `CEvent` , należy przekazać `TRUE` `bManualReset` parametr podczas konstruowania.

Aby użyć `CEvent` obiektu, `CEvent` Konstruuj obiekt, gdy jest to wymagane. Określ nazwę zdarzenia, na które chcesz czekać, a także określ, że Twoja aplikacja powinna początkowo być jej własnością. Następnie można uzyskać dostęp do zdarzenia, gdy Konstruktor zwróci wartość. Wywołaj metodę [SetEvent](#setevent) do Signal (Udostępnij) obiekt zdarzenia, a następnie Wywołaj metodę [Unlock](#unlock) po zakończeniu uzyskiwania dostępu do kontrolowanego zasobu.

Alternatywną metodą używania `CEvent` obiektów jest dodanie zmiennej typu `CEvent` jako elementu członkowskiego danych do klasy, którą chcesz kontrolować. Podczas konstruowania kontrolowanego obiektu Wywołaj konstruktora `CEvent` elementu członkowskiego danych i określ, czy zdarzenie jest początkowo sygnalizowane, a także specifythe typ obiektu zdarzenia, nazwę zdarzenia (jeśli będzie używana między procesami granice) i wszystkie atrybuty zabezpieczeń, które chcesz.

Aby uzyskać dostęp do zasobu kontrolowanego `CEvent` przez obiekt w ten sposób, należy najpierw utworzyć zmienną typu [CSingleLock](../../mfc/reference/csinglelock-class.md) lub [CMultiLock](../../mfc/reference/cmultilock-class.md) w metodzie dostępu do zasobu. Następnie Wywołaj `Lock` metodę obiektu Lock (na przykład [CMultiLock:: Lock](../../mfc/reference/cmultilock-class.md#lock)). W tym momencie wątek uzyska dostęp do zasobu, poczeka na zwolnienie zasobu i uzyskanie dostępu albo poczeka na zwolnienie zasobu, przekroczenie limitu czasu i uzyskanie dostępu do zasobu. W każdym przypadku do zasobu uzyskano dostęp w sposób bezpieczny dla wątków. Aby zwolnić zasób, wywołaj `SetEvent` polecenie sygnalizujące obiekt zdarzenia, a następnie `Unlock` Użyj metody obiektu Lock (na przykład [CMultiLock:: Unlock](../../mfc/reference/cmultilock-class.md#unlock)) lub pozwól, że obiekt blokady wykracza poza zakres.

Aby uzyskać więcej informacji o sposobach `CEvent` korzystania z obiektów [, zobacz wielowątkowość: Jak używać klas](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)synchronizacji.

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt. h

##  <a name="cevent"></a>CEvent::CEvent

Konstruuje `CEvent` obiekt nazwany lub nienazwany.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bInitiallyOwn*<br/>
W przypadku wartości true wątek dla `CMultilock` obiektu lub `CSingleLock` jest włączony. W przeciwnym razie wszystkie wątki, do których chce uzyskać dostęp do zasobu, muszą czekać.

*bManualReset*<br/>
Jeśli wartość jest równa TRUE, określa, że obiekt zdarzenia jest zdarzeniem ręcznym, w przeciwnym razie obiekt zdarzenia jest zdarzeniem automatycznym.

*lpszName*<br/>
`CEvent` Nazwa obiektu. Należy podać, jeśli obiekt będzie używany między granicami procesu. Jeśli nazwa jest zgodna z istniejącym zdarzeniem, Konstruktor kompiluje `CEvent` nowy obiekt, który odwołuje się do zdarzenia o tej nazwie. Jeśli nazwa jest zgodna z istniejącym obiektem synchronizacji, który nie jest zdarzeniem, konstrukcja zakończy się niepowodzeniem. Jeśli wartość jest równa NULL, nazwa będzie równa null.

*lpsaAttribute*<br/>
Atrybuty zabezpieczeń dla obiektu zdarzenia. Aby uzyskać pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) w Windows SDK.

### <a name="remarks"></a>Uwagi

Aby `CEvent` uzyskać dostęp do obiektu, Utwórz obiekt [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) , a następnie Wywołaj funkcje [blokady](../../mfc/reference/csinglelock-class.md#lock) i [odblokowywania](../../mfc/reference/csinglelock-class.md#unlock) elementów członkowskich.

Aby zmienić stan `CEvent` obiektu na zasygnalizowanie (wątki nie muszą czekać), wywołaj metodę setevents lub [PulseEvent](#pulseevent). [](#setevent) Aby ustawić stan `CEvent` obiektu na Niesygnalizowane (wątki muszą oczekiwać), wywołaj [ResetEvent](#resetevent).

> [!IMPORTANT]
>  Po utworzeniu `CEvent` obiektu Użyj [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby upewnić się, że mutex nie istnieje. Jeśli obiekt mutex wystąpił nieoczekiwanie, może to oznaczać, że nieautoryzowany proces jest squatting i może zależeć od złośliwego użycia obiektu mutex. W takim przypadku zalecaną procedurę świadomego zabezpieczenia jest zamknięcie uchwytu i kontynuowanie tak, jakby Wystąpił błąd podczas tworzenia obiektu.

##  <a name="pulseevent"></a>CEvent::P ulseEvent

Ustawia stan zdarzenia do sygnalizowania (dostępny), zwalnia wszystkie oczekujące wątki i resetuje go do niesygnalizowanego (niedostępne).

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli zdarzenie jest ręczne, wszystkie oczekujące wątki są wydane, zdarzenie jest ustawione na Niesygnalizowane i `PulseEvent` zwraca. Jeśli zdarzenie jest automatyczne, zostanie wydane pojedyncze wątku, zdarzenie jest ustawione na Niesygnalizowane i `PulseEvent` zwraca wartość.

Jeśli żadne wątki nie oczekują lub nie można zwolnić wątków natychmiast, `PulseEvent` ustawia stan zdarzenia na Niesygnalizowane i zwraca wartość.

`PulseEvent`używa podstawowej funkcji Win32 `PulseEvent` , która może zostać chwilowo usunięta ze stanu oczekiwania przez asynchroniczne wywołanie procedury w trybie jądra. W `PulseEvent` związku z tym jest zawodny i nie powinien być używany przez nowe aplikacje. Aby uzyskać więcej informacji, zobacz [Funkcja PulseEvent](/windows/win32/api/winbase/nf-winbase-pulseevent).

##  <a name="resetevent"></a>CEvent::ResetEvent

Ustawia stan zdarzenia na Niesygnalizowane, dopóki nie zostanie jawnie ustawiony do sygnalizowania przez funkcję elementu [](#setevent) Członkowskiego seteven.

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Powoduje to, że wszystkie wątki, które chcą uzyskać dostęp do tego zdarzenia, oczekują.

Ta funkcja członkowska nie jest używana przez zdarzenia automatyczne.

##  <a name="setevent"></a>CEvent:: SetEvent

Ustawia stan zdarzenia do sygnalizowania, zwalniając wszystkie oczekujące wątki.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli funkcja zakończyła się powodzeniem, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli zdarzenie jest ręczne, zdarzenie pozostanie sygnalizowane do momentu wywołania [ResetEvent](#resetevent) . W tym przypadku można wydać więcej niż jeden wątek. Jeśli wydarzenie jest automatyczne, zdarzenie pozostanie sygnalizowane do momentu zwolnienia pojedynczego wątku. System ustawi następnie stan zdarzenia na Niesygnalizowane. Jeśli żadne wątki nie oczekują, stan pozostaje zasygnalizowani do momentu wydania jednego wątku.

##  <a name="unlock"></a>CEvent:: Unlock

Zwalnia obiekt zdarzenia.

```
BOOL Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli wątek należący do obiektu zdarzenia i zdarzenie jest zdarzeniem automatycznym; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez wątki, które obecnie są własnością automatyczne, aby zwolnić je po zakończeniu, jeśli ich obiekt blokady jest ponownie używany. Jeśli obiekt blokady nie zostanie ponownie użyty, ta funkcja zostanie wywołana przez destruktor obiektu blokady.

## <a name="see-also"></a>Zobacz także

[Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
