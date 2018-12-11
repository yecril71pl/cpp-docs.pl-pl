---
title: Cdialogimpl — klasa
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
ms.openlocfilehash: b4844ed2246b5e700d9dc1895c3292cdde4efe8b
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178151"
---
# <a name="cdialogimpl-class"></a>Cdialogimpl — klasa

Ta klasa dostarcza metody do tworzenia modalne lub niemodalne okno dialogowe.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T,
    class TBase = CWindow>
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Z klasą pochodną `CDialogImpl`.

*Tpodstawowe*<br/>
Klasa bazowa nowej klasie. Domyślna klasa bazowa jest [CWindow](../../atl/reference/cwindow-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Tworzenie](#create)|Tworzy niemodalne okno dialogowe.|
|[Destroywindow —](#destroywindow)|Niszczy niemodalnego okna dialogowego.|
|[DoModal](#domodal)|Tworzy modalne okno dialogowe.|
|[Zdarzenie EndDialog](#enddialog)|Niszczy okno modalne okno dialogowe.|

### <a name="cdialogimplbaset-methods"></a>Metody CDialogImplBaseT

|||
|-|-|
|[GetDialogProc](#getdialogproc)|Zwraca bieżącą procedurę okna dialogowego pole.|
|[MapDialogRect](#mapdialogrect)|Mapuje jednostki okno dialogowe prostokąta określonej jednostki ekranu (w pikselach).|
|[OnFinalMessage](#onfinalmessage)|Wywołuje się po otrzymaniu ostatniego komunikatu zazwyczaj WM_NCDESTROY.|

### <a name="static-functions"></a>Funkcje statyczne

|||
|-|-|
|[DialogProc](#dialogproc)|Przetwarza komunikaty wysyłane do okna dialogowego.|
|[StartDialogProc](#startdialogproc)|Wywołuje się, gdy pierwszy wiadomość zostaje odebrana do przetwarzania komunikatów wysłanych do okna dialogowego.|

## <a name="remarks"></a>Uwagi

Za pomocą `CDialogImpl` utworzysz modalne lub niemodalne okno dialogowe. `CDialogImpl` zawiera procedury okno dialogowe używa domyślnego mapy komunikatów do przekierowywania komunikatów do odpowiedniej procedury obsługi.

Destruktor klasy podstawowej `~CWindowImplRoot` gwarantuje, że okno jest stała się przed zniszczenia obiektu.

`CDialogImpl` pochodzi od klasy `CDialogImplBaseT`, który z kolei pochodzi od klasy `CWindowImplRoot`.

> [!NOTE]
>  Klasa musi definiować `IDD` elementu członkowskiego, który określa identyfikator zasobu szablonu okna dialogowego. Na przykład Kreator projektów ATL automatycznie dodaje następujący wiersz do swojej klasy:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]

gdzie `MyDlg` jest **krótką nazwę** wprowadzona w kreatorze **nazwy** strony.

|Aby uzyskać więcej informacji dotyczących|Zobacz|
|--------------------------------|---------|
|Tworzenie formantów|[ALT — samouczek](../../atl/active-template-library-atl-tutorial.md)|
|Za pomocą okien dialogowych w ATL|[Klasy okien ATL](../../atl/atl-window-classes.md)|
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|
|Okna dialogowe|[Okna dialogowe](/windows/desktop/dlgbox/dialog-boxes) i kolejnych tematów w zestawie Windows SDK|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin.h

##  <a name="create"></a>  CDialogImpl::Create

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
[in] Dojście do okna właściciela.

**Prostokąt &** *prostokąt* [in] A [Prostokąt](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, określając rozmiar i położenie okna dialogowego.

*dwInitParam*<br/>
[in] Określa wartość do przekazania do okna dialogowego w *lParam* parametr / / Złap wiadomości.

### <a name="return-value"></a>Wartość zwracana

Uchwyt do nowo utworzonego okna dialogowego.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie dołączany do `CDialogImpl` obiektu. Aby utworzyć modalne okno dialogowe, wywołaj [DoModal](#domodal). Drugi zastąpienie powyżej jest używany tylko z [CComControl](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>  CDialogImpl::DestroyWindow

Niszczy niemodalnego okna dialogowego.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli okno dialogowe pomyślnie została zniszczona; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, jeśli okno dialogowe pomyślnie została zniszczona; w przeciwnym razie wartość FALSE.

##  <a name="dialogproc"></a>  CDialogImpl::DialogProc

Ta funkcja statyczna implementuje procedury okno dialogowe.

```
static LRESULT CALLBACK DialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Dojście do okna dialogowego.

*uMsg*<br/>
[in] Komunikat wysyłany do okna dialogowego.

*wParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli komunikat jest przetwarzany; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

`DialogProc` używa domyślnej mapy komunikatów do przekierowywania komunikatów do odpowiedniej procedury obsługi.

Można zastąpić `DialogProc` inny mechanizm obsługi wiadomości.

##  <a name="domodal"></a>  CDialogImpl::DoModal

Tworzy modalne okno dialogowe.

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

Jeśli to się powiedzie, wartość *nRetCode* parametr w wywołaniu [EndDialog](#enddialog). W przeciwnym razie, wartość -1.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie dołączany do `CDialogImpl` obiektu.

Aby utworzyć niemodalnego okna dialogowego, wywołaj [Utwórz](#create).

##  <a name="enddialog"></a>  CDialogImpl::EndDialog

Niszczy okno modalne okno dialogowe.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
[in] Wartość zwracana przez [CDialogImpl::DoModal](#domodal).

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli jest niszczony, okno dialogowe; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

`EndDialog` musi zostać wywołany przez procedurę okna dialogowego. Po jest niszczony, okno dialogowe, Windows używa wartości *nRetCode* jako wartość zwracaną dla `DoModal`, której utworzone okno dialogowe.

> [!NOTE]
>  Nie wywołuj `EndDialog` zniszczyć niemodalnego okna dialogowego. Wywołaj [CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) zamiast tego.

##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc

Zwraca `DialogProc`, bieżącą procedurę okna dialogowego pole.

```
virtual WNDPROC GetDialogProc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżącej procedurze okno dialogowe.

### <a name="remarks"></a>Uwagi

Zastępuje tę metodę, aby zastąpić procedurę okna dialogowego swoją własną.

##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect

Konwertuje jednostki (maps) okno dialogowe jednostki określonego prostokąta do ekranu (w pikselach).

```
BOOL MapDialogRect(LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*lprect —*<br/>
Wskazuje `CRect` obiektu lub [Prostokąt](/windows/desktop/api/windef/ns-windef-tagrect) strukturę, która będzie odbierać współrzędne klienta aktualizacji, która otacza region aktualizacji.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli aktualizacja się powiedzie; 0, jeśli aktualizacja nie powiodła się. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError`.

### <a name="remarks"></a>Uwagi

Funkcja zastępuje współrzędnych w określonym `RECT` struktura przekonwertowanego współrzędne, co pozwala strukturę, która ma być używany, aby utworzyć okno dialogowe lub położenie formantu w oknie dialogowym.

##  <a name="onfinalmessage"></a>  CDialogImpl::OnFinalMessage

Wywołuje się po otrzymaniu ostatniego komunikatu (zazwyczaj `WM_NCDESTROY`).

```
virtual void OnFinalMessage(HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Dojście do okna niszczone.

### <a name="remarks"></a>Uwagi

Należy pamiętać, że jeśli chcesz automatycznie usunąć obiektu na zniszczenie okna, można wywołać **usunąć ten;** tutaj.

##  <a name="startdialogproc"></a>  CDialogImpl::StartDialogProc

Wywoływana tylko raz, gdy pierwsza wiadomość zostanie odebrana, przetwarzać komunikaty wysyłane do okna dialogowego.

```
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
[in] Dojście do okna dialogowego.

*uMsg*<br/>
[in] Komunikat wysyłany do okna dialogowego.

*wParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

*lParam*<br/>
[in] Dodatkowe informacje specyficzne dla wiadomości.

### <a name="return-value"></a>Wartość zwracana

Procedurę okna.

### <a name="remarks"></a>Uwagi

Po wywołaniu początkowej `StartDialogProc`, `DialogProc` jest ustawiona jako procedurę okna dialogowego i dalsze wywołania przejdź do tego miejsca.

## <a name="see-also"></a>Zobacz też

[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)