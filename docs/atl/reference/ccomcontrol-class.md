---
title: Klasa CComControl
ms.date: 11/04/2016
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
ms.openlocfilehash: bf0f64d8c7b8e8a3347e4c0fcad902b9e8a0ecb4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497533"
---
# <a name="ccomcontrol-class"></a>Klasa CComControl

Ta klasa udostępnia metody tworzenia formantów ATL i zarządzania nimi.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa implementująca formant.

*WinBase*<br/>
Klasa bazowa, która implementuje funkcje okna. Wartość domyślna to [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Tworzy okno dla kontrolki.|
|[CComControl::FireOnChanged](#fireonchanged)|Powiadamia ujścia kontenera o zmianie właściwości kontrolki.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Powiadamia ujścia kontenera, że właściwość kontrolki ma zostać zmieniona i że obiekt żąda ujścia, jak to zrobić.|
|[CComControl::MessageBox](#messagebox)|Wywołaj tę metodę, aby utworzyć, wyświetlić i obsłużyć okno komunikatu.|

## <a name="remarks"></a>Uwagi

`CComControl`jest zestawem przydatnych funkcji pomocnika kontroli i najważniejszych elementów członkowskich danych dla formantów ATL. Podczas tworzenia kontrolki standardowej lub kontrolki DHTML przy użyciu kreatora kontrolki ATL, Kreator automatycznie utworzy klasę z `CComControl`. `CComControl`wynika z większości metod z [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Aby uzyskać więcej informacji na temat tworzenia kontrolki, zobacz [samouczek ATL](../../atl/active-template-library-atl-tutorial.md). Aby uzyskać więcej informacji na temat Kreatora projektu ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

Aby zapoznać się z `CComControl` przykładami metod i składowych danych, zobacz [cykl](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl. h

##  <a name="ccomcontrol"></a>CComControl::CComControl

Konstruktor.

```
CComControl();
```

### <a name="remarks"></a>Uwagi

Wywołuje Konstruktor [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) , przekazując `m_hWnd` element członkowski danych Dziedziczony za pomocą [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

##  <a name="controlqueryinterface"></a>CComControl::ControlQueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
podczas Identyfikator GUID żądanego interfejsu.

*ppv*<br/>
określoną Wskaźnik do wskaźnika interfejsu identyfikowanego przez *Identyfikator IID*lub wartość null, jeśli nie można odnaleźć interfejsu.

### <a name="remarks"></a>Uwagi

Obsługuje tylko interfejsy w tabeli mapy COM.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow

Domyślnie program tworzy okno dla formantu przez wywołanie `CWindowImpl::Create`.

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
podczas Dojście do okna nadrzędnego lub właściciela. Należy podać prawidłowe dojście do okna. Okno sterowania jest ograniczone do obszaru okna nadrzędnego.

*rcPos*<br/>
podczas Początkowy rozmiar i położenie okna, które ma zostać utworzone.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, jeśli chcesz zrobić coś innego niż Utwórz pojedyncze okno, na przykład, aby utworzyć dwa okna, jeden z nich jest paskiem narzędzi dla kontrolki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>CComControl::FireOnChanged

Powiadamia ujścia kontenera o zmianie właściwości kontrolki.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*dispID*<br/>
podczas Identyfikator właściwości, która została zmieniona.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli Klasa formantów pochodzi z [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), ta metoda wywołuje [CFirePropNotifyEvent:: FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) , aby powiadomić wszystkie `IPropertyNotifySink` połączone interfejsy o zmianie określonej właściwości kontrolki. Jeśli Klasa kontroli nie pochodzi od `IPropertyNotifySink`, metoda zwraca S_OK.

Ta metoda jest bezpieczna do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit

Powiadamia ujścia kontenera, że właściwość kontrolki ma zostać zmieniona i że obiekt żąda ujścia, jak to zrobić.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*dispID*<br/>
podczas Identyfikator właściwości, która ma zostać zmieniona.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli Klasa formantów pochodzi z [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), ta metoda wywołuje [CFirePropNotifyEvent:: FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) , aby powiadomić wszystkie `IPropertyNotifySink` połączone interfejsy o zmianie określonej właściwości kontrolki. Jeśli Klasa kontroli nie pochodzi od `IPropertyNotifySink`, metoda zwraca S_OK.

Ta metoda jest bezpieczna do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>CComControl:: MessageBox

Wywołaj tę metodę, aby utworzyć, wyświetlić i obsłużyć okno komunikatu.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Tekst, który będzie wyświetlany w oknie komunikatu.

*lpszCaption*<br/>
Tytuł okna dialogowego. Jeśli wartość jest równa NULL (wartość domyślna), jest używany tytuł "Error".

*Npowiadomienia*<br/>
Określa zawartość i zachowanie okna dialogowego. Zapoznaj się z wpisem [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) w dokumentacji Windows SDK, aby wyświetlić listę różnych dostępnych okien komunikatów. Domyślnie jest dostępny prosty przycisk **OK** .

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę całkowitą określającą jedną z wartości elementów menu wyświetlaną w obszarze [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) w dokumentacji Windows SDK.

### <a name="remarks"></a>Uwagi

`MessageBox`jest przydatne zarówno podczas opracowywania, jak i w prosty sposób, aby wyświetlić błąd lub komunikat ostrzegawczy użytkownika.

## <a name="see-also"></a>Zobacz także

[Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComControlBase](../../atl/reference/ccomcontrolbase-class.md)<br/>
[Klasa CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)
