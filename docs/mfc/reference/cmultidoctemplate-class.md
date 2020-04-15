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
ms.openlocfilehash: 3b3f239b05b1cf7661929333e2d616acce6bedb0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319744"
---
# <a name="cmultidoctemplate-class"></a>Klasa CMultiDocTemplate

Definiuje szablon dokumentu, który implementuje interfejs wielu dokumentów (MDI).

## <a name="syntax"></a>Składnia

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|Konstruuje `CMultiDocTemplate` obiekt.|

## <a name="remarks"></a>Uwagi

Aplikacja MDI używa okna ramki głównej jako obszaru roboczego, w którym użytkownik może otworzyć zero lub więcej okien ramek dokumentu, z których każdy wyświetla dokument. Aby uzyskać bardziej szczegółowy opis mdi, zobacz *Wskazówki dotyczące projektowania oprogramowania dotyczące interfejsu systemu Windows*.

Szablon dokumentu definiuje relacje między trzema typami klas:

- Klasa dokumentu, która pochodzi z [CDocument](../../mfc/reference/cdocument-class.md).

- Klasa widoku, która wyświetla dane z klasy dokumentu wymienionej powyżej. Tę klasę można wyprowadzić z `CScrollView` `CFormView` [cView](../../mfc/reference/cview-class.md), , lub `CEditView`. (Można również `CEditView` użyć bezpośrednio.)

- Klasa okna ramki, która zawiera widok. W przypadku szablonu dokumentu MDI można `CMDIChildWnd`wyprowadzić tę klasę z programu , lub, jeśli nie trzeba dostosowywać zachowania okien ramki dokumentu, można użyć [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) bezpośrednio bez wyprowadzania własnej klasy.

Aplikacja MDI może obsługiwać więcej niż jeden typ dokumentu, a dokumenty różnych typów mogą być otwierane w tym samym czasie. Aplikacja ma jeden szablon dokumentu dla każdego typu dokumentu, który obsługuje. Na przykład jeśli aplikacja MDI obsługuje zarówno arkusze kalkulacyjne, jak i dokumenty tekstowe, aplikacja ma dwa `CMultiDocTemplate` obiekty.

Aplikacja używa szablonów dokumentów, gdy użytkownik tworzy nowy dokument. Jeśli aplikacja obsługuje więcej niż jeden typ dokumentu, a następnie ramy pobiera nazwy obsługiwanych typów dokumentów z szablonów dokumentów i wyświetla je na liście w oknie dialogowym Plik nowy. Po wybraniu przez użytkownika typu dokumentu aplikacja tworzy obiekt klasy dokumentu, obiekt okna ramki i obiekt widoku i dołącza je do siebie.

Nie trzeba wywoływać żadnych funkcji `CMultiDocTemplate` członkowskich z wyjątkiem konstruktora. Struktura obsługuje `CMultiDocTemplate` obiekty wewnętrznie.

Aby uzyskać `CMultiDocTemplate`więcej informacji na temat , zobacz [Szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdoctemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

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

*nIDSerwród*<br/>
Określa identyfikator zasobów używanych z typem dokumentu. Może to obejmować menu, ikonę, tabelę akceleratora i zasoby ciągów.

Zasób ciągu składa się z maksymalnie siedmiu podciągów oddzielonych znakiem '\n' (znak '\n' jest potrzebny jako uchwyt miejsca, jeśli podciąg nie jest uwzględniony; jednak końcowe znaki "\n"; te podciągi opisują typ dokumentu. Aby uzyskać informacje na temat podciągów, zobacz [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Przykład:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Należy zauważyć, że ciąg zaczyna się od znaku '\n'; jest to spowodowane pierwszym podciągiem nie jest używany dla aplikacji MDI i tak nie jest uwzględniony. Ten ciąg można edytować za pomocą edytora ciągów; cały ciąg pojawia się jako pojedynczy wpis w Edytorze ciągów, a nie jako siedem oddzielnych wpisów.

Aby uzyskać więcej informacji na temat tych typów zasobów, zobacz [Edytory zasobów](../../windows/resource-editors.md).

*pDocClass (klasa pDocClass)*<br/>
Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa `CDocument`jest klasą pochodną, którą definiujesz w celu reprezentowania dokumentów.

*pFrameClass (klasa pFrameclass)*<br/>
Wskazuje `CRuntimeClass` obiekt klasy okna ramki. Ta klasa może `CMDIChildWnd`być klasą pochodną `CMDIChildWnd` lub może być sama, jeśli chcesz domyślne zachowanie dla okien ramki dokumentu.

*pViewClass (Klasa widoków)*<br/>
Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa `CView`jest klasą pochodną zdefiniowaną w celu wyświetlenia dokumentów.

### <a name="remarks"></a>Uwagi

Dynamicznie przydzielić jeden `CMultiDocTemplate` obiekt dla każdego typu dokumentu, `CWinApp::AddDocTemplate` który `InitInstance` aplikacja obsługuje i przekazać każdy z nich z funkcji elementu członkowskiego klasy aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

Oto drugi przykład.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)<br/>
[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)
