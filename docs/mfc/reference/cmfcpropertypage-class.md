---
title: Klasa CMFCPropertyPage
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: e493f016b6384a768935186c31e3fc71ade6382f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361759"
---
# <a name="cmfcpropertypage-class"></a>Klasa CMFCPropertyPage

Klasa `CMFCPropertyPage` obsługuje wyświetlanie menu podręcznych na stronie właściwości.

## <a name="syntax"></a>Składnia

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Konstruuje `CMFCPropertyPage` obiekt.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CMFCPropertyPage::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|`CMFCPropertyPage::OnSetActive`|Ta funkcja elementu członkowskiego jest wywoływana przez platformę, gdy strona jest wybierana przez użytkownika i staje się aktywną stroną. (Zastępuje [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Tłumaczy komunikaty okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. Aby uzyskać więcej informacji i składni metody, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CPropertyPage::PreTranslateMessage`).|

## <a name="remarks"></a>Uwagi

Klasa `CMFCPropertyPage` reprezentuje poszczególne strony arkusza właściwości, inaczej znane jako okno dialogowe karty.

Użyj `CMFCPropertyPage` klasy wraz z [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) klasy. Aby użyć menu na stronie właściwości, zastąp wszystkie wystąpienia `CPropertyPage` klasy klasą. `CMFCPropertyPage`

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[Cpropertypage](../../mfc/reference/cpropertypage-class.md)

[STRONA CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertypage.h

## <a name="cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage

Konstruuje `CMFCPropertyPage` obiekt.

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>Parametry

*nIDTemplate*<br/>
Identyfikator zasobu szablonu dla tej strony.

*nIDCaption (nIDCaption)*<br/>
Identyfikator zasobu etykiety do umieszczenia na karcie dla tej strony. Jeśli 0, nazwa jest uzyskiwana z szablonu okna dialogowego dla tej strony. Wartość domyślna to 0.

*lpszTemplateName*<br/>
Wskazuje nazwę szablonu dla tej strony. Nie może być null.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat parametrów konstruktora, zobacz [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)
