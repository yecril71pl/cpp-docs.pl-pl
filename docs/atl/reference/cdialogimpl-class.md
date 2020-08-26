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
ms.openlocfilehash: b92b5130b31e88565d79b59a24b2bd377d0d84c0
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834729"
---
# <a name="cdialogimpl-class"></a>Klasa CDialogImpl

Ta klasa udostępnia metody tworzenia modalnych lub niemodalnych okien dialogowych.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa, która pochodzi od `CDialogImpl` .

*TBase*<br/>
Klasa bazowa nowej klasy. Domyślną klasą bazową jest [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|Funkcja|Opis|
|-|-|
|[Utwórz](#create)|Tworzy niemodalne okno dialogowe.|
|[DestroyWindow](#destroywindow)|Niszczy niemodalne okno dialogowe.|
|[DoModal](#domodal)|Tworzy modalne okno dialogowe.|
|[Zdarzenie EndDialog](#enddialog)|Niszczy modalne okno dialogowe.|

### <a name="cdialogimplbaset-methods"></a>Metody CDialogImplBaseT

|Funkcja|Opis|
|-|-|
|[GetDialogProc](#getdialogproc)|Zwraca bieżącą procedurę okna dialogowego.|
|[MapDialogRect](#mapdialogrect)|Mapuje jednostki okna dialogowego określonego prostokąta na jednostki ekranu (piksele).|
|[OnFinalMessage](#onfinalmessage)|Wywoływana po odebraniu ostatniego komunikatu, zwykle WM_NCDESTROY.|

### <a name="static-functions"></a>Funkcje statyczne

|Funkcja|Opis|
|-|-|
|[DialogProc](#dialogproc)|Przetwarza komunikaty wysyłane do okna dialogowego.|
|[StartDialogProc](#startdialogproc)|Wywoływana, gdy zostanie odebrany pierwszy komunikat do przetwarzania komunikatów wysyłanych do okna dialogowego.|

## <a name="remarks"></a>Uwagi

Za pomocą można `CDialogImpl` utworzyć modalne lub niemodalne okno dialogowe. `CDialogImpl` zawiera procedurę okna dialogowego, która używa domyślnej mapy komunikatów do kierowania komunikatów do odpowiednich programów obsługi.

Destruktor klasy bazowej `~CWindowImplRoot` gwarantuje, że okno zostało utracone przed zniszczeniem obiektu.

`CDialogImpl` pochodzi od `CDialogImplBaseT` , co z kolei wynika z `CWindowImplRoot` .

> [!NOTE]
> Klasa musi definiować `IDD` składową, która określa identyfikator zasobu szablonu okna dialogowego. Na przykład Kreator projektu ATL automatycznie dodaje następujący wiersz do klasy:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

gdzie `MyDlg` to **krótka nazwa** wprowadzona na stronie **nazw** kreatora.

|Aby uzyskać więcej informacji dotyczących|Zobacz|
|--------------------------------|---------|
|Tworzenie kontrolek|[Samouczek ATL](../../atl/active-template-library-atl-tutorial.md)|
|Używanie okien dialogowych w ATL|[Klasy okien ATL](../../atl/atl-window-classes.md)|
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Okna dialogowe|[Okna dialogowe](/windows/win32/dlgbox/dialog-boxes) i kolejne tematy w Windows SDK|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

## <a name="cdialogimplcreate"></a><a name="create"></a> CDialogImpl:: Create

Tworzy niemodalne okno dialogowe.

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

*hWndParent*<br/>
podczas Uchwyt do okna właściciela.

**Rect&** *Rect* [in] struktura [prostokąta](/windows/win32/api/windef/ns-windef-rect) określająca rozmiar i położenie okna dialogowego.

*dwInitParam*<br/>
podczas Określa wartość, która ma zostać przekazana do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do nowo utworzonego okna dialogowego.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie dołączane do `CDialogImpl` obiektu. Aby utworzyć modalne okno dialogowe, wywołaj [DoModal](#domodal). Drugie zastąpienie powyżej jest używane tylko z [CComControl](../../atl/reference/ccomcontrol-class.md).

## <a name="cdialogimpldestroywindow"></a><a name="destroywindow"></a> CDialogImpl::D estroyWindow

Niszczy niemodalne okno dialogowe.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno dialogowe zostało pomyślnie zniszczone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Zwraca wartość TRUE, jeśli okno dialogowe zostało pomyślnie zniszczone; w przeciwnym razie FALSE.

## <a name="cdialogimpldialogproc"></a><a name="dialogproc"></a> CDialogImpl::D ialogProc

Ta funkcja statyczna implementuje procedurę okna dialogowego.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Uchwyt do okna dialogowego.

*uMsg*<br/>
podczas Wiadomość wysłana do okna dialogowego.

*wParam*<br/>
podczas Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
podczas Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli komunikat jest przetwarzany; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`DialogProc` używa domyślnej mapy komunikatów do kierowania komunikatów do odpowiednich programów obsługi.

Można przesłonić, `DialogProc` Aby zapewnić inny mechanizm obsługi komunikatów.

## <a name="cdialogimpldomodal"></a><a name="domodal"></a> CDialogImpl::D oModal

Tworzy modalne okno dialogowe.

```
INT_PTR DoModal(
    HWND hWndParent = ::GetActiveWindow(),
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
podczas Uchwyt do okna właściciela. Wartość domyślna jest wartością zwracaną funkcji Win32 [GetActiveWindow](/windows/win32/api/winuser/nf-winuser-getactivewindow) .

*dwInitParam*<br/>
podczas Określa wartość, która ma zostać przekazana do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, wartość parametru *nRetCode* określona w wywołaniu metody [zdarzenie EndDialog](#enddialog). W przeciwnym razie-1.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie dołączane do `CDialogImpl` obiektu.

Aby utworzyć niemodalne okno dialogowe, wywołaj polecenie [Utwórz](#create).

## <a name="cdialogimplenddialog"></a><a name="enddialog"></a> CDialogImpl:: zdarzenie EndDialog

Niszczy modalne okno dialogowe.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
podczas Wartość, która ma zostać zwrócona przez [CDialogImpl::D omodal](#domodal).

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli okno dialogowe zostało zniszczone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`EndDialog` musi być wywoływana za pomocą procedury okna dialogowego. Po zniszczeniu okna dialogowego system Windows używa wartości *nRetCode* jako wartości zwracanej dla `DoModal` , która utworzyła okno dialogowe.

> [!NOTE]
> Nie wywołuj, `EndDialog` aby zniszczyć niemodalne okno dialogowe. W zamian wywołaj [CWindow::D estroywindow](../../atl/reference/cwindow-class.md#destroywindow) .

## <a name="cdialogimplgetdialogproc"></a><a name="getdialogproc"></a> CDialogImpl::GetDialogProc

Zwraca `DialogProc` bieżącą procedurę okna dialogowego.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca procedura okna dialogowego.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, aby zamienić procedurę dialogu z własnymi.

## <a name="cdialogimplmapdialogrect"></a><a name="mapdialogrect"></a> CDialogImpl::MapDialogRect

Konwertuje (mapuje) jednostki okna dialogowego określonego prostokąta na jednostki ekranu (piksele).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lpRect*<br/>
Wskazuje na `CRect` obiekt lub strukturę [prostokąta](/windows/win32/api/windef/ns-windef-rect) , który ma otrzymywać współrzędne klienta aktualizacji, która zawiera region aktualizacji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli aktualizacja się powiedzie; 0, jeśli aktualizacja nie powiedzie się. Aby uzyskać rozszerzone informacje o błędzie, wywołaj polecenie `GetLastError` .

### <a name="remarks"></a>Uwagi

Funkcja zastępuje współrzędne w określonej `RECT` strukturze przy użyciu przekonwertowanych współrzędnych, dzięki czemu struktura ma być używana do tworzenia okna dialogowego lub pozycjonowania kontrolki w oknie dialogowym.

## <a name="cdialogimplonfinalmessage"></a><a name="onfinalmessage"></a> CDialogImpl::OnFinalMessage

Wywoływana po odebraniu ostatniej wiadomości (zazwyczaj `WM_NCDESTROY` ).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Dojście do uszkodzonego okna.

### <a name="remarks"></a>Uwagi

Należy pamiętać, że jeśli chcesz automatycznie usunąć obiekt przy zniszczeniu okna, możesz wywołać polecenie **Usuń** w tym miejscu.

## <a name="cdialogimplstartdialogproc"></a><a name="startdialogproc"></a> CDialogImpl::StartDialogProc

Wywoływana tylko raz, gdy zostanie odebrany pierwszy komunikat, w celu przetworzenia komunikatów wysyłanych do okna dialogowego.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Właściwość*<br/>
podczas Uchwyt do okna dialogowego.

*uMsg*<br/>
podczas Wiadomość wysłana do okna dialogowego.

*wParam*<br/>
podczas Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
podczas Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Procedura okna.

### <a name="remarks"></a>Uwagi

Po początkowej wywołaniu do `StartDialogProc` , `DialogProc` jest ustawiony jako procedura okna dialogowego, a następnie w tym miejscu znajdują się dalsze wywołania.

## <a name="see-also"></a>Zobacz też

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
