---
title: Klasa CDialogImpl
ms.date: 11/04/2016
f1_keywords:
- CDialogImpl
- ATLWIN/ATL::CDialogImpl
- ATLWIN/ATL::Create
- ATLWIN/ATL::DestroyWindow
- ATLWIN/ATL::DoModal
- ATLWIN/ATL::EndDialog
- ATLWIN/ATL::GetDialogProc
- ATLWIN/ATL::MapDialogRect
- ATLWIN/ATL::OnFinalMessage
- ATLWIN/ATL::DialogProc
- ATLWIN/ATL::StartDialogProc
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
ms.openlocfilehash: 900a312c97d7b83eac93a372be39a006b3c4344d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327052"
---
# <a name="cdialogimpl-class"></a>Klasa CDialogImpl

Ta klasa zawiera metody tworzenia modalnego lub trybutowego okna dialogowego.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Twoja klasa, pochodząca od `CDialogImpl`.

*Baza danych TBase*<br/>
Klasa podstawowa nowej klasy. Domyślną klasą podstawową jest [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Utwórz](#create)|Tworzy niemodowe okno dialogowe.|
|[Destroywindow](#destroywindow)|Niszczy niemodowe okno dialogowe.|
|[Domodal](#domodal)|Tworzy modalne okno dialogowe.|
|[Enddialog](#enddialog)|Niszczy modalne okno dialogowe.|

### <a name="cdialogimplbaset-methods"></a>Metody CDialogImplBaseT

|||
|-|-|
|[GetDialogProc ( GetDialogProc )](#getdialogproc)|Zwraca bieżącą procedurę okna dialogowego.|
|[MapDialogRect](#mapdialogrect)|Mapuje jednostki okna dialogowego określonego prostokąta na jednostki ekranu (piksele).|
|[OnFinalMessage](#onfinalmessage)|Wywoływana po otrzymaniu ostatniej wiadomości, zazwyczaj WM_NCDESTROY.|

### <a name="static-functions"></a>Funkcje statyczne

|||
|-|-|
|[Dialogproc](#dialogproc)|Przetwarza wiadomości wysyłane do okna dialogowego.|
|[StartDialogProc](#startdialogproc)|Wywoływana po odebraniu pierwszej wiadomości w celu przetworzenia wiadomości wysłanych do okna dialogowego.|

## <a name="remarks"></a>Uwagi

Za `CDialogImpl` pomocą można utworzyć modalne lub trybowe okno dialogowe. `CDialogImpl`zawiera procedurę okna dialogowego, która używa domyślnej mapy wiadomości do kierowania wiadomości do odpowiednich programów obsługi.

Destruktor `~CWindowImplRoot` klasy podstawowej zapewnia, że okno zniknie przed zniszczeniem obiektu.

`CDialogImpl`wynika z `CDialogImplBaseT`, który z `CWindowImplRoot`kolei pochodzi z .

> [!NOTE]
> Klasa musi zdefiniować element członkowski, `IDD` który określa identyfikator zasobu szablonu okna dialogowego. Na przykład Kreator projektu ATL automatycznie dodaje do klasy następujący wiersz:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

gdzie `MyDlg` znajduje się **krótka nazwa** wprowadzona na stronie **Nazwy** kreatora.

|Aby uzyskać więcej informacji dotyczących|Zobacz|
|--------------------------------|---------|
|Tworzenie formantów|[Samouczek ATL](../../atl/active-template-library-atl-tutorial.md)|
|Korzystanie z okien dialogowych w atl|[Klasy okien atl](../../atl/atl-window-classes.md)|
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Okna dialogowe|[Okna dialogowe](/windows/win32/dlgbox/dialog-boxes) i kolejne tematy w programie Windows SDK|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

## <a name="cdialogimplcreate"></a><a name="create"></a>CDialogImpl::Tworzenie

Tworzy niemodowe okno dialogowe.

```
HWND Create(
    HWND hWndParent,
    LPARAM dwInitParam = NULL );

HWND Create(
    HWND hWndParent,
    RECT&,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
[w] Dojście do okna właściciela.

**RECT&** *rect* [in] Struktura [RECT](/previous-versions/dd162897\(v=vs.85\)) określająca rozmiar i położenie okna dialogowego.

*dwInitParam*<br/>
[w] Określa wartość, która ma być przekazywalna do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

### <a name="return-value"></a>Wartość zwracana

Dojście do nowo utworzonego okna dialogowego.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie `CDialogImpl` dołączane do obiektu. Aby utworzyć modalne okno dialogowe, zadzwoń do [domodalu](#domodal). Drugie zastąpienie powyżej jest używane tylko z [CComControl](../../atl/reference/ccomcontrol-class.md).

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a>CDialogImpl::DestroyWindow

Niszczy niemodowe okno dialogowe.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno dialogowe zostało pomyślnie zniszczone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, jeśli okno dialogowe zostało pomyślnie zniszczone; w przeciwnym razie FALSE.

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a>CDialogImpl::DialogProc

Ta funkcja statyczna implementuje procedurę okna dialogowego.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[w] Uchwyt do okna dialogowego.

*uMsg*<br/>
[w] Wiadomość wysłana do okna dialogowego.

*Wparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

*Lparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli wiadomość jest przetwarzana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`DialogProc`używa domyślnej mapy wiadomości do kierowania wiadomości do odpowiednich programów obsługi.

Można `DialogProc` zastąpić, aby zapewnić inny mechanizm obsługi komunikatów.

## <a name="cdialogimpldomodal"></a><a name="domodal"></a>CDialogImpl::DoModal

Tworzy modalne okno dialogowe.

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

Jeśli się powiedzie, wartość parametru *nRetCode* określona w wywołaniu [EndDialog](#enddialog). W przeciwnym razie -1.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie `CDialogImpl` dołączane do obiektu.

Aby utworzyć niemodowe okno dialogowe, zadzwoń [do programu Create](#create).

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a>CDialogImpl::KoniecDialog

Niszczy modalne okno dialogowe.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*kod nRetCode*<br/>
[w] Wartość zwracana przez [CDialogImpl::DoModal](#domodal).

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno dialogowe zostanie zniszczone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`EndDialog`należy wywołać za pomocą procedury okna dialogowego. Po zniszczeniu okna dialogowego system Windows używa wartości *nRetCode* `DoModal`jako wartości zwracanej dla programu , która utworzyła okno dialogowe.

> [!NOTE]
> Nie wzywaj `EndDialog` do zniszczenia niemodytnego okna dialogowego. Zamiast tego zadzwoń [do CWindow::DestroyWindow.](../../atl/reference/cwindow-class.md#destroywindow)

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a>CDialogImpl::GetDialogProc

Zwraca `DialogProc`bieżącą procedurę okna dialogowego.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca procedura okna dialogowego.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby zastąpić procedurę okna dialogowego własną.

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a>CDialogImpl::MapDialogRect

Konwertuje (mapuje) jednostki okna dialogowego określonego prostokąta na jednostki ekranu (piksele).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Lprect*<br/>
Wskazuje obiekt `CRect` lub [strukturę RECT,](/windows/win32/api/windef/ns-windef-rect) która ma odbierać współrzędne klienta aktualizacji, która obejmuje region aktualizacji.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli aktualizacja zakończy się pomyślnie; 0, jeśli aktualizacja nie powiedzie się. Aby uzyskać rozszerzone informacje `GetLastError`o błędzie, zadzwoń do pliku .

### <a name="remarks"></a>Uwagi

Funkcja zastępuje współrzędne `RECT` w określonej strukturze konwertowanymi współrzędnymi, co umożliwia użycie struktury do utworzenia okna dialogowego lub umieszczenia formantu w oknie dialogowym.

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a>CDialogImpl::OnFinalMessage

Wywoływana po otrzymaniu ostatniej wiadomości `WM_NCDESTROY`(zazwyczaj ).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[w] Uchwyt do okna jest niszczony.

### <a name="remarks"></a>Uwagi

Zauważ, że jeśli chcesz automatycznie usunąć obiekt po zniszczeniu okna, możesz wywołać **usuń to;** tutaj.

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a>CDialogImpl::StartDialogProc

Wywoływana tylko raz, po odebraniu pierwszej wiadomości, do przetwarzania wiadomości wysłanych do okna dialogowego.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[w] Uchwyt do okna dialogowego.

*uMsg*<br/>
[w] Wiadomość wysłana do okna dialogowego.

*Wparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

*Lparam*<br/>
[w] Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Procedura okna.

### <a name="remarks"></a>Uwagi

Po początkowym `StartDialogProc`wywołaniu , `DialogProc` jest ustawiona jako procedura okna dialogowego, a dalsze połączenia tam.

## <a name="see-also"></a>Zobacz też

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
