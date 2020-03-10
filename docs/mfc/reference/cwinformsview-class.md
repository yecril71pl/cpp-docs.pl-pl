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
ms.openlocfilehash: f4a5e6b88527dad8606092ccebd4899bba5181f6
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78872449"
---
# <a name="cwinformsview-class"></a>Klasa CWinFormsView

Udostępnia funkcje ogólne do hostowania formantu Windows Forms jako widoku MFC.

## <a name="syntax"></a>Składnia

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CWinFormsView:: CWinFormsView](#cwinformsview)|Konstruuje obiekt `CWinFormsView`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CWinFormsView:: GetControl](#getcontrol)|Pobiera wskaźnik do kontrolki Windows Forms.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)||
|----------|-|
|[CWinFormsView:: operator — formant ^](#operator_control)|Rzutuje typ jako wskaźnik do kontrolki Windows Forms.|

## <a name="remarks"></a>Uwagi

MFC używa klasy `CWinFormsView` do hostowania kontrolki Windows Forms .NET Framework w widoku MFC. Kontrolka jest elementem podrzędnym widoku natywnego i zajmuje cały obszar klienta widoku MFC. Wynik jest podobny do widoku `CFormView`, co pozwala na skorzystanie z projektanta Windows Forms i czasu wykonywania w celu utworzenia rozbudowanych widoków opartych na formularzach.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
>  Integracja MFC Windows Forms działa tylko w projektach, które łączą się dynamicznie z MFC (projekty, w których zdefiniowano AFXDLL).

> [!NOTE]
>  CWinFormsView nie obsługuje okna rozdzielacza MFC ( [Klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)). Obecnie jest obsługiwana tylko Windows Forms kontrolka rozdzielacza.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms. h

##  <a name="cwinformsview"></a>CWinFormsView:: CWinFormsView

Konstruuje obiekt `CWinFormsView`.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parametry

*pManagedViewType*<br/>
Wskaźnik do typu danych kontrolki użytkownika Windows Forms.

### <a name="example"></a>Przykład

W poniższym przykładzie Klasa `CUserView` dziedziczy po `CWinFormsView` i przekazuje typ `UserControl1` do konstruktora `CWinFormsView`. `UserControl1` jest kontrolką niestandardową wbudowaną w ControlLibrary1. dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>CWinFormsView:: GetControl

Pobiera wskaźnik do kontrolki Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do obiektu `System.Windows.Forms.Control`.

### <a name="remarks"></a>Uwagi

Aby zapoznać się z przykładem korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_control"></a>CWinFormsView:: operator — formant ^

Rzutuje typ jako wskaźnik do kontrolki Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Uwagi

Ten operator umożliwia przekazywanie `CWinFormsView` widoku do funkcji, które akceptują wskaźnik do kontrolki Windows Forms typu <xref:System.Windows.Forms.Control>.

### <a name="example"></a>Przykład

  Zobacz [CWinFormsView:: GetControl](#getcontrol).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)<br/>
[Klasa CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)
