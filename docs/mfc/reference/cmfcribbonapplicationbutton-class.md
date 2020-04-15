---
title: Klasa CMFCRibbonApplicationButton
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
ms.openlocfilehash: 0debd40825990b647cd5b1df9a144e3abd450de3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361604"
---
# <a name="cmfcribbonapplicationbutton-class"></a>Klasa CMFCRibbonApplicationButton

Implementuje specjalny przycisk znajdujący się w lewym górnym rogu okna aplikacji. Po kliknięciu przycisk otwiera menu, które zwykle zawiera typowe polecenia **Plik,** takie jak **Otwórz,** **Zapisz**i **Zakończ**.

## <a name="syntax"></a>Składnia

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|Konstruuje i inicjuje `CMFCRibbonApplicationButton` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|Używany przez platformę do tworzenia dynamicznego wystąpienia tego typu klasy.|
|`CMFCRibbonApplicationButton::GetThisClass`|Używany przez platformę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tego typu klasy.|
|[CMFCRibbonZałączenieButton::SetImage](#setimage)|Przypisuje obraz do przycisku aplikacji wstążki.|

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCRibbonApplicationButton` używać różnych metod w klasie. W przykładzie pokazano, jak przypisać obraz do przycisku aplikacji i jak ustawić jego etykietkę narzędzia. Ten fragment kodu jest częścią [próbki Klienta rysowania](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonPołączenie aplikacji](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxRibbonBar.h

## <a name="cmfcribbonapplicationbuttoncmfcribbonapplicationbutton"></a><a name="cmfcribbonapplicationbutton"></a>CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

Konstruuje i inicjuje [OBIEKT CMFCRibbonApplicationButton.](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>Parametry

*interfejs użytkownika uiBmpResID*<br/>
Identyfikator zasobu obrazu do wyświetlenia na przycisku aplikacji.

*hBmp (wł.)*<br/>
Uchwyt do mapy bitowej do wyświetlenia na przycisku aplikacji.

### <a name="remarks"></a>Uwagi

Przycisk aplikacji wstążki to specjalny przycisk, który znajduje się w lewym górnym rogu okna aplikacji. Gdy użytkownik kliknie ten przycisk, aplikacja otwiera menu, które zwykle zawiera typowe polecenia **Plik,** takie jak **Otwórz,** **Zapisz**i **Zakończ**.

## <a name="cmfcribbonapplicationbuttonsetimage"></a><a name="setimage"></a>CMFCRibbonZałączenieButton::SetImage

Przypisuje obraz do przycisku aplikacji.

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>Parametry

*interfejs użytkownika uiBmpResID*<br/>
[w] Identyfikator zasobu obrazu do wyświetlenia na przycisku aplikacji.

*hBmp (wł.)*<br/>
[w] Uchwyt do mapy bitowej do wyświetlenia na przycisku aplikacji.

### <a name="remarks"></a>Uwagi

Ta metoda służy do przypisywania nowego obrazu do przycisku aplikacji wstążki po utworzeniu przycisku. Przycisk aplikacji znajduje się w lewym górnym rogu okna aplikacji.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
