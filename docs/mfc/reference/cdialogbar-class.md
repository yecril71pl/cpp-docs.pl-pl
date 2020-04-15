---
title: Klasa CDialogBar
ms.date: 11/04/2016
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
ms.openlocfilehash: cf9a2658807959108b3bb0af672d4c1835b58bc5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375673"
---
# <a name="cdialogbar-class"></a>Klasa CDialogBar

Udostępnia funkcje trybuowego okna dialogowego systemu Windows na pasku sterowania.

## <a name="syntax"></a>Składnia

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialogBar::CDialogBar](#cdialogbar)|Konstruuje `CDialogBar` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialogBar::Utwórz](#create)|Tworzy pasek dialogowy systemu Windows `CDialogBar` i dołącza go do obiektu.|

## <a name="remarks"></a>Uwagi

Pasek dialogowy przypomina okno dialogowe, ponieważ zawiera standardowe formanty systemu Windows, między którymi użytkownik może się między nim wymieniać. Innym podobieństwem jest utworzenie szablonu okna dialogowego reprezentującego pasek dialogowy.

Tworzenie i używanie paska dialogowego jest podobne `CFormView` do tworzenia i używania obiektu. Najpierw użyj [edytora okien dialogowych,](../../windows/dialog-editor.md) aby zdefiniować szablon okna dialogowego z WS_CHILD stylu i bez innego stylu. Szablon nie może mieć stylu WS_VISIBLE. W kodzie aplikacji wywołać konstruktora do konstruowania `CDialogBar` obiektu, a następnie wywołać, `Create` aby utworzyć okno paska dialogowego i dołączyć go do `CDialogBar` obiektu.

Aby uzyskać `CDialogBar`więcej informacji na temat , zobacz artykuł [Paski dialogowe](../../mfc/dialog-bars.md) i [Uwaga techniczna 31](../../mfc/tn031-control-bars.md), Paski sterowania.

> [!NOTE]
> W bieżącym wydaniu `CDialogBar` obiekt nie może obsługiwać formantów windows forms. Aby uzyskać więcej informacji na temat formantów formularzy systemu Windows w języku Visual C++, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ccontrolbar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

## <a name="cdialogbarcdialogbar"></a><a name="cdialogbar"></a>CDialogBar::CDialogBar

Konstruuje `CDialogBar` obiekt.

```
CDialogBar();
```

## <a name="cdialogbarcreate"></a><a name="create"></a>CDialogBar::Utwórz

Ładuje szablon zasobu okna `lpszTemplateName` dialogowego określony przez lub `nIDTemplate`, tworzy okno paska dialogowego, ustawia jego styl i kojarzy go z obiektem. `CDialogBar`

```
virtual BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

virtual BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Wskaźnik do obiektu `CWnd` nadrzędnego.

*lpszTemplateName*<br/>
Wskaźnik do nazwy szablonu `CDialogBar` zasobu okna dialogowego obiektu.

*styl nStyle*<br/>
Styl paska narzędzi. Dodatkowe obsługiwane style paska narzędzi to:

- CBRS_TOP pasek sterowania znajduje się w górnej części okna ramki.

- CBRS_BOTTOM pasek sterowania znajduje się w dolnej części okna ramki.

- CBRS_NOALIGN pasek sterowania nie jest zmieniany po zmianie jego zmiany.

- CBRS_TOOLTIPS pasek sterowania wyświetla wskazówki dotyczące narzędzi.

- CBRS_SIZE_DYNAMIC pasek sterowania jest dynamiczny.

- CBRS_SIZE_FIXED pasek sterowania jest stały.

- CBRS_FLOATING pasek sterowania jest zmienny.

- CBRS_FLYBY pasek stanu wyświetla informacje o przycisku.

- CBRS_HIDE_INPLACE pasek sterowania nie jest wyświetlany użytkownikowi.

*Nid*<br/>
Identyfikator formantu paska dialogowego.

*nIDTemplate*<br/>
Identyfikator zasobu szablonu `CDialogBar` okna dialogowego obiektu.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli określisz styl wyrównania CBRS_TOP lub CBRS_BOTTOM, szerokość paska dialogowego jest szerokością okna ramki, a jego wysokość jest zasób określony przez *nIDTemplate*. Jeśli określisz styl wyrównania CBRS_LEFT lub CBRS_RIGHT, wysokość paska dialogowego jest wysokość okna ramki i jego szerokość jest to, że zasób określony przez *nIDTemplate*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbka MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
