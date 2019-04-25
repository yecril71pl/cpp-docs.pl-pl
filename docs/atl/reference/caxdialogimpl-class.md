---
title: Klasa CAxDialogImpl
ms.date: 11/04/2016
f1_keywords:
- CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl
- ATLWIN/ATL::CAxDialogImpl::AdviseSinkMap
- ATLWIN/ATL::CAxDialogImpl::Create
- ATLWIN/ATL::CAxDialogImpl::DestroyWindow
- ATLWIN/ATL::CAxDialogImpl::DoModal
- ATLWIN/ATL::CAxDialogImpl::EndDialog
- ATLWIN/ATL::CAxDialogImpl::GetDialogProc
- ATLWIN/ATL::CAxDialogImpl::GetIDD
- ATLWIN/ATL::CAxDialogImpl::IsDialogMessage
- ATLWIN/ATL::CAxDialogImpl::m_bModal
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
ms.openlocfilehash: d6f08553a9eff421923ef348caee2022849674ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259966"
---
# <a name="caxdialogimpl-class"></a>Klasa CAxDialogImpl

Ta klasa implementuje okno dialogowe (modalnym lub niemodalnym), który obsługuje formanty ActiveX.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `CAxDialogImpl`.

*Tpodstawowe*<br/>
Klasa podstawowa okna dla `CDialogImplBaseT`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Wywołaj tę metodę, aby przeprowadzić operację advise lub unadvise wszystkie wpisy w mapie zdarzeń mapie obiektu.|
|[CAxDialogImpl::Create](#create)|Wywołaj tę metodę, aby utworzyć niemodalnego okna dialogowego.|
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Wywołaj tę metodę, aby zniszczyć niemodalnego okna dialogowego.|
|[CAxDialogImpl::DoModal](#domodal)|Wywołaj tę metodę, aby utworzyć modalne okno dialogowe.|
|[CAxDialogImpl::EndDialog](#enddialog)|Wywołaj tę metodę, aby zniszczyć modalne okno dialogowe.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Wywołaj tę metodę, aby uzyskać wskaźnik do `DialogProc` funkcji wywołania zwrotnego.|
|[CAxDialogImpl::GetIDD](#getidd)|Wywołaj tę metodę, aby uzyskać identyfikator zasobu szablonu okna dialogowego|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Wywołanie tej metody, aby ustalić, czy komunikat jest przeznaczony dla tego okna dialogowego, a jeśli tak jest, należy przetworzyć komunikatu.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CAxDialogImpl::m_bModal](#m_bmodal)|Zmienna, która istnieje tylko w przypadku debugowania kompilacji i jest ustawiona na wartość true, jeśli jest modalne okno dialogowe.|

## <a name="remarks"></a>Uwagi

`CAxDialogImpl` Pozwala utworzyć modalne lub niemodalne okno dialogowe. `CAxDialogImpl` zawiera procedury okno dialogowe używa domyślnego mapy komunikatów do przekierowywania komunikatów do odpowiedniej procedury obsługi.

`CAxDialogImpl` pochodzi od klasy `CDialogImplBaseT`, który z kolei pochodzi od klasy *Tpodstawowe* (domyślnie `CWindow`) i `CMessageMap`.

Klasa musi definiować element członkowski IDD, który określa identyfikator zasobu szablonu okna dialogowego. Na przykład dodanie obiektu okna dialogowego ATL za pomocą **Dodaj klasę** okno dialogowe automatycznie dodaje następujący wiersz do swojej klasy:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

gdzie `MyDialog` jest **krótką nazwę** wprowadzone w Kreatorze okna dialogowego ATL.

Zobacz [Implementowanie okna dialogowego](../../atl/implementing-a-dialog-box.md) Aby uzyskać więcej informacji.

Należy zauważyć, że formant ActiveX na modalne okno dialogowe utworzonych za pomocą `CAxDialogImpl` nie będzie obsługiwał klawiszy skrótów. Do obsługi klawiszy skrótów w oknie dialogowym utworzonych za pomocą `CAxDialogImpl`, niemodalne okno dialogowe Tworzenie i używanie własnych pętli komunikatów, należy użyć [CAxDialogImpl::IsDialogMessage](#isdialogmessage) po otrzymaniu komunikatu z kolejki w celu obsługi klawisz skrótu.

Aby uzyskać więcej informacji na temat `CAxDialogImpl`, zobacz [ATL kontroli zawierania — często zadawane pytania](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="advisesinkmap"></a>  CAxDialogImpl::AdviseSinkMap

Wywołaj tę metodę, aby przeprowadzić operację advise lub unadvise wszystkie wpisy w mapie zdarzeń mapie obiektu.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Ustaw wartość true, jeśli wszystkie wpisy ujścia zaleceniem; obiekt sink wartość false, jeśli wszystkie wpisy są unadvised.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="create"></a>  CAxDialogImpl::Create

Wywołaj tę metodę, aby utworzyć niemodalnego okna dialogowego.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[in] Dojście do okna właściciela.

*dwInitParam*<br/>
[in] Określa wartość do przekazania do okna dialogowego w *lParam* parametr / / Złap wiadomości.

*PROSTOKĄT &AMP;*<br/>
Ten parametr nie jest używany. Ten parametr jest przekazywany w przez `CComControl`.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do nowo utworzonego okna dialogowego.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie dołączany do `CAxDialogImpl` obiektu. Aby utworzyć modalne okno dialogowe, wywołaj [DoModal](#domodal).

Drugi zastąpienia znajduje się tylko w przypadku, więc okien dialogowych mogą być używane z [CComControl](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>  CAxDialogImpl::DestroyWindow

Wywołaj tę metodę, aby zniszczyć niemodalnego okna dialogowego.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okno jest niszczony, pomyślnie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Nie wywołuj `DestroyWindow` zniszczyć modalne okno dialogowe. Wywołaj [EndDialog](#enddialog) zamiast tego.

##  <a name="domodal"></a>  CAxDialogImpl::DoModal

Wywołaj tę metodę, aby utworzyć modalne okno dialogowe.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[in] Dojście do okna właściciela. Wartość domyślna to wartość zwracana przez [GetActiveWindow](/windows/desktop/api/winuser/nf-winuser-getactivewindow) funkcję Win32.

*dwInitParam*<br/>
[in] Określa wartość do przekazania do okna dialogowego w *lParam* parametr / / Złap wiadomości.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wartość *nRetCode* parametr w wywołaniu [EndDialog](#enddialog); w przeciwnym razie wartość -1.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie dołączany do `CAxDialogImpl` obiektu.

Aby utworzyć niemodalnego okna dialogowego, wywołaj [Utwórz](#create).

##  <a name="enddialog"></a>  CAxDialogImpl::EndDialog

Wywołaj tę metodę, aby zniszczyć modalne okno dialogowe.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
[in] Wartość zwracana przez [DoModal](#domodal).

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli jest niszczony, okno dialogowe; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

`EndDialog` musi zostać wywołany przez procedurę okno dialogowe. Po jest niszczony, okno dialogowe, Windows używa wartości *nRetCode* jako wartość zwracaną dla `DoModal`, której utworzone okno dialogowe.

> [!NOTE]
>  Nie wywołuj `EndDialog` zniszczyć niemodalnego okna dialogowego. Wywołaj [destroywindow —](#destroywindow) zamiast tego.

##  <a name="getdialogproc"></a>  CAxDialogImpl::GetDialogProc

Wywołaj tę metodę, aby uzyskać wskaźnik do `DialogProc` funkcji wywołania zwrotnego.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `DialogProc` funkcji wywołania zwrotnego.

### <a name="remarks"></a>Uwagi

`DialogProc` Funkcji jest zdefiniowany przez aplikację funkcji wywołania zwrotnego.

##  <a name="getidd"></a>  CAxDialogImpl::GetIDD

Wywołanie tej metody można pobrać identyfikatora zasobu szablonu okna dialogowego.

```
int GetIDD();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca identyfikator zasobu szablonu okna dialogowego.

##  <a name="isdialogmessage"></a>  CAxDialogImpl::IsDialogMessage

Wywołanie tej metody, aby ustalić, czy komunikat jest przeznaczony dla tego okna dialogowego, a jeśli tak jest, należy przetworzyć komunikatu.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskaźnik do [MSG](/windows/desktop/api/winuser/ns-winuser-msg) strukturę, która zawiera komunikat, który ma być zaznaczone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli komunikat został przetworzony, wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Ta metoda jest przeznaczona do wywoływania z w obrębie pętli komunikatów.

##  <a name="m_bmodal"></a>  CAxDialogImpl::m_bModal

Zmienna, która istnieje tylko w przypadku debugowania kompilacji i jest ustawiona na wartość true, jeśli jest modalne okno dialogowe.

```
bool m_bModal;
```

## <a name="see-also"></a>Zobacz także

[Klasa CDialogImpl](../../atl/reference/cdialogimpl-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
