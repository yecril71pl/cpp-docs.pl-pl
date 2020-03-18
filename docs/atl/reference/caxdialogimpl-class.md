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
ms.openlocfilehash: 548d2aed0644187b4b8dee1e472b581f1f92d6a1
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418014"
---
# <a name="caxdialogimpl-class"></a>Klasa CAxDialogImpl

Ta klasa implementuje okno dialogowe (modalne lub niemodalne), które obsługuje kontrolki ActiveX.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class TBase = CWindow>
class ATL_NO_VTABLE CAxDialogImpl : public CDialogImplBaseT<TBase>
```

#### <a name="parameters"></a>Parametry

*&*<br/>
Klasa, która pochodzi od `CAxDialogImpl`.

*TBase*<br/>
Klasa okna podstawowego dla `CDialogImplBaseT`.

## <a name="members"></a>Members

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CAxDialogImpl::AdviseSinkMap](#advisesinkmap)|Wywołaj tę metodę, aby zalecić lub nielecić wszystkich wpisów w mapie zdarzeń mapy ujścia obiektu.|
|[CAxDialogImpl:: Create](#create)|Wywołaj tę metodę, aby utworzyć niemodalne okno dialogowe.|
|[CAxDialogImpl::D estroyWindow](#destroywindow)|Wywołaj tę metodę, aby zniszczyć niemodalne okno dialogowe.|
|[CAxDialogImpl::D oModal](#domodal)|Wywołaj tę metodę, aby utworzyć modalne okno dialogowe.|
|[CAxDialogImpl:: zdarzenie EndDialog](#enddialog)|Wywołaj tę metodę, aby zniszczyć modalne okno dialogowe.|
|[CAxDialogImpl::GetDialogProc](#getdialogproc)|Wywołaj tę metodę, aby uzyskać wskaźnik do funkcji wywołania zwrotnego `DialogProc`.|
|[CAxDialogImpl::GetIDD](#getidd)|Wywołaj tę metodę, aby uzyskać identyfikator zasobu szablonu okna dialogowego|
|[CAxDialogImpl::IsDialogMessage](#isdialogmessage)|Wywołaj tę metodę, aby określić, czy komunikat jest przeznaczony dla tego okna dialogowego, a jeśli tak, przetwórz komunikat.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CAxDialogImpl:: m_bModal](#m_bmodal)|Zmienna, która istnieje tylko w kompilacjach debugowania i ma ustawioną wartość true, jeśli okno dialogowe jest modalne.|

## <a name="remarks"></a>Uwagi

`CAxDialogImpl` umożliwia tworzenie modalnych lub niemodalnych okien dialogowych. `CAxDialogImpl` zawiera procedurę okna dialogowego, która używa domyślnej mapy komunikatów do kierowania komunikatów do odpowiednich programów obsługi.

`CAxDialogImpl` pochodzi od `CDialogImplBaseT`, co z kolei wynika z *TBase* (domyślnie `CWindow`) i `CMessageMap`.

Klasa musi definiować element członkowski IDD, który określa identyfikator zasobu szablonu okna dialogowego. Na przykład dodanie obiektu okna dialogowego ATL przy użyciu okna dialogowego **Dodaj klasę** automatycznie dodaje następujący wiersz do klasy:

[!code-cpp[NVC_ATL_Windowing#41](../../atl/codesnippet/cpp/caxdialogimpl-class_1.h)]

gdzie `MyDialog` to **krótka nazwa** wprowadzona w Kreatorze okna dialogowego ATL.

Aby uzyskać więcej informacji, zobacz [implementowanie okna dialogowego](../../atl/implementing-a-dialog-box.md) .

Należy zauważyć, że formant ActiveX w modalnym oknie dialogowym utworzonym przy użyciu `CAxDialogImpl` nie będzie obsługiwał klawiszy akceleratora. Aby zapewnić obsługę klawiszy skrótów w oknie dialogowym utworzonym za pomocą `CAxDialogImpl`, Utwórz niemodalne okno dialogowe i, używając własnej pętli komunikatów, użyj [CAxDialogImpl:: IsDialogMessage](#isdialogmessage) po otrzymaniu komunikatu z kolejki w celu obsługi klawisza skrótu.

Aby uzyskać więcej informacji na temat `CAxDialogImpl`, zobacz temat informacje o [zawieraniu formantów ATL — często zadawane pytania](../../atl/atl-control-containment-faq.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CMessageMap](../../atl/reference/cmessagemap-class.md)

`TBase`

`CWindowImplRoot`

`CDialogImplBaseT`

`CAxDialogImpl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlwin. h

##  <a name="advisesinkmap"></a>CAxDialogImpl::AdviseSinkMap

Wywołaj tę metodę, aby zalecić lub nielecić wszystkich wpisów w mapie zdarzeń mapy ujścia obiektu.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parametry

*bAdvise*<br/>
Ustaw wartość true, jeśli wszystkie wpisy ujścia mają być zalecane; wartość false, jeśli wszystkie wpisy ujścia mają być niezalecane.

