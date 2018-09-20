---
title: Klasa CSingleDocTemplate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
dev_langs:
- C++
helpviewer_keywords:
- CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 66b5ff9f2cae462ebd7e5bb90cd51f02600e6a85
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395872"
---
# <a name="csingledoctemplate-class"></a>Klasa CSingleDocTemplate

Określa szablon dokumentu, który implementuje interfejs dokumentu pojedynczego (SDI).

## <a name="syntax"></a>Składnia

```
class CSingleDocTemplate : public CDocTemplate
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSingleDocTemplate::CSingleDocTemplate](#csingledoctemplate)|Konstruuje `CSingleDocTemplate` obiektu.|

## <a name="remarks"></a>Uwagi

Korzysta z aplikacji interfejsu SDI ramki głównego okna do wyświetlenia dokumentu. tylko jeden dokument może być otwarty naraz.

Szablon dokumentu definiuje relację między trzy typy klas:

- Klasy dokumentów, które pochodzą z `CDocument`.

- Klasy widoku, która wyświetla dane z klasy dokumentu wymienionych powyżej. Utworzeniu klasy pochodnej tej klasy z `CView`, `CScrollView`, `CFormView`, lub `CEditView`. (Możesz również użyć `CEditView` bezpośrednio.)

- Klasy okna ramki, który zawiera widok. W przypadku szablonu dokumentu SDI utworzeniu klasy pochodnej tej klasy z `CFrameWnd`; Jeśli nie trzeba dostosować zachowanie głównej ramki okna, możesz użyć `CFrameWnd` bezpośrednio, bez wyprowadzanie własne klasy.

Aplikacji interfejsu SDI zazwyczaj obsługuje jeden typ dokumentu, dlatego ma tylko jeden `CSingleDocTemplate` obiektu. Tylko jeden dokument może być otwarty naraz.

Nie musisz wywołać dowolny członek funkcji `CSingleDocTemplate` z wyjątkiem konstruktora. Uchwyty framework `CSingleDocTemplate` obiekty wewnętrznie.

Aby uzyskać więcej informacji na temat korzystania z `CSingleDocTemplate`, zobacz [szablonów dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)

`CSingleDocTemplate`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="csingledoctemplate"></a>  CSingleDocTemplate::CSingleDocTemplate

Konstruuje `CSingleDocTemplate` obiektu.

```
CSingleDocTemplate(
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Parametry

*nIDResource*<br/>
Określa identyfikator zasoby używane za pomocą typu dokumentu. Może to obejmować menu, ikony, tabeli akceleratora i zasoby w postaci ciągów.

Zasób ciągu składa się z maksymalnie siedem podciągów oddzielone znakiem "\n" (znak '\n' jest wymagane jako symbol zastępczy, jeśli podciąg nie jest uwzględniony jednak nie są konieczne znaki końcowe '\n'); te podciągów opisują typ dokumentu. Aby uzyskać informacje na temat podciągów, zobacz [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Na przykład:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"
END
```

Możesz edytować ten ciąg przy użyciu edytora ciągów; cały ciąg pojawi się jako pojedynczy wpis w edytorze ciągu nie jako siedmiu osobnych wpisów.

Aby uzyskać więcej informacji na temat tych typów zasobów, zobacz [edytor ciągów](../../windows/string-editor.md).

*pDocClass*<br/>
Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa jest `CDocument`— zdefiniuj do reprezentowania dokumentów klasy pochodnej.

*pFrameClass*<br/>
Wskazuje `CRuntimeClass` obiektu klasę okna ramowego. Ta klasa może być `CFrameWnd`-klasy pochodnej lub może być `CFrameWnd` sam chcącym domyślne zachowanie dla okna głównej ramki.

*pViewClass*<br/>
Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa jest `CView`— należy zdefiniować, aby wyświetlić swoje dokumenty klasy pochodnej.

### <a name="remarks"></a>Uwagi

Dynamiczne przydzielanie `CSingleDocTemplate` obiektu i przekazać ją do `CWinApp::AddDocTemplate` z `InitInstance` funkcji składowej klasy aplikacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]

[!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Próbki MFC DOCKTOOL](../../visual-cpp-samples.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Klasa CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Klasa CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Klasa CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[Klasa CView](../../mfc/reference/cview-class.md)<br/>
[Klasa CWinApp](../../mfc/reference/cwinapp-class.md)
