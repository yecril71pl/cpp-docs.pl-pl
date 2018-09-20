---
title: Klasa CMultiDocTemplate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMultiDocTemplate
- AFXWIN/CMultiDocTemplate
- AFXWIN/CMultiDocTemplate::CMultiDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- CMultiDocTemplate [MFC], CMultiDocTemplate
ms.assetid: 5b8aa328-e461-41d0-b388-00594535e119
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0a3c7c301feecaf00fbf2dffcd6288b11ecfc7b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380818"
---
# <a name="cmultidoctemplate-class"></a>Klasa CMultiDocTemplate

Określa szablon dokumentu, który implementuje interfejs dokumentu wielokrotnego (MDI).

## <a name="syntax"></a>Składnia

```
class CMultiDocTemplate : public CDocTemplate
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMultiDocTemplate::CMultiDocTemplate](#cmultidoctemplate)|Konstruuje `CMultiDocTemplate` obiektu.|

## <a name="remarks"></a>Uwagi

Aplikacja MDI używa ramką głównego okna jako obszar roboczy, w którym użytkownik może otwierać zero lub więcej okien ramowych dokumentu, z których każdy zawiera dokument. Aby uzyskać bardziej szczegółowy opis MDI, zobacz *Windows interfejsu wytyczne dotyczące projektowania oprogramowania*.

Szablon dokumentu zdefiniuje relacje między trzy typy klas:

- Klasy dokumentów, które pochodzą z [CDocument](../../mfc/reference/cdocument-class.md).

- Klasy widoku, która wyświetla dane z klasy dokumentu wymienionych powyżej. Utworzeniu klasy pochodnej tej klasy z [CView](../../mfc/reference/cview-class.md), `CScrollView`, `CFormView`, lub `CEditView`. (Możesz również użyć `CEditView` bezpośrednio.)

- Klasy okna ramki, który zawiera widok. W przypadku szablonu dokumentu MDI utworzeniu klasy pochodnej tej klasy z `CMDIChildWnd`, lub jeśli nie potrzebujesz dostosować zachowanie okien ramowych dokumentu, można użyć [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) bezpośrednio, bez wyprowadzanie własne klasy.

Aplikacja MDI może obsługiwać więcej niż jednego typu dokumentu i dokumenty o różnych typach może być otwarty, w tym samym czasie. Twoja aplikacja ma jeden szablon dokumentu dla każdego typu dokumentu, który ją obsługuje. Na przykład, jeśli aplikacja MDI obsługuje arkuszy kalkulacyjnych i dokumenty tekstowe, aplikacja ma dwa `CMultiDocTemplate` obiektów.

Aplikacja używa szablony dokumentu, gdy użytkownik tworzy nowy dokument. Jeśli aplikacja obsługuje więcej niż jeden typ dokumentu, struktura pobiera nazwy typów obsługiwanych dokumentu z szablonów dokumentów i wyświetla je na liście w oknie dialogowym Nowy plik. Po użytkownik wybrał typu dokumentu, aplikacja tworzy obiekt klasy dokumentu, obiekt okna ramki i obiekt widoku i dołącza je do siebie nawzajem.

Nie musisz wywołać dowolny członek funkcji `CMultiDocTemplate` z wyjątkiem konstruktora. Uchwyty framework `CMultiDocTemplate` obiekty wewnętrznie.

Aby uzyskać więcej informacji na temat `CMultiDocTemplate`, zobacz [szablonów dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CMultiDocTemplate`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cmultidoctemplate"></a>  CMultiDocTemplate::CMultiDocTemplate

Konstruuje `CMultiDocTemplate` obiektu.

```
CMultiDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Określa identyfikator zasoby używane za pomocą typu dokumentu. Może to obejmować menu, ikony, tabeli akceleratora i zasoby w postaci ciągów.

Zasób ciągu składa się z maksymalnie siedem podciągów oddzielone znakiem "\n" (znak '\n' jest wymagane jako symbolu zastępczego, jeśli podciąg nie jest uwzględniony jednak nie są konieczne znaki końcowe '\n'); te podciągów opisują typ dokumentu. Aby uzyskać informacji na temat podciągów, zobacz [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Na przykład:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Należy zauważyć, że ciąg rozpoczyna się od znaku '\n'; jest to spowodowane pierwszego podciągu nie jest używana dla aplikacji MDI, a zatem nie jest dołączony. Możesz edytować ten ciąg przy użyciu edytora ciągów; cały ciąg pojawi się jako pojedynczy wpis w edytorze ciągu nie jako siedmiu osobnych wpisów.

Aby uzyskać więcej informacji na temat tych typów zasobów, zobacz [edytory zasobów](../../windows/resource-editors.md).

*pDocClass*<br/>
Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa jest `CDocument`— zdefiniuj do reprezentowania dokumentów klasy pochodnej.

*pFrameClass*<br/>
Wskazuje `CRuntimeClass` obiekt klasy okien ramowych. Ta klasa może być `CMDIChildWnd`-klasy pochodnej lub może być `CMDIChildWnd` sam chcącym domyślne zachowanie dla Twojego okien ramowych dokumentu.

*pViewClass*<br/>
Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa jest `CView`— należy zdefiniować, aby wyświetlić swoje dokumenty klasy pochodnej.

### <a name="remarks"></a>Uwagi

Dynamiczne przydzielanie jeden `CMultiDocTemplate` obiekt dla każdego typu dokumentu, który obsługuje i przekazać każdy z nich w aplikacji `CWinApp::AddDocTemplate` z `InitInstance` funkcji składowej klasy aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]

Oto przykład drugi.

[!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)<br/>
[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)
