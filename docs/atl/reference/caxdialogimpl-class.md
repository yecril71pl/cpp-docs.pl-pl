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
ms.openlocfilehash: d8e60a817d197f67c14318a7d50ddf796e570142
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318738"
---
# <a name="caxdialogimpl-class"></a>Klasa CAxDialogImpl

Ta klasa implementuje okno dialogowe (modalne lub modne), w którym są hosty formantów ActiveX.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `CAxDialogImpl`.

*Baza danych TBase*<br/>
Podstawowa klasa `CDialogImplBaseT`okna dla .

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Wywołanie tej metody, aby doradzić lub unadvise wszystkie wpisy na mapie ujścia obiektu mapę zdarzeń.|
|[CAxDialogImpl::Tworzenie](#create)|Wywołanie tej metody, aby utworzyć niemodowe okno dialogowe.|
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Wywołanie tej metody, aby zniszczyć niemodless okna dialogowego.|
|[CAxDialogImpl::DoModal](#domodal)|Wywołanie tej metody, aby utworzyć modalne okno dialogowe.|
|[CAxDialogImpl::KoniecDialog](#enddialog)|Wywołanie tej metody, aby zniszczyć modalne okno dialogowe.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Wywołanie tej metody, aby `DialogProc` uzyskać wskaźnik do funkcji wywołania zwrotnego.|
|[CAxDialogImpl::GetIDD](#getidd)|Wywołanie tej metody, aby uzyskać identyfikator zasobu szablonu okna dialogowego|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Wywołanie tej metody, aby ustalić, czy wiadomość jest przeznaczona dla tego okna dialogowego i, jeśli jest, proces wiadomości.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CAxDialogImpl::m_bModal](#m_bmodal)|Zmienna, która istnieje tylko w kompilacjach debugowania i jest ustawiona na true, jeśli okno dialogowe jest modalne.|

## <a name="remarks"></a>Uwagi

`CAxDialogImpl`umożliwia utworzenie modalnego lub trybuless okna dialogowego. `CAxDialogImpl`zawiera procedurę okna dialogowego, która używa domyślnej mapy wiadomości do kierowania wiadomości do odpowiednich programów obsługi.

`CAxDialogImpl`pochodzi od `CDialogImplBaseT`, który z kolei pochodzi z `CWindow` *TBase* (domyślnie) i `CMessageMap`.

Klasa musi zdefiniować element członkowski identyfikatora, który określa identyfikator zasobu szablonu okna dialogowego. Na przykład dodanie obiektu okna dialogowego ATL za pomocą okna dialogowego **Dodawanie klasy** automatycznie dodaje do klasy następujący wiersz:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

gdzie `MyDialog` jest **krótka nazwa** wprowadzona w Kreatorze okien dialogowych ATL.

Aby uzyskać więcej informacji, zobacz [Implementowanie okna dialogowego.](../../atl/implementing-a-dialog-box.md)

Należy zauważyć, że kontrolka ActiveX `CAxDialogImpl` w oknie dialogowym modalnym utworzonym za pomocą nie obsługuje klawiszy akceleratora. Aby obsługiwać klucze akceleratora w oknie dialogowym utworzonym za pomocą `CAxDialogImpl`programu , utwórz niemodne okno dialogowe i używając własnej pętli komunikatów, użyj [CAxDialogImpl::IsDialogMessage](#isdialogmessage) po otrzymaniu wiadomości z kolejki w celu obsługi klucza akceleratora.

Aby uzyskać `CAxDialogImpl`więcej informacji na temat , zobacz [ATL Control Containment FAQ](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cmessagemap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="caxdialogimpladvisesinkmap"></a><a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap

Wywołanie tej metody, aby doradzić lub unadvise wszystkie wpisy na mapie ujścia obiektu mapę zdarzeń.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Ustaw wartość true, jeśli wszystkie wpisy zlewu mają być zalecane; false, jeśli wszystkie wpisy ujścia mają być unadvised.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="caxdialogimplcreate"></a><a name="create"></a>CAxDialogImpl::Tworzenie

Wywołanie tej metody, aby utworzyć niemodowe okno dialogowe.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
[w] Dojście do okna właściciela.

*dwInitParam*<br/>
[w] Określa wartość, która ma być przekazywalna do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

*&RECT*<br/>
Ten parametr nie jest używany. Ten parametr jest `CComControl`przekazywany przez .

### <a name="return-value"></a>Wartość zwracana

Dojście do nowo utworzonego okna dialogowego.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie `CAxDialogImpl` dołączane do obiektu. Aby utworzyć modalne okno dialogowe, zadzwoń do [domodalu](#domodal).

Drugie zastąpienie jest dostępne tylko po to, aby okna dialogowe mogły być używane z [CComControl](../../atl/reference/ccomcontrol-class.md).

## <a name="caxdialogimpldestroywindow"></a><a name="destroywindow"></a>CAxDialogImpl::DestroyWindow

Wywołanie tej metody, aby zniszczyć niemodless okna dialogowego.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno zostało pomyślnie zniszczone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Nie należy `DestroyWindow` wywoływać, aby zniszczyć modalne okno dialogowe. Zamiast tego zadzwoń [do EndDialog.](#enddialog)

## <a name="caxdialogimpldomodal"></a><a name="domodal"></a>CAxDialogImpl::DoModal

Wywołanie tej metody, aby utworzyć modalne okno dialogowe.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
[w] Dojście do okna właściciela. Wartością domyślną jest zwracana wartość funkcji [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) Win32.

*dwInitParam*<br/>
[w] Określa wartość, która ma być przekazywalna do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, wartość parametru *nRetCode* określona w wywołaniu [EndDialog](#enddialog); w przeciwnym razie -1.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie `CAxDialogImpl` dołączane do obiektu.

Aby utworzyć niemodowe okno dialogowe, zadzwoń [do programu Create](#create).

## <a name="caxdialogimplenddialog"></a><a name="enddialog"></a>CAxDialogImpl::KoniecDialog

Wywołanie tej metody, aby zniszczyć modalne okno dialogowe.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*kod nRetCode*<br/>
[w] Wartość, która ma zostać zwrócona przez [DoModal](#domodal).

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno dialogowe zostanie zniszczone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`EndDialog`należy wywołać za pomocą procedury okna dialogowego. Po zniszczeniu okna dialogowego system Windows używa wartości *nRetCode* `DoModal`jako wartości zwracanej dla programu , która utworzyła okno dialogowe.

> [!NOTE]
> Nie wzywaj `EndDialog` do zniszczenia niemodytnego okna dialogowego. Zamiast tego zadzwoń [do DestroyWindow.](#destroywindow)

## <a name="caxdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc

Wywołanie tej metody, aby `DialogProc` uzyskać wskaźnik do funkcji wywołania zwrotnego.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `DialogProc` funkcji wywołania zwrotnego.

### <a name="remarks"></a>Uwagi

Funkcja `DialogProc` jest funkcją wywołania zwrotnego zdefiniowaną przez aplikację.

## <a name="caxdialogimplgetidd"></a><a name="getidd"></a>CAxDialogImpl::GetIDD

Wywołanie tej metody, aby uzyskać identyfikator zasobu szablonu okna dialogowego.

```
int GetIDD();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca identyfikator zasobu szablonu okna dialogowego.

## <a name="caxdialogimplisdialogmessage"></a><a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage

Wywołanie tej metody, aby ustalić, czy wiadomość jest przeznaczona dla tego okna dialogowego i, jeśli jest, proces wiadomości.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskaźnik do struktury [MSG,](/windows/win32/api/winuser/ns-winuser-msg) która zawiera wiadomość do sprawdzenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli wiadomość została przetworzona, w przeciwnym razie wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

Ta metoda jest przeznaczona do wywołania z wewnątrz pętli komunikatów.

## <a name="caxdialogimplm_bmodal"></a><a name="m_bmodal"></a>CAxDialogImpl::m_bModal

Zmienna, która istnieje tylko w kompilacjach debugowania i jest ustawiona na true, jeśli okno dialogowe jest modalne.

```
bool m_bModal;
```

## <a name="see-also"></a>Zobacz też

[Klasa CDialogImpl](../../atl/reference/cdialogimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
