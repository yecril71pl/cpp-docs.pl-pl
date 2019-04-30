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
ms.openlocfilehash: af84c5239a9cb3cbddb1ab4f0230e5b1a3373573
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400724"
---
# <a name="cdialogbar-class"></a>Klasa CDialogBar

Oferuje funkcje Windows niemodalnego okna dialogowego na pasku sterowania.

## <a name="syntax"></a>Składnia

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialogBar::CDialogBar](#cdialogbar)|Konstruuje `CDialogBar` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDialogBar::Create](#create)|Tworzy Pasek dialogowy Windows i dołącza je do `CDialogBar` obiektu.|

## <a name="remarks"></a>Uwagi

Pasek dialogowy przypomina okno dialogowe, ponieważ zawiera standardowych kontrolek Windows, które użytkownik może karcie między. Inny podobieństwa jest utworzenie szablonu okna dialogowego do reprezentowania paska dialogowego.

Tworzenie i używanie paska dialogowego jest podobne do tworzenia i używania `CFormView` obiektu. Najpierw za pomocą [Edytor okien dialogowych](../../windows/dialog-editor.md) do definiowania szablonu okna dialogowego ze stylem WS_CHILD i nie inne stylu. Szablon nie może mieć styl WS_VISIBLE. W kodzie aplikacji należy wywołać konstruktora do konstruowania `CDialogBar` obiektu, a następnie wywołaj `Create` utworzyć okno Pasek dialogowy i dołącz ją do `CDialogBar` obiektu.

Aby uzyskać więcej informacji na temat `CDialogBar`, zapoznaj się z artykułem [paski dialogowe](../../mfc/dialog-bars.md) i [techniczne 31 Uwaga](../../mfc/tn031-control-bars.md), pasków sterowania.

> [!NOTE]
>  W bieżącej wersji `CDialogBar` obiektu nie może obsługiwać kontrolek formularzy Windows Forms. Aby uzyskać więcej informacji na temat formantów formularzy Windows w języku Visual C++, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxext.h

##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar

Konstruuje `CDialogBar` obiektu.

```
CDialogBar();
```

##  <a name="create"></a>  CDialogBar::Create

Ładuje szablonu zasobów okno dialogowe, które są określone przez `lpszTemplateName` lub `nIDTemplate`, tworzy okno Pasek dialogowy, ustawia jego styl i kojarzy ją z `CDialogBar` obiektu.

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
Wskaźnik do elementu nadrzędnego `CWnd` obiektu.

*lpszTemplateName*<br/>
Wskaźnik na nazwę `CDialogBar` obiektu szablonu zasobu okna dialogowego.

*nStyle*<br/>
Styl paska narzędzi. Style dodatkowych narzędzi, obsługiwane są następujące:

- Pasek sterowania CBRS_TOP to u góry okna ramki.

- Pasek sterowania CBRS_BOTTOM jest w dolnej części okna ramki.

- Pasek sterowania CBRS_NOALIGN nie zostaje przeniesiony, gdy zmieniany jest rozmiar obiektu nadrzędnego.

- Pasek sterowania CBRS_TOOLTIPS Wyświetla etykietek narzędzi.

- Pasek sterowania CBRS_SIZE_DYNAMIC jest dynamiczny.

- Pasek sterowania CBRS_SIZE_FIXED jest stała.

- Pasek sterowania CBRS_FLOATING jest liczb zmiennoprzecinkowych.

- Pasek stanu CBRS_FLYBY Wyświetla informacje o przycisku.

- Pasek sterowania CBRS_HIDE_INPLACE są niewidoczne dla użytkownika.

*nID*<br/>
Identyfikator formantu paska dialogowego.

*nIDTemplate*<br/>
Identyfikator zasobu `CDialogBar` obiektu szablonu okna dialogowego.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli określisz style wyrównania CBRS_TOP lub CBRS_BOTTOM, Pasek dialogowy się szerokość ramki okna i jego wysokość jest zasób określony przez *nIDTemplate*. Jeśli określisz style wyrównania CBRS_LEFT lub CBRS_RIGHT, wysokość paska dialogowego jest to, że ramki okna i jego szerokość jest zasób określony przez *nIDTemplate*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Próbki MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFormView](../../mfc/reference/cformview-class.md)<br/>
[Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
