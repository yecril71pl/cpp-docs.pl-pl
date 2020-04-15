---
title: Klasa CSingleDocTemplate
ms.date: 11/04/2016
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
ms.openlocfilehash: 5a014b35a6cd2d12367e190e4d6dd689e28eae66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318344"
---
# <a name="csingledoctemplate-class"></a>Klasa CSingleDocTemplate

Definiuje szablon dokumentu, który implementuje interfejs pojedynczego dokumentu (SDI).

## <a name="syntax"></a>Składnia

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Płyta CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|Konstruuje `CSingleDocTemplate` obiekt.|

## <a name="remarks"></a>Uwagi

Aplikacja SDI używa okna ramki głównej do wyświetlania dokumentu; tylko jeden dokument może być otwarty naraz.

Szablon dokumentu definiuje relację między trzema typami klas:

- Klasa dokumentu, z `CDocument`której pochodzisz .

- Klasa widoku, która wyświetla dane z klasy dokumentu wymienionej powyżej. Tę klasę można wyprowadzić `CScrollView` `CFormView`z `CView` `CEditView`, , , lub . (Można również `CEditView` użyć bezpośrednio.)

- Klasa okna ramki, która zawiera widok. W przypadku szablonu dokumentu SDI można `CFrameWnd`wyprowadzić tę klasę z ; Jeśli nie trzeba dostosowywać zachowanie okna ramki głównej, `CFrameWnd` można użyć bezpośrednio bez wyprowadzania własnej klasy.

Aplikacja SDI zazwyczaj obsługuje jeden typ dokumentu, więc `CSingleDocTemplate` ma tylko jeden obiekt. Jednocześnie można otworzyć tylko jeden dokument.

Nie trzeba wywoływać żadnych funkcji `CSingleDocTemplate` członkowskich z wyjątkiem konstruktora. Struktura obsługuje `CSingleDocTemplate` obiekty wewnętrznie.

Aby uzyskać więcej `CSingleDocTemplate`informacji na temat używania , zobacz [Szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdoctemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="csingledoctemplatecsingledoctemplate"></a><a name="csingledoctemplate"></a>Płyta CSingleDocTemplate::CSingleDocTemplate

Konstruuje `CSingleDocTemplate` obiekt.

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDSerwród*<br/>
Określa identyfikator zasobów używanych z typem dokumentu. Może to obejmować menu, ikonę, tabelę akceleratora i zasoby ciągów.

Zasób ciągu składa się z maksymalnie siedmiu podciągów oddzielonych znakiem '\n' (znak '\n' jest potrzebny jako symbol zastępczy, jeśli podciąg nie jest uwzględniony; jednak końcowe znaki "\n"nie są konieczne); te podciągi opisują typ dokumentu. Aby uzyskać informacje na temat podciągów, zobacz [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Przykład:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

Ten ciąg można edytować za pomocą edytora ciągów; cały ciąg pojawia się jako pojedynczy wpis w Edytorze ciągów, a nie jako siedem oddzielnych wpisów.

Aby uzyskać więcej informacji na temat tych typów zasobów, zobacz [Edytor ciągów](../../windows/string-editor.md).

*pDocClass (klasa pDocClass)*<br/>
Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa `CDocument`jest klasą pochodną, którą definiujesz w celu reprezentowania dokumentów.

*pFrameClass (klasa pFrameclass)*<br/>
Wskazuje `CRuntimeClass` obiekt klasy okna ramki. Ta klasa może `CFrameWnd`być klasą pochodną `CFrameWnd` lub może być sama, jeśli chcesz domyślne zachowanie dla okna ramki głównej.

*pViewClass (Klasa widoków)*<br/>
Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa `CView`jest klasą pochodną zdefiniowaną w celu wyświetlenia dokumentów.

### <a name="remarks"></a>Uwagi

Dynamicznie przydzielić `CSingleDocTemplate` obiekt i `CWinApp::AddDocTemplate` przekazać `InitInstance` go z funkcji elementu członkowskiego klasy aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Przykładowy DOCKTOOL MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Klasa CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)
