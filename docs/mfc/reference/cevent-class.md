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
ms.openlocfilehash: 009a17342cb92025d67bf2fe0df1b9d5c7c0c6f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373956"
---
# <a name="cevent-class"></a>Klasa CEvent

Reprezentuje zdarzenie, który jest obiekt synchronizacji, który umożliwia jeden wątek, aby powiadomić innego, że wystąpiło zdarzenie.

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
|[CEvent::PulseEvent](#pulseevent)|Ustawia zdarzenie na dostępne (sygnalizowane), zwalnia oczekujące wątki i ustawia zdarzenie na niedostępne (niepodpisane).|
|[CEvent::ResetEvent](#resetevent)|Ustawia zdarzenie na niedostępne (niepodpisane).|
|[CEvent::SetEvent](#setevent)|Ustawia zdarzenie na dostępne (sygnalizowane) i zwalnia wszystkie wątki oczekiwania.|
|[CEvent::Odblokuj](#unlock)|Zwalnia obiekt zdarzenia.|

## <a name="remarks"></a>Uwagi

Zdarzenia są przydatne, gdy wątek musi wiedzieć, kiedy wykonać swoje zadanie. Na przykład wątek kopiuje dane do archiwum danych musi być powiadamiany, gdy dostępne są nowe dane. Za pomocą `CEvent` obiektu do powiadamiania wątku kopiowania, gdy nowe dane są dostępne, wątek może wykonać swoje zadanie tak szybko, jak to możliwe.

`CEvent`obiekty mają dwa typy: ręczny i automatyczny.

Obiekt `CEvent` automatyczny automatycznie powraca do stanu niesygnalizowanego (niedostępnego) po zwolnieniu co najmniej jednego wątku. Domyślnie obiekt `CEvent` jest automatyczny, `TRUE` chyba że przekażesz dla *parametru bManualReset* podczas budowy.

Obiekt `CEvent` ręczny pozostaje w stanie ustawionym przez [SetEvent](#setevent) lub [ResetEvent,](#resetevent) dopóki nie zostanie wywołana inna funkcja. Aby utworzyć `CEvent` obiekt ręczny, przekaż `TRUE` `bManualReset` parametr podczas budowy.

Aby użyć `CEvent` obiektu, `CEvent` należy skonstruować obiekt, gdy jest to wymagane. Określ nazwę zdarzenia, na które chcesz czekać, a także określ, że aplikacja powinna początkowo być jej właścicielem. Następnie można uzyskać dostęp do zdarzenia, gdy konstruktor zwraca. Wywołaj [SetEvent,](#setevent) aby zasygnalizować (udostępnić) obiekt zdarzenia, a następnie [wywołać Unlock](#unlock) po zakończeniu uzyskiwania dostępu do kontrolowanego zasobu.

Alternatywną metodą `CEvent` używania obiektów jest `CEvent` dodanie zmiennej typu jako elementu członkowskiego danych do klasy, którą chcesz kontrolować. Podczas budowy kontrolowanego obiektu wywołaj konstruktora elementu członkowskiego `CEvent` danych i określ, czy zdarzenie jest początkowo sygnalizowane, a także określ typ obiektu zdarzenia, którego chcesz, nazwę zdarzenia (jeśli będzie on używany przez granice procesu) i wszelkie atrybuty zabezpieczeń, które chcesz.

Aby uzyskać dostęp do `CEvent` zasobu kontrolowanego przez obiekt w ten sposób, najpierw należy utworzyć zmienną typu [CSingleLock](../../mfc/reference/csinglelock-class.md) lub typu [CMultiLock](../../mfc/reference/cmultilock-class.md) w metodzie dostępu zasobu. Następnie wywołaj `Lock` metodę obiektu blokady (na przykład [CMultiLock::Lock](../../mfc/reference/cmultilock-class.md#lock)). W tym momencie wątek będzie albo uzyskać dostęp do zasobu, czekać na zasób do zwolnienia i uzyskać dostęp lub czekać na zasób do wydania, limit czasu i nie można uzyskać dostępu do zasobu. W każdym przypadku zasób został osiągnięty w sposób bezpieczny dla wątków. Aby zwolnić zasób, wywołać `SetEvent` sygnał obiektu `Unlock` zdarzenia, a następnie użyć metody obiektu lock (na przykład [CMultiLock::Unlock](../../mfc/reference/cmultilock-class.md#unlock)), lub niech obiekt blokady wypaść z zakresu.

Aby uzyskać więcej informacji `CEvent` na temat używania obiektów, zobacz [Wielowątkowe: Jak korzystać z klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CSyncObject (100)](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

## <a name="ceventcevent"></a><a name="cevent"></a>CEvent::CEvent

Konstruuje obiekt o `CEvent` nazwie lub bez nazwy.

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>Parametry

*bNienajleszaninowo*<br/>
Jeśli true, `CMultilock` wątek `CSingleLock` lub obiektu jest włączona. W przeciwnym razie wszystkie wątki, które chcą uzyskać dostęp do zasobu musi czekać.

*bManualReset*<br/>
Jeśli TRUE, określa, że obiekt zdarzenia jest zdarzeniem ręcznym, w przeciwnym razie obiekt zdarzenia jest zdarzeniem automatycznym.

*Lpszname*<br/>
Nazwa `CEvent` obiektu. Musi być dostarczony, jeśli obiekt będzie używany przez granice procesu. Jeśli nazwa pasuje do istniejącego zdarzenia, konstruktor tworzy nowy `CEvent` obiekt, który odwołuje się do zdarzenia o tej nazwie. Jeśli nazwa pasuje do istniejącego obiektu synchronizacji, który nie jest zdarzeniem, konstrukcja zakończy się niepowodzeniem. Jeśli wartość NULL, nazwa będzie null.

*lpsaAttribute*<br/>
Atrybuty zabezpieczeń obiektu zdarzenia. Aby uzyskać pełny opis tej struktury, zobacz [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) w windows SDK.

### <a name="remarks"></a>Uwagi

Aby uzyskać dostęp `CEvent` do obiektu lub zwolnić go, należy utworzyć obiekt [CMultiLock](../../mfc/reference/cmultilock-class.md) lub [CSingleLock](../../mfc/reference/csinglelock-class.md) i wywołać jego funkcje elementów członkowskich [Lock](../../mfc/reference/csinglelock-class.md#lock) i [Unlock.](../../mfc/reference/csinglelock-class.md#unlock)

Aby zmienić stan `CEvent` obiektu na sygnalizowany (wątki nie muszą czekać), wywołaj [SetEvent](#setevent) lub [PulseEvent](#pulseevent). Aby ustawić stan `CEvent` obiektu na niezasygnatowany (wątki muszą czekać), zadzwoń [ResetEvent](#resetevent).

> [!IMPORTANT]
> Po utworzeniu `CEvent` obiektu należy użyć [GetLastError,](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) aby upewnić się, że obiekt mutex jeszcze nie istnieje. Jeśli mutex nie istnieje nieoczekiwanie, może to wskazywać, że proces nieuczciwych jest kucanie i może być zamierza użyć mutex złośliwie. W takim przypadku zalecana procedura dbająca o bezpieczeństwo jest zamknięcie dojścia i kontynuowanie tak, jakby wystąpił błąd w tworzeniu obiektu.

## <a name="ceventpulseevent"></a><a name="pulseevent"></a>CEvent::PulseEvent

Ustawia stan zdarzenia na sygnalizowane (dostępne), zwalnia wszystkie wątki oczekiwania i resetuje go do nonsignaled (niedostępne) automatycznie.

```
BOOL PulseEvent();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli zdarzenie jest ręczne, wszystkie wątki oczekiwania są zwalniane, zdarzenie `PulseEvent` jest ustawione na nonsignaled i zwraca. Jeśli zdarzenie jest automatyczne, pojedynczy wątek jest zwalniany, zdarzenie `PulseEvent` jest ustawione na nonsignaled i zwraca.

Jeśli nie wątki oczekują lub nie wątki mogą `PulseEvent` być zwolnione natychmiast, ustawia stan zdarzenia nonsignaled i zwraca.

`PulseEvent`używa podstawowej funkcji `PulseEvent` Win32, która może być chwilowo usunięta ze stanu oczekiwania przez wywołanie procedury asynchronicznie w trybie jądra. W związku `PulseEvent` z tym jest zawodne i nie powinny być używane przez nowe aplikacje. Aby uzyskać więcej informacji, zobacz [funkcję PulseEvent](/windows/win32/api/winbase/nf-winbase-pulseevent).

## <a name="ceventresetevent"></a><a name="resetevent"></a>CEvent::ResetEvent

Ustawia stan zdarzenia nonsignaled, dopóki jawnie ustawić na sygnalizowane przez [SetEvent](#setevent) funkcji elementu członkowskiego.

```
BOOL ResetEvent();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Powoduje to, że wszystkie wątki, które chcą uzyskać dostęp do tego zdarzenia, aby poczekać.

Ta funkcja elementu członkowskiego nie jest używana przez zdarzenia automatyczne.

## <a name="ceventsetevent"></a><a name="setevent"></a>CEvent::SetEvent

Ustawia stan zdarzenia do sygnalizowane, zwalniając żadnych wątków oczekiwania.

```
BOOL SetEvent();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli funkcja zakończyła się pomyślnie, w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli zdarzenie jest ręczne, zdarzenie pozostanie sygnalizowane do momentu [wywołania resetevent.](#resetevent) W tym przypadku można uwolnić więcej niż jeden wątek. Jeśli zdarzenie jest automatyczne, zdarzenie pozostanie sygnalizowane, dopóki nie zostanie zwolniony pojedynczy wątek. System ustawi następnie stan zdarzenia na nonsignaled. Jeśli nie wątki czekają, stan pozostaje sygnalizowane, dopóki jeden wątek jest zwolniony.

## <a name="ceventunlock"></a><a name="unlock"></a>CEvent::Odblokuj

Zwalnia obiekt zdarzenia.

```
BOOL Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wątek posiadał obiekt zdarzenia, a zdarzenie jest zdarzeniem automatycznym; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego jest wywoływana przez wątki, które obecnie posiadają zdarzenie automatyczne, aby zwolnić go po zakończeniu, jeśli ich obiekt blokady ma być ponownie użyczony. Jeśli obiekt lock nie ma być ponownie za pomocą, funkcja ta zostanie wywołana przez destruktora obiektu blokady.

## <a name="see-also"></a>Zobacz też

[Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
