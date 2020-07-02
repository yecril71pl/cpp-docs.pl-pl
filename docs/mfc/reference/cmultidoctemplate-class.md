---
title: Klasa CMultiDocTemplate
ms.date: 11/04/2016
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
ms.openlocfilehash: af950d188c4e02a38a39ed3c672f0f8c4161bee8
ms.sourcegitcommit: 8fd49f8ac20457710ceb5403ca46fc73cb3f95f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737481"
---
# <a name="cmultidoctemplate-class"></a>Klasa CMultiDocTemplate

Definiuje szablon dokumentu, który implementuje interfejs wielu dokumentów (MDI).

## <a name="syntax"></a>Składnia

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>Elementy członkowskie

Funkcje członkowskie dla tej klasy są wirtualne. Aby uzyskać dokumentację, zobacz [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) i [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) .

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|Konstruuje `CMultiDocTemplate` obiekt.|

## <a name="remarks"></a>Uwagi

Aplikacja MDI używa głównego okna ramowego jako obszaru roboczego, w którym użytkownik może otworzyć zero lub więcej okien ramowych dokumentu, z których każdy Wyświetla dokument. Aby uzyskać bardziej szczegółowy opis usługi MDI, zobacz *wskazówki dotyczące interfejsu systemu Windows dotyczące projektowania oprogramowania*.

Szablon dokumentu definiuje relacje między trzema typami klas:

- Klasa dokumentu, która pochodzi od [CDocument](../../mfc/reference/cdocument-class.md).

- Klasa widoku, która wyświetla dane z klasy dokumentu wymienionej powyżej. Można utworzyć pochodną klasę z [CView](../../mfc/reference/cview-class.md), `CScrollView` , `CFormView` , lub `CEditView` . (Można również użyć `CEditView` bezpośrednio).

- Klasa okna ramki, która zawiera widok. Dla szablonu dokumentu MDI można utworzyć tę klasę z `CMDIChildWnd` , lub, jeśli nie musisz dostosowywać zachowania okien ramowych dokumentu, możesz użyć [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) bezpośrednio bez tworzenia własnej klasy.

Aplikacja MDI może obsługiwać więcej niż jeden typ dokumentu, a dokumenty różnych typów mogą być otwierane w tym samym czasie. Aplikacja ma jeden szablon dokumentu dla każdego typu dokumentu, który obsługuje. Na przykład jeśli aplikacja MDI obsługuje zarówno arkusze kalkulacyjne, jak i dokumenty tekstowe, aplikacja ma dwa `CMultiDocTemplate` obiekty.

Aplikacja używa szablonów dokumentów, gdy użytkownik tworzy nowy dokument. Jeśli aplikacja obsługuje więcej niż jeden typ dokumentu, struktura pobiera nazwy obsługiwanych typów dokumentów z szablonów dokumentów i wyświetla je na liście w oknie dialogowym Nowy plik. Gdy użytkownik wybierze typ dokumentu, aplikacja tworzy obiekt klasy dokumentu, obiekt okna ramki i obiekt widoku i dołącza je do siebie.

Nie musisz wywoływać żadnych funkcji składowych z `CMultiDocTemplate` wyjątkiem konstruktora. Struktura obsługuje `CMultiDocTemplate` obiekty wewnętrznie.

Aby uzyskać więcej informacji na temat `CMultiDocTemplate` , zobacz [Szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="cmultidoctemplatecmultidoctemplate"></a><a name="cmultidoctemplate"></a>CMultiDocTemplate::CMultiDocTemplate

Konstruuje `CMultiDocTemplate` obiekt.

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Określa identyfikator zasobów używanych z typem dokumentu. Może to obejmować menu, ikonę, tabelę akceleratorów i zasoby ciągu.

Zasób ciągu składa się z maksymalnie siedmiu podciągów oddzielonych znakiem "\n" (znak "\n" jest potrzebny jako symbol zastępczy, jeśli nie jest uwzględniony podciąg, ale kończy się znakiem "\n"); te podciągi opisują typ dokumentu. Aby uzyskać informacje na temat podciągów, zobacz [CDocTemplate:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Przykład:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Ciąg rozpoczyna się od znaku "\n", ponieważ pierwszy podciąg nie jest używany w aplikacjach MDI i dlatego nie jest uwzględniony. Można edytować ten ciąg za pomocą edytora ciągów; cały ciąg pojawia się jako pojedynczy wpis w edytorze ciągów, a nie jako siedem oddzielnych wpisów.

Więcej informacji o tych typach zasobów można znaleźć w temacie [edytory zasobów](../../windows/resource-editors.md).

*pDocClass*<br/>
Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa jest `CDocument` klasą pochodną, która jest definiowana do reprezentowania dokumentów.

*pFrameClass*<br/>
Wskazuje `CRuntimeClass` obiekt klasy Frame-Window. Ta klasa może być `CMDIChildWnd` klasą pochodną lub `CMDIChildWnd` samą, jeśli chcesz, aby domyślne zachowanie dla okien ramowych dokumentu.

*pViewClass*<br/>
Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa jest `CView` klasą pochodną, która jest definiowana do wyświetlania dokumentów.

### <a name="remarks"></a>Uwagi

Dynamicznie Przydziel jeden `CMultiDocTemplate` obiekt dla każdego typu dokumentu obsługiwanego przez aplikację i przekaż go do `CWinApp::AddDocTemplate` `InitInstance` funkcji członkowskiej klasy aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

Oto drugi przykład.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)<br/>
[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)
