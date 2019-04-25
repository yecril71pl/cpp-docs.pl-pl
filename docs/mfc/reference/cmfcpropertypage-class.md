---
title: CMFCPropertyPage Class
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: 62e33da998f1e5332436d887c38d3fd65526561b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310492"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage Class

`CMFCPropertyPage` Klasa obsługuje wyświetlanie wyskakujących menu na stronie właściwości.

## <a name="syntax"></a>Składnia

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Konstruuje `CMFCPropertyPage` obiektu.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Używane przez platformę do tworzenia dynamicznych wystąpienia tego typu klasy.|
|`CMFCPropertyPage::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|
|`CMFCPropertyPage::OnSetActive`|Ta funkcja członkowska jest wywoływana przez platformę, gdy strona jest wybierany przez użytkownika i staje się stroną aktywną. (Przesłania [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Wykonuje translację komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkcje Windows. Aby uzyskać więcej informacji i składnia metody, zobacz [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Przesłania `CPropertyPage::PreTranslateMessage`).|

## <a name="remarks"></a>Uwagi

`CMFCPropertyPage` Klasa przedstawia pojedyncze strony arkusza właściwości, znane również jako zakładki okna dialogowego.

Użyj `CMFCPropertyPage` klasy wraz z [CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md) klasy. Aby użyć menu na stronie właściwości, należy zastąpić wszystkie wystąpienia `CPropertyPage` klasy `CMFCPropertyPage` klasy.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxpropertypage.h

##  <a name="cmfcpropertypage"></a>  CMFCPropertyPage::CMFCPropertyPage

Konstruuje `CMFCPropertyPage` obiektu.

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
Identyfikator zasobu szablon dla tej strony.

*nIDCaption*<br/>
Identyfikator zasobu etykiety, aby umieścić na karcie tej strony. Jeśli jest to 0, nazwa jest uzyskiwana z szablonu okna dialogowego na tej stronie. Wartość domyślna to 0.

*lpszTemplateName*<br/>
Wskazuje nazwę szablonu dla tej strony. Nie może mieć wartości NULL.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat parametrów konstruktora, zobacz [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)
