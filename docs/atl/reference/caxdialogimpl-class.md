---
title: Klasa CAxDialogImpl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CAxDialogImpl class
- ATL, dialog boxes
ms.assetid: 817df483-3fa8-44e7-8487-72ba0881cd27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3e1b7d4f88428060f4aa4d01180bce1e970b650
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365080"
---
# <a name="caxdialogimpl-class"></a>Klasa CAxDialogImpl
Ta klasa implementuje okno dialogowe (modalne i niemodalne) obsługującego formantów ActiveX.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, class TBase = CWindow>  
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Z klasą pochodną `CAxDialogImpl`.  
  
 *TBase*  
 Klasa podstawowa okna dla **CDialogImplBaseT**.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Wywołaj tę metodę w celu poinformowania lub unadvise wszystkie wpisy obiektu sink mapy zdarzeń mapy.|  
|[CAxDialogImpl::Create](#create)|Wywołaj tę metodę, aby utworzyć niemodalne okno dialogowe.|  
|[CAxDialogImpl::DestroyWindow](#destroywindow)|Wywołanie tej metody można zniszczyć niemodalne okno dialogowe.|  
|[CAxDialogImpl::DoModal](#domodal)|Wywołaj tę metodę, aby utworzyć modalne okno dialogowe.|  
|[CAxDialogImpl::EndDialog](#enddialog)|Wywołanie tej metody można zniszczyć modalne okno dialogowe.|  
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Wywołanie tej metody, aby uzyskać wskaźnik do `DialogProc` funkcja wywołania zwrotnego.|  
|[CAxDialogImpl::GetIDD](#getidd)|Wywołanie tej metody, aby uzyskać identyfikator zasobu szablonu okna dialogowego|  
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Wywołanie tej metody, aby określić, czy wiadomość jest przeznaczony dla tego okna dialogowego, a jeśli tak jest, przetworzyć komunikatu.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAxDialogImpl::m_bModal](#m_bmodal)|Zmienna, która istnieje tylko w przypadku debugowania kompilacje i jest ustawiona na wartość true, jeśli jest modalne okno dialogowe.|  
  
## <a name="remarks"></a>Uwagi  
 `CAxDialogImpl` Służy do tworzenia modalne i niemodalne okno dialogowe. `CAxDialogImpl` zawiera procedury okno dialogowe używa domyślnej mapy wiadomości do kierowania wiadomości na odpowiednie programy obsługi.  
  
 `CAxDialogImpl` pochodną `CDialogImplBaseT`, który z kolei jest pochodną *TBase* (domyślnie `CWindow`) i `CMessageMap`.  
  
 Klasa musi definiować IDD elementu członkowskiego, który określa identyfikator zasobu szablonu okna dialogowego. Na przykład dodawanie obiektu okna dialogowego ATL przy użyciu **Dodaj klasę** okno dialogowe automatycznie dodaje następujący wiersz do klasy:  
  
 [!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]  
  
 gdzie `MyDialog` jest **krótką nazwę** wprowadzone w Kreatorze okna dialogowego ATL.  
  
 Zobacz [implementacja okno dialogowe](../../atl/implementing-a-dialog-box.md) Aby uzyskać więcej informacji.  
  
 Należy pamiętać, że utworzone za pomocą formantu ActiveX na modalne okno dialogowe `CAxDialogImpl` nie będzie obsługiwał klawiszy skrótów. Do obsługi klawisze skrótów w oknie dialogowym utworzone za pomocą `CAxDialogImpl`, niemodalne okno dialogowe Tworzenie i używanie własnych pętli komunikatów, należy użyć [CAxDialogImpl::IsDialogMessage](#isdialogmessage) po otrzymaniu komunikatu z kolejki, do obsługi klawisz skrótu.  
  
 Aby uzyskać więcej informacji na temat `CAxDialogImpl`, zobacz [— często zadawane pytania ATL kontroli zawierania](../../atl/atl-control-containment-faq.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CDialogImplBaseT`  
  
 `CAxDialogImpl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlwin.h  
  
##  <a name="advisesinkmap"></a>  CAxDialogImpl::AdviseSinkMap  
 Wywołaj tę metodę w celu poinformowania lub unadvise wszystkie wpisy obiektu sink mapy zdarzeń mapy.  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>Parametry  
 `bAdvise`  
 Ustaw wartość true, jeśli wszystkie wpisy zbiornika zaleceniem; zbiornik wartość false, jeśli wszystkie wpisy są unadvised.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku awarii.  
  
##  <a name="create"></a>  CAxDialogImpl::Create  
 Wywołaj tę metodę, aby utworzyć niemodalne okno dialogowe.  
  
```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [in] Dojście do okna nadrzędnego.  
  
 `dwInitParam`  
 [in] Określa wartość do przekazania do okna dialogowego w `lParam` parametr **WM_INITDIALOG** wiadomości.  
  
 **RECT &AMP;**  
 Ten parametr nie jest używany. Ten parametr jest przekazywany w `CComControl`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do okna dialogowego nowo utworzony.  
  
### <a name="remarks"></a>Uwagi  
 To okno dialogowe jest automatycznie dołączane do `CAxDialogImpl` obiektu. Aby utworzyć modalne okno dialogowe, wywołaj [DoModal](#domodal).  
  
 Zastąpienie drugi jest dostępne tylko, okna dialogowe mogą być używane z [CComControl](../../atl/reference/ccomcontrol-class.md).  
  
##  <a name="destroywindow"></a>  CAxDialogImpl::DestroyWindow  
 Wywołanie tej metody można zniszczyć niemodalne okno dialogowe.  
  
```
BOOL DestroyWindow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli okno pomyślnie zostanie zniszczony; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 Nie wywołuj `DestroyWindow` do zniszczenia modalne okno dialogowe. Wywołanie [EndDialog](#enddialog) zamiast tego.  
  
##  <a name="domodal"></a>  CAxDialogImpl::DoModal  
 Wywołaj tę metodę, aby utworzyć modalne okno dialogowe.  
  
```
INT_PTR DoModal(
  HWND hWndParent = ::GetActiveWindow(), 
  LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [in] Dojście do okna nadrzędnego. Wartość domyślna to wartość zwracana [GetActiveWindow](http://msdn.microsoft.com/library/windows/desktop/ms646292) funkcji Win32.  
  
 `dwInitParam`  
 [in] Określa wartość do przekazania do okna dialogowego w `lParam` parametr **WM_INITDIALOG** wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia wartość `nRetCode` parametr w wywołaniu [EndDialog](#enddialog); w przeciwnym razie wartość -1.  
  
### <a name="remarks"></a>Uwagi  
 To okno dialogowe jest automatycznie dołączane do `CAxDialogImpl` obiektu.  
  
 Aby utworzyć niemodalne okno dialogowe, wywołaj [Utwórz](#create).  
  
##  <a name="enddialog"></a>  CAxDialogImpl::EndDialog  
 Wywołanie tej metody można zniszczyć modalne okno dialogowe.  
  
```
BOOL EndDialog(int nRetCode);
```  
  
### <a name="parameters"></a>Parametry  
 `nRetCode`  
 [in] Wartość zwracana przez [DoModal](#domodal).  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli okno zostanie zniszczone; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 `EndDialog` musi zostać wywołana za pomocą procedury — okno dialogowe. Po niszczenie okna dialogowego systemu Windows używa wartości `nRetCode` jako wartości zwracane dla `DoModal`, które utworzone okno dialogowe.  
  
> [!NOTE]
>  Nie wywołuj `EndDialog` do zniszczenia niemodalne okno dialogowe. Wywołanie [DestroyWindow](#destroywindow) zamiast tego.  
  
##  <a name="getdialogproc"></a>  CAxDialogImpl::GetDialogProc  
 Wywołanie tej metody, aby uzyskać wskaźnik do `DialogProc` funkcja wywołania zwrotnego.  
  
```
virtual DLGPROC GetDialogProc();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do `DialogProc` funkcja wywołania zwrotnego.  
  
### <a name="remarks"></a>Uwagi  
 `DialogProc` Funkcja jest funkcją zdefiniowanym przez aplikację wywołania zwrotnego.  
  
##  <a name="getidd"></a>  CAxDialogImpl::GetIDD  
 Wywołanie tej metody można pobrać identyfikatora zasobu szablonu okna dialogowego.  
  
```
int GetIDD();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca identyfikator zasobu szablonu okna dialogowego.  
  
##  <a name="isdialogmessage"></a>  CAxDialogImpl::IsDialogMessage  
 Wywołanie tej metody, aby określić, czy wiadomość jest przeznaczony dla tego okna dialogowego, a jeśli tak jest, przetworzyć komunikatu.  
  
```
BOOL IsDialogMessage(LPMSG pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Wskaźnik do [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) struktury, która zawiera komunikat, który ma być sprawdzane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli komunikat zostało przetworzone, wartość FALSE w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest przeznaczona do wywoływania z wewnątrz pętli komunikatów.  
  
##  <a name="m_bmodal"></a>  CAxDialogImpl::m_bModal  
 Zmienna, która istnieje tylko w przypadku debugowania kompilacje i jest ustawiona na wartość true, jeśli jest modalne okno dialogowe.  
  
```
bool m_bModal;
```  
  
## <a name="see-also"></a>Zobacz też  
 [Cdialogimpl — klasa](../../atl/reference/cdialogimpl-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
