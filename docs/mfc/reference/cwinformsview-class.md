---
title: Klasa CWinFormsView | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4d90f2a7f964d264966d5254d051ebddaf2baa
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448145"
---
# <a name="cwinformsview-class"></a>Klasa CWinFormsView

Oferuje ogólną funkcję obsługi formantu Windows Forms jako widoku MFC.

## <a name="syntax"></a>Składnia

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|Konstruuje `CWinFormsView` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|Pobiera wskaźnik do kontrolki Windows Forms.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa||
|----------|-|
|[Kontrolka CWinFormsView::operator ^](#operator_control)|Rzutuje typu jako wskaźnik do formantu Windows Forms.|

## <a name="remarks"></a>Uwagi

MFC wykorzystuje `CWinFormsView` klasy do hostowania formantu .NET Framework Windows Forms w widoku MFC. Formant jest elementem podrzędnym natywnych widoku i zajmuje całego obszaru klienta widoku MFC. Wynik jest podobny do `CFormView` widoku, co pozwala na korzystanie z zalet projektanta Windows Forms i czasie wykonywania, aby utworzyć gotowe, rozbudowane widoki oparte na formularzach.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
>  Integracja biblioteki MFC, formularzy Windows działa tylko w projektach, które dołączana dynamicznie z MFC (projekty, w których zdefiniowano AFXDLL).

> [!NOTE]
>  CWinFormsView nie obsługuje okno rozdzielacza MFC ( [klasa CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)). Obecnie tylko Windows Forms rozdzielacz jest obsługiwany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h

##  <a name="cwinformsview"></a>  CWinFormsView::CWinFormsView

Konstruuje `CWinFormsView` obiektu.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Parametry

*pManagedViewType*<br/>
Wskaźnik do typu danych kontrolki użytkownika Windows Forms.

### <a name="example"></a>Przykład

W poniższym przykładzie `CUserView` klasa dziedziczy `CWinFormsView` i przekazuje typ `UserControl1` do `CWinFormsView` konstruktora. `UserControl1` jest kontrolki niestandardowej w ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>  CWinFormsView::GetControl

Pobiera wskaźnik do kontrolki Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `System.Windows.Forms.Control` obiektu.

### <a name="remarks"></a>Uwagi

Na przykład dotyczące używania formularzy Windows zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_control"></a>  Kontrolka CWinFormsView::operator ^

Rzutuje typu jako wskaźnik do formantu Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Uwagi

Ten operator umożliwia przekazywanie `CWinFormsView` widok do funkcji, które akceptują wskaźnik do formantu Windows Forms typu <xref:System.Windows.Forms.Control>.

### <a name="example"></a>Przykład

  Zobacz [CWinFormsView::GetControl](#getcontrol).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md)<br/>
[Klasa CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)
