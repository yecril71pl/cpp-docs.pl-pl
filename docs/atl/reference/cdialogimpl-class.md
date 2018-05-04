---
title: Cdialogimpl — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes, ATL
- CDialogImpl class
ms.assetid: d430bc7b-8a28-4ad3-9507-277bdd2c2c2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4119daf89820de0a835bfbc572cdfbf38c99e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cdialogimpl-class"></a>Cdialogimpl — klasa
Ta klasa dostarcza metody do tworzenia modalne i niemodalne okno dialogowe.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
 
template <class T,  
    class TBase = CWindow>  
    class ATL_NO_VTABLE CDialogImpl : public CDialogImplBaseT<TBase>  
 
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `CDialogImpl`.  
  
 *TBase*  
 Klasa podstawowa nowej klasy. Domyślna klasa podstawowa jest [CWindow](../../atl/reference/cwindow-class.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Utwórz](#create)|Tworzy niemodalne okno dialogowe.|  
|[DestroyWindow](#destroywindow)|Niszczy niemodalne okno dialogowe.|  
|[DoModal](#domodal)|Tworzy modalne okno dialogowe.|  
|[EndDialog](#enddialog)|Niszczy modalne okno dialogowe.|  
  
### <a name="cdialogimplbaset-methods"></a>Metody CDialogImplBaseT  
  
|||  
|-|-|  
|[GetDialogProc](#getdialogproc)|Zwraca bieżącą procedurę okno dialogowe.|  
|[MapDialogRect](#mapdialogrect)|Mapuje jednostki okno dialogowe określonego prostokąta na ekranie jednostki (w pikselach).|  
|[OnFinalMessage](#onfinalmessage)|Wywołuje się po otrzymaniu ostatniego komunikatu zwykle `WM_NCDESTROY`.|  
  
### <a name="static-functions"></a>Funkcje statyczne  
  
|||  
|-|-|  
|[DialogProc](#dialogproc)|Przetwarza wiadomości wysyłane do okna dialogowego.|  
|[StartDialogProc](#startdialogproc)|Wywoływane, gdy pierwszy komunikat jest odbierany przetworzyć komunikaty wysyłane do okna dialogowego.|  
  
## <a name="remarks"></a>Uwagi  
 Z `CDialogImpl` można utworzyć modalne i niemodalne okno dialogowe. `CDialogImpl` zawiera procedury okno dialogowe używa domyślnej mapy wiadomości do kierowania wiadomości na odpowiednie programy obsługi.  
  
 Destruktor klasy podstawowej **~ CWindowImplRoot** gwarantuje, że okna został usunięty przed niszczenie obiektu.  
  
 `CDialogImpl` pochodną **CDialogImplBaseT**, który z kolei jest pochodną **CWindowImplRoot**.  
  
> [!NOTE]
>  Zdefiniuj klasy **IDD** elementu członkowskiego, który określa identyfikator zasobu szablonu okna dialogowego. Na przykład Kreator projektu ATL automatycznie dodaje następujący wiersz do klasy:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/cdialogimpl-class_1.h)]  
  
 gdzie `MyDlg` jest **krótką nazwę** wprowadzona w kreatorze **nazwy** strony.  
  
|Aby uzyskać więcej informacji dotyczących|Zobacz|  
|--------------------------------|---------|  
|Tworzenie formantów|[ALT — samouczek](../../atl/active-template-library-atl-tutorial.md)|  
|Za pomocą okien dialogowych w ATL|[Klasy okien ATL](../../atl/atl-window-classes.md)|  
|Kreator projektu ATL|[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)|  
|Okna dialogowe|[Okna dialogowe](http://msdn.microsoft.com/library/windows/desktop/ms632588) i kolejnych tematach w zestawie SDK systemu Windows|  
  
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
 `hWndParent`  
 [in] Dojście do okna nadrzędnego.  
  
 **RECT &AMP;** `rect`  
 [in] A [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) Struktura określająca rozmiar i położenie okna dialogowego.  
  
 `dwInitParam`  
 [in] Określa wartość do przekazania do okna dialogowego w **lParam** parametr **WM_INITDIALOG** wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do okna dialogowego nowo utworzony.  
  
### <a name="remarks"></a>Uwagi  
 To okno dialogowe jest automatycznie dołączane do `CDialogImpl` obiektu. Aby utworzyć modalne okno dialogowe, wywołaj [DoModal](#domodal). Drugi zastąpienie powyżej jest używana tylko z [CComControl](../../atl/reference/ccomcontrol-class.md).  
  
##  <a name="destroywindow"></a>  CDialogImpl::DestroyWindow  
 Niszczy niemodalne okno dialogowe.  
  
```  
 
BOOL DestroyWindow();

 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli okno dialogowe został pomyślnie niszczone; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **TRUE** Jeśli okno dialogowe został pomyślnie niszczone; w przeciwnym razie **FALSE**.  
  
##  <a name="dialogproc"></a>  CDialogImpl::DialogProc  
 Ta funkcja statyczna implementuje procedury — okno dialogowe.  
  
```  
 
static LRESULT CALLBACK DialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam);

 
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [in] Dojście do okna dialogowego.  
  
 `uMsg`  
 [in] Komunikat wysyłany do okna dialogowego.  
  
 `wParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
 `lParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli komunikat jest przetworzonych; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 `DialogProc` używa domyślnej mapy wiadomości do kierowania wiadomości na odpowiednie programy obsługi.  
  
 Można zastąpić `DialogProc` na inny mechanizm obsługi wiadomości.  
  
##  <a name="domodal"></a>  CDialogImpl::DoModal  
 Tworzy modalne okno dialogowe.  
  
```   
INT_PTR DoModal(  
    HWND hWndParent = ::GetActiveWindow(),   
    LPARAM dwInitParam = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [in] Dojście do okna nadrzędnego. Wartość domyślna to wartość zwracana [GetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646292) funkcji Win32.  
  
 `dwInitParam`  
 [in] Określa wartość do przekazania do okna dialogowego w **lParam** parametr **WM_INITDIALOG** wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia wartość `nRetCode` parametr w wywołaniu [EndDialog](#enddialog). W przeciwnym razie wartość -1.  
  
### <a name="remarks"></a>Uwagi  
 To okno dialogowe jest automatycznie dołączane do `CDialogImpl` obiektu.  
  
 Aby utworzyć niemodalne okno dialogowe, wywołaj [Utwórz](#create).  
  
##  <a name="enddialog"></a>  CDialogImpl::EndDialog  
 Niszczy modalne okno dialogowe.  
  
```   
BOOL EndDialog(int nRetCode); 
```  
  
### <a name="parameters"></a>Parametry  
 `nRetCode`  
 [in] Wartość zwracana przez [CDialogImpl::DoModal](#domodal).  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli okno dialogowe jest niszczone; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 `EndDialog` musi zostać wywołany przez procedurę okna dialogowego. Po niszczenie okna dialogowego systemu Windows używa wartości `nRetCode` jako wartości zwracane dla `DoModal`, które utworzone okno dialogowe.  
  
> [!NOTE]
>  Nie wywołuj `EndDialog` do zniszczenia niemodalne okno dialogowe. Wywołanie [CWindow::DestroyWindow](../../atl/reference/cwindow-class.md#destroywindow) zamiast tego.  
  
##  <a name="getdialogproc"></a>  CDialogImpl::GetDialogProc  
 Zwraca `DialogProc`, bieżącą procedurę okno dialogowe.  
  
```   
virtual WNDPROC GetDialogProc(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżącej procedurze okno dialogowe.  
  
### <a name="remarks"></a>Uwagi  
 Zastępuje tę metodę, aby zastąpić procedurę okna dialogowego swoją własną.  
  
##  <a name="mapdialogrect"></a>  CDialogImpl::MapDialogRect  
 Konwertuje (maps) jednostki okno dialogowe określonego prostokąta do ekranu jednostki (w pikselach).  
  
```   
BOOL MapDialogRect(LPRECT lpRect); 
```  
  
### <a name="parameters"></a>Parametry  
 `lpRect`  
 Wskazuje `CRect` obiektu lub [RECT](../../mfc/reference/rect-structure1.md) struktury, który ma otrzymać współrzędne klienta aktualizacji, które umieszcza region aktualizacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli aktualizacja zakończy się pomyślnie; 0, jeśli aktualizacja nie powiedzie się. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać `GetLastError`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zastępuje współrzędnych w określonym `RECT` struktury z przekonwertowanego współrzędne, dzięki czemu struktury ma być używany do tworzenie okna dialogowego lub położenie formantu w oknie dialogowym.  
  
##  <a name="onfinalmessage"></a>  CDialogImpl::OnFinalMessage  
 Wywołuje się po otrzymaniu ostatniego komunikatu (zazwyczaj `WM_NCDESTROY`).  
  
```   
virtual void OnFinalMessage(HWND hWnd); 
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [in] Dojście do okna zostaną zniszczone.  
  
### <a name="remarks"></a>Uwagi  
 Należy zauważyć, że jeśli chcesz automatycznie usunąć obiekt na zniszczenie okna, można wywołać `delete this;` tutaj.  
  
##  <a name="startdialogproc"></a>  CDialogImpl::StartDialogProc  
 Wywołana tylko raz, po odebraniu pierwszego komunikatu, aby przetwarzać komunikaty wysyłane do okna dialogowego.  
  
```   
static LRESULT CALLBACK StartDialogProc(
    HWND hWnd,  
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam); 
```  
  
### <a name="parameters"></a>Parametry  
 `hWnd`  
 [in] Dojście do okna dialogowego.  
  
 `uMsg`  
 [in] Komunikat wysyłany do okna dialogowego.  
  
 `wParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
 `lParam`  
 [in] Dodatkowe informacje specyficzne dla wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Procedurę okna.  
  
### <a name="remarks"></a>Uwagi  
 Po początkowym wywołaniu `StartDialogProc`, `DialogProc` jest ustawiony jako procedurę okna dialogowego i późniejszych wywołaniach na tej stronie.  
  
## <a name="see-also"></a>Zobacz też  
 [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)   
 [Przegląd klas](../../atl/atl-class-overview.md)