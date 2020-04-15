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
ms.openlocfilehash: 3518de3596748fa284c1f898b69d1576903e9510
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320769"
---
# <a name="ccomcontrol-class"></a>Klasa CComControl

Ta klasa zawiera metody tworzenia formantów ATL i zarządzania nimi.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class WinBase = CWindowImpl<T>>
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Klasa implementująca formant.

*Baza danych WinBase*<br/>
Klasa podstawowa, która implementuje funkcje okna. Wartość domyślna to [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControl::CComControl](#ccomcontrol)|Konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Pobiera wskaźnik do żądanego interfejsu.|
|[CComControl::CreateControlWindow](#createcontrolwindow)|Tworzy okno dla formantu.|
|[CComControl::FireOnChanged](#fireonchanged)|Powiadamia ujście kontenera, że właściwość formantu została zmieniona.|
|[CComControl::FireOnRequestEdytuj](#fireonrequestedit)|Powiadamia ujście kontenera, że właściwość formantu ma się zmienić i że obiekt pyta zniejmowca, jak postępować.|
|[CComControl::MessageBox](#messagebox)|Wywołanie tej metody, aby utworzyć, wyświetlić i obsługiwać okno komunikatu.|

## <a name="remarks"></a>Uwagi

`CComControl`to zestaw przydatnych funkcji pomocnika sterowania i podstawowych elementów członkowskich danych dla formantów ATL. Podczas tworzenia formantu standardowego lub kontrolki DHTML za pomocą Kreatora sterowania `CComControl`ATL kreator automatycznie wyprowadzi klasę z programu . `CComControl`większość jego metod pochodzi z [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).

Aby uzyskać więcej informacji na temat tworzenia formantu, zobacz [samouczek ATL](../../atl/active-template-library-atl-tutorial.md). Aby uzyskać więcej informacji na temat Kreatora projektów ATL, zobacz artykuł [Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md).

Aby zapoznać `CComControl` się z demonstracją metod i elementów członkowskich danych, zobacz przykład [CIRC.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`WinBase`

[Baza CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

`CComControl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlctl.h

## <a name="ccomcontrolccomcontrol"></a><a name="ccomcontrol"></a>CComControl::CComControl

Konstruktor.

```
CComControl();
```

### <a name="remarks"></a>Uwagi

Wywołuje konstruktor [cComControlBase,](ccomcontrolbase-class.md#ccomcontrolbase) przekazując element członkowski `m_hWnd` danych dziedziczony za pośrednictwem [CWindowImpl](../../atl/reference/cwindowimpl-class.md).

## <a name="ccomcontrolcontrolqueryinterface"></a><a name="controlqueryinterface"></a>CComControl::ControlQueryInterface

Pobiera wskaźnik do żądanego interfejsu.

```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[w] Identyfikator GUID żądanego interfejsu.

*Ppv*<br/>
[na zewnątrz] Wskaźnik do wskaźnika interfejsu identyfikowanego przez *iid*lub NULL, jeśli interfejs nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Obsługuje tylko interfejsy w tabeli mapy COM.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]

## <a name="ccomcontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComControl::CreateControlWindow

Domyślnie tworzy okno dla formantu, wywołując `CWindowImpl::Create`program .

```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```

### <a name="parameters"></a>Parametry

*hWndRodziciek*<br/>
[w] Dojście do okna nadrzędnego lub właściciela. Należy podać prawidłowy uchwyt okna. Okno kontrolne jest ograniczone do obszaru jego okna nadrzędnego.

*z o.o.*<br/>
[w] Początkowy rozmiar i położenie okna, które ma zostać utworzone.

### <a name="remarks"></a>Uwagi

Zastąp tę metodę, jeśli chcesz zrobić coś innego niż utworzyć pojedyncze okno, na przykład, aby utworzyć dwa okna, z których jeden staje się paskiem narzędzi dla formantu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]

## <a name="ccomcontrolfireonchanged"></a><a name="fireonchanged"></a>CComControl::FireOnChanged

Powiadamia ujście kontenera, że właściwość formantu została zmieniona.

```
HRESULT FireOnChanged(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
[w] Identyfikator właściwości, która uległa zmianie.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli klasa formantu pochodzi od [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), ta metoda wywołuje [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) powiadomić wszystkie połączone `IPropertyNotifySink` interfejsy, że określona właściwość formantu została zmieniona. Jeśli klasa kontroli nie pochodzi `IPropertyNotifySink`od , ta metoda zwraca S_OK.

Ta metoda jest bezpieczna do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]

## <a name="ccomcontrolfireonrequestedit"></a><a name="fireonrequestedit"></a>CComControl::FireOnRequestEdytuj

Powiadamia ujście kontenera, że właściwość formantu ma się zmienić i że obiekt pyta zniejmowca, jak postępować.

```
HRESULT FireOnRequestEdit(DISPID dispID);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
[w] Identyfikator właściwości, która ma ulec zmianie.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli klasa formantu pochodzi od [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink), ta metoda wywołuje [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) powiadomić wszystkie połączone `IPropertyNotifySink` interfejsy, że określona właściwość control ma się zmienić. Jeśli klasa kontroli nie pochodzi `IPropertyNotifySink`od , ta metoda zwraca S_OK.

Ta metoda jest bezpieczna do wywołania, nawet jeśli formant nie obsługuje punktów połączenia.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]

## <a name="ccomcontrolmessagebox"></a><a name="messagebox"></a>CComControl::MessageBox

Wywołanie tej metody, aby utworzyć, wyświetlić i obsługiwać okno komunikatu.

```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Tekst, który ma być wyświetlany w oknie komunikatu.

*lpszCaption (własnowie)*<br/>
Tytuł okna dialogowego. Jeśli null (wartość domyślna), używany jest tytuł "Błąd".

*nTyp*<br/>
Określa zawartość i zachowanie okna dialogowego. Zobacz wpis [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) w dokumentacji zestawie Windows SDK, aby uzyskać listę dostępnych różnych okien komunikatów. Wartość domyślna zapewnia prosty przycisk **OK.**

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość całkowitą określającą jedną z wartości elementu menu wymienionych w obszarze [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) w dokumentacji zestawu Windows SDK.

### <a name="remarks"></a>Uwagi

`MessageBox`jest przydatna zarówno podczas tworzenia, jak i jako łatwy sposób wyświetlania użytkownikowi komunikatu o błędzie lub ostrzeżeniu.

## <a name="see-also"></a>Zobacz też

[Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComControlBase](../../atl/reference/ccomcontrolbase-class.md)<br/>
[Klasa CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)
