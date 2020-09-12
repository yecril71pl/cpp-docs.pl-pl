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
ms.openlocfilehash: 3c247babd2ec1057f1e24b8132ed81727a0fd402
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040655"
---
# <a name="cwinformsview-class"></a>Klasa CWinFormsView

Udostępnia funkcje ogólne do hostowania formantu Windows Forms jako widoku MFC.

## <a name="syntax"></a>Składnia

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsView:: CWinFormsView](#cwinformsview)|Konstruuje `CWinFormsView` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsView:: GetControl](#getcontrol)|Pobiera wskaźnik do kontrolki Windows Forms.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-|
|[CWinFormsView:: operator — formant ^](#operator_control)|Rzutuje typ jako wskaźnik do kontrolki Windows Forms.|

## <a name="remarks"></a>Uwagi

MFC używa `CWinFormsView` klasy do hostowania kontrolki Windows Forms .NET Framework w widoku MFC. Kontrolka jest elementem podrzędnym widoku natywnego i zajmuje cały obszar klienta widoku MFC. Wynik jest podobny do `CFormView` widoku, co umożliwia skorzystanie z projektanta Windows Forms i czasu wykonywania w celu tworzenia zaawansowanych widoków opartych na formularzach.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
> Integracja MFC Windows Forms działa tylko w projektach, które łączą się dynamicznie z MFC (projekty, w których zdefiniowano AFXDLL).

> [!NOTE]
> CWinFormsView nie obsługuje okna rozdzielacza MFC ( [Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)). Obecnie jest obsługiwana tylko Windows Forms kontrolka rozdzielacza.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms. h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a> CWinFormsView:: CWinFormsView

Konstruuje `CWinFormsView` obiekt.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parametry

*pManagedViewType*<br/>
Wskaźnik do typu danych kontrolki użytkownika Windows Forms.

### <a name="example"></a>Przykład

W poniższym przykładzie `CUserView` Klasa dziedziczy po `CWinFormsView` i przekazuje typ `UserControl1` do `CWinFormsView` konstruktora. `UserControl1` jest kontrolką wbudowaną niestandardową w ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a> CWinFormsView:: GetControl

Pobiera wskaźnik do kontrolki Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `System.Windows.Forms.Control` obiektu.

### <a name="remarks"></a>Uwagi

Aby zapoznać się z przykładem korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a> CWinFormsView:: operator — formant ^

Rzutuje typ jako wskaźnik do kontrolki Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Uwagi

Ten operator umożliwia przekazanie `CWinFormsView` widoku do funkcji, które akceptują wskaźnik do kontrolki Windows Forms typu <xref:System.Windows.Forms.Control> .

### <a name="example"></a>Przykład

  Zobacz [CWinFormsView:: GetControl](#getcontrol).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)<br/>
[Klasa CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)
