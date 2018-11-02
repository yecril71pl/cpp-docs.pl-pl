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
ms.openlocfilehash: 3fe01128fc5f0a9d3058df2d6f95a6c038b28062
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644200"
---
# <a name="ccomcontrol-class"></a>Klasa CComControl

Ta klasa dostarcza metody do tworzenia i zarządzania formantami ATL.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa Implementowanie formantu.

*WinBase*<br/>
Klasa bazowa implementuje funkcji obsługi okien. Wartość domyślna to [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Tworzy okno, dla formantu.|
|[CComControl::FireOnChanged](#fireonchanged)|Powiadamia obiekt sink kontenera, które uległy zmianie właściwości formantu.|
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Powiadamia obiekt sink kontenera, gdy dla właściwości kontrolki zostanie zmienione i czy obiekt jest zapytaniem ujścia dalszego postępowania.|
|[CComControl::MessageBox](#messagebox)|Wywołaj tę metodę w celu tworzenia, wyświetlania i obsługiwanie okno komunikatu.|

## <a name="remarks"></a>Uwagi

`CComControl` to zestaw funkcji pomocnika przydatne kontroli i elementy członkowskie danych istotnych dla kontrolek ATL. Podczas tworzenia kontrolki standardowej lub kontrolki DHTML przy użyciu kreator kontrolki ATL, Kreator automatycznie, z której pochodzą z klasy `CComControl`. `CComControl` wywodzi się większość jego metody z [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Aby uzyskać więcej informacji na temat tworzenia kontrolki zobacz [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md). Aby uzyskać więcej informacji na temat Kreator projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

Do pokazania `CComControl` metod i składowych danych, zobacz [OK](../../visual-cpp-samples.md) próbki.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

##  <a name="ccomcontrol"></a>  CComControl::CComControl

Konstruktor.

```
CComControl();
```

### <a name="remarks"></a>Uwagi

Wywołania [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) konstruktora, przekazując `m_hWnd` element członkowski danych dziedziczone [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

##  <a name="controlqueryinterface"></a>  CComControl::ControlQueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parametry

*IID*<br/>
[in] Identyfikator GUID interfejsu żądanej.

*ppv*<br/>
[out] Wskaźnik do wskaźnika interfejsu identyfikowane przez *iid*, lub wartość NULL, jeśli nie można odnaleźć interfejsu.

### <a name="remarks"></a>Uwagi

obsługuje tylko interfejsów COM tabeli mapy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

##  <a name="createcontrolwindow"></a>  CComControl::CreateControlWindow

Domyślnie tworzy okna dla kontrolki, wywołując `CWindowImpl::Create`.

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndParent*<br/>
[in] Dojście do okna nadrzędnego lub właściciela. Należy podać prawidłowy uchwyt okna. Okno kontrolki jest ograniczona do obszaru okna nadrzędnego.

*rcPos*<br/>
[in] Początkowy rozmiar i położenie okna, które ma zostać utworzony.

### <a name="remarks"></a>Uwagi

Przesłonić tę metodę, jeśli chcesz zrobić coś innego niż tworzenie jednego okna, na przykład aby utworzyć dwa okna, z których jedna staje się pasek narzędzi dla formantu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

##  <a name="fireonchanged"></a>  CComControl::FireOnChanged

Powiadamia obiekt sink kontenera, które uległy zmianie właściwości formantu.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*dispID*<br/>
[in] Identyfikator właściwości, które uległy zmianie.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Jeśli pochodną klasy kontrolki [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink), ta metoda wywołuje [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) powiadomić wszystkich połączonych `IPropertyNotifySink` interfejsów określoną kontrolkę Właściwość zostanie zmieniona. Jeśli nie jest pochodną klasy kontrolki `IPropertyNotifySink`, ta metoda zwraca wartość S_OK.

Ta metoda jest bezpieczny do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

##  <a name="fireonrequestedit"></a>  CComControl::FireOnRequestEdit

Powiadamia obiekt sink kontenera, gdy dla właściwości kontrolki zostanie zmienione i czy obiekt jest zapytaniem ujścia dalszego postępowania.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*dispID*<br/>
[in] Identyfikator właściwości, które chcesz zmienić.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Jeśli pochodną klasy kontrolki [ipropertynotifysink —](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink), ta metoda wywołuje [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) powiadomić wszystkich połączonych `IPropertyNotifySink` interfejsów określonego właściwości kontrolki zostanie zmienione. Jeśli nie jest pochodną klasy kontrolki `IPropertyNotifySink`, ta metoda zwraca wartość S_OK.

Ta metoda jest bezpieczny do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

##  <a name="messagebox"></a>  CComControl::MessageBox

Wywołaj tę metodę w celu tworzenia, wyświetlania i obsługiwanie okno komunikatu.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Tekst, który ma być wyświetlany w oknie komunikatu.

*lpszCaption*<br/>
Tytuł okna dialogowego. Jeśli wartość NULL (ustawienie domyślne), tytuł "Error" jest używany.

*nNie*<br/>
Określa zawartość i zachowanie okna dialogowego. Zobacz [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) wpisu w dokumentacji zestawu SDK Windows listę dostępnych pól inny komunikat. Wartość domyślna zapewnia prosty **OK** przycisku.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość całkowitą określającą jedną z wartości element menu na liście [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) w dokumentacji zestawu Windows SDK.

### <a name="remarks"></a>Uwagi

`MessageBox` jest przydatne zarówno podczas tworzenia, jak i w prosty sposób, aby wyświetlić błąd lub ostrzeżenie dla użytkownika.

## <a name="see-also"></a>Zobacz też

[Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa CComControlBase](../../atl/reference/ccomcontrolbase-class.md)<br/>
[Klasa CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)