### <a name="return-value"></a>Wartość zwrócona

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="create"></a>CAxDialogImpl:: Create

Wywołaj tę metodę, aby utworzyć niemodalne okno dialogowe.

```
HWND Create(HWND hWndParent, LPARAM dwInitParam = NULL);
HWND Create(HWND hWndParent, RECT&, LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
podczas Uchwyt do okna właściciela.

*dwInitParam*<br/>
podczas Określa wartość, która ma zostać przekazana do okna dialogowego w parametrze *lParam* komunikatu WM_INITDIALOG.

*& RECT*<br/>
Ten parametr nie jest używany. Ten parametr jest przesyłany przez `CComControl`.

### <a name="return-value"></a>Wartość zwrócona

Uchwyt do nowo utworzonego okna dialogowego.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie dołączane do obiektu `CAxDialogImpl`. Aby utworzyć modalne okno dialogowe, wywołaj [DoModal](#domodal).

Drugie przesłonięcie jest dostępne tylko wtedy, gdy można używać okien dialogowych z [CComControl](../../atl/reference/ccomcontrol-class.md).

##  <a name="destroywindow"></a>CAxDialogImpl::D estroyWindow

Wywołaj tę metodę, aby zniszczyć niemodalne okno dialogowe.

```
BOOL DestroyWindow();
```

### <a name="return-value"></a>Wartość zwrócona

Ma wartość TRUE, jeśli okno zostanie zniszczone pomyślnie. w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Nie wywołuj `DestroyWindow`, aby zniszczyć modalne okno dialogowe. Zamiast tego wywołaj [zdarzenie EndDialog](#enddialog) .

##  <a name="domodal"></a>CAxDialogImpl::D oModal

Wywołaj tę metodę, aby utworzyć modalne okno dialogowe.

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

### <a name="return-value"></a>Wartość zwrócona

Jeśli to się powiedzie, wartość parametru *nRetCode* określona w wywołaniu [zdarzenie EndDialog](#enddialog); w przeciwnym razie-1.

### <a name="remarks"></a>Uwagi

To okno dialogowe jest automatycznie dołączane do obiektu `CAxDialogImpl`.

Aby utworzyć niemodalne okno dialogowe, wywołaj polecenie [Utwórz](#create).

##  <a name="enddialog"></a>CAxDialogImpl:: zdarzenie EndDialog

Wywołaj tę metodę, aby zniszczyć modalne okno dialogowe.

```
BOOL EndDialog(int nRetCode);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
podczas Wartość, która ma zostać zwrócona przez [DoModal](#domodal).

### <a name="return-value"></a>Wartość zwrócona

PRAWDA, jeśli okno dialogowe zostało zniszczone; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

`EndDialog` należy wywołać za pomocą procedury okna dialogowego. Po zniszczeniu okna dialogowego system Windows używa wartości *nRetCode* jako wartości zwracanej dla `DoModal`, która utworzyła okno dialogowe.

> [!NOTE]
>  Nie wywołuj `EndDialog`, aby zniszczyć niemodalne okno dialogowe. Zamiast tego wywołaj [DestroyWindow](#destroywindow) .

##  <a name="getdialogproc"></a>CAxDialogImpl::GetDialogProc

Wywołaj tę metodę, aby uzyskać wskaźnik do funkcji wywołania zwrotnego `DialogProc`.

```
virtual DLGPROC GetDialogProc();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca wskaźnik do funkcji wywołania zwrotnego `DialogProc`.

### <a name="remarks"></a>Uwagi

Funkcja `DialogProc` jest funkcją wywołania zwrotnego zdefiniowanego przez aplikację.

##  <a name="getidd"></a>CAxDialogImpl::GetIDD

Wywołaj tę metodę, aby uzyskać identyfikator zasobu szablonu okna dialogowego.

```
int GetIDD();
```

### <a name="return-value"></a>Wartość zwrócona

Zwraca identyfikator zasobu szablonu okna dialogowego.

##  <a name="isdialogmessage"></a>CAxDialogImpl::IsDialogMessage

Wywołaj tę metodę, aby określić, czy komunikat jest przeznaczony dla tego okna dialogowego, a jeśli tak, przetwórz komunikat.

```
BOOL IsDialogMessage(LPMSG pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Wskaźnik do struktury [MSG](/windows/win32/api/winuser/ns-winuser-msg) , która zawiera komunikat, który ma zostać sprawdzony.

### <a name="return-value"></a>Wartość zwrócona

Zwraca wartość PRAWDA, jeśli komunikat został przetworzony, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ta metoda jest przeznaczona do wywoływania z poziomu pętli komunikatów.

##  <a name="m_bmodal"></a>CAxDialogImpl:: m_bModal

Zmienna, która istnieje tylko w kompilacjach debugowania i ma ustawioną wartość true, jeśli okno dialogowe jest modalne.

```
bool m_bModal;
```

## <a name="see-also"></a>Zobacz też

[Klasa CDialogImpl](../../atl/reference/cdialogimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
