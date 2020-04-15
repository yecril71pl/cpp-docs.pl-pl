---
title: Klasa CWinFormsView
ms.date: 11/04/2016
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
ms.openlocfilehash: 6eb6b9e385e9dbc96eb3b62ffb80909e54569e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369603"
---
# <a name="cwinformsview-class"></a>Klasa CWinFormsView

Zapewnia ogólne funkcje hostingu formantu Windows Forms jako widoku MFC.

## <a name="syntax"></a>Składnia

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|Konstruuje `CWinFormsView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|Pobiera wskaźnik do formantu Windows Forms.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa||
|----------|-|
|[CWinFormsView::kontrola operatora^](#operator_control)|Rzutuje typ jako wskaźnik do formantu Windows Forms.|

## <a name="remarks"></a>Uwagi

MFC używa `CWinFormsView` klasy do hosta .NET Framework Windows Forms form formantu w widoku MFC. Formant jest podrzędnym widoku macierzystego i zajmuje cały obszar klienta widoku MFC. Wynik jest podobny `CFormView` do widoku, co pozwala na korzystanie z projektanta formularzy systemu Windows i czasu wykonywania w celu utworzenia widoków opartych na formularzach.

Aby uzyskać więcej informacji na temat korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
> Integracja formularzy systemu Windows MFC działa tylko w projektach, które łączą się dynamicznie z MFC (projekty, w których jest zdefiniowana afxdll).

> [!NOTE]
> CWinFormsView nie obsługuje okna rozdzielacza MFC ( [CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)). Obecnie obsługiwany jest tylko formant rozdzielacza formularzy systemu Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a>CWinFormsView::CWinFormsView

Konstruuje `CWinFormsView` obiekt.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parametry

*pManagedViewType*<br/>
Wskaźnik do typu danych formantu użytkownika formularzy systemu Windows.

### <a name="example"></a>Przykład

W `CUserView` poniższym przykładzie klasa `CWinFormsView` dziedziczy i `UserControl1` przekazuje `CWinFormsView` typ do konstruktora. `UserControl1`jest specjalnie zbudowanym formantem w pliku ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a>CWinFormsView::GetControl

Pobiera wskaźnik do formantu Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `System.Windows.Forms.Control` obiektu.

### <a name="remarks"></a>Uwagi

Aby uzyskać przykład użycia formularzy systemu Windows, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a>CWinFormsView::kontrola operatora^

Rzutuje typ jako wskaźnik do formantu Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Uwagi

Ten operator umożliwia przekazywanie `CWinFormsView` widoku do funkcji, które akceptują <xref:System.Windows.Forms.Control>wskaźnik do formantu typu Windows Forms .

### <a name="example"></a>Przykład

  Zobacz [CWinFormsView::GetControl](#getcontrol).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)<br/>
[Klasa CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)
