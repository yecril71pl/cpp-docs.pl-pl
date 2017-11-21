---
title: Klasa CSingleDocTemplate | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSingleDocTemplate
- AFXWIN/CSingleDocTemplate
- AFXWIN/CSingleDocTemplate::CSingleDocTemplate
dev_langs: C++
helpviewer_keywords: CSingleDocTemplate [MFC], CSingleDocTemplate
ms.assetid: 4f3a8212-81ee-48a0-ad22-e0ed7c36a391
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e23db022f62dab171359f2d0a9cdb158c36557c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csingledoctemplate-class"></a>Klasa CSingleDocTemplate
Definiuje szablonu dokumentu, który implementuje interfejs pojedynczego dokumentu (SDI).  
  
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
 Aplikacja SDI używa główną ramkę okna do wyświetlenia dokumentu. tylko jeden dokument może być otwarty naraz.  
  
 Szablon dokumentu definiuje relację między trzy typy klas:  
  
-   Klasy dokumentów, który pochodzi od **CDocument**.  
  
-   Klasy widoku, która zawiera dane z klasy dokumentu wymienionych powyżej. Można pochodzi ta klasa z `CView`, `CScrollView`, `CFormView`, lub `CEditView`. (Można również użyć `CEditView` bezpośrednio.)  
  
-   Klasy okna ramki, który zawiera widok. Dla szablonu dokumentów SDI może pochodzi ta klasa z `CFrameWnd`; Jeśli nie musisz dostosować zachowanie głównego ramki okna, możesz użyć `CFrameWnd` bezpośrednio, bez wyprowadzanie własne klasy.  
  
 SDI aplikacji zwykle obsługuje jeden typ pliku, co powoduje tylko jeden `CSingleDocTemplate` obiektu. Tylko jeden dokument może być otwarty naraz.  
  
 Nie trzeba wywołać żadnego członka funkcji `CSingleDocTemplate` z wyjątkiem konstruktora. Uchwyty framework `CSingleDocTemplate` obiekty wewnętrznie.  
  
 Aby uzyskać więcej informacji na temat używania `CSingleDocTemplate`, zobacz [szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [Cdoctemplate —](../../mfc/reference/cdoctemplate-class.md)  
  
 `CSingleDocTemplate`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="csingledoctemplate"></a>CSingleDocTemplate::CSingleDocTemplate  
 Konstruuje `CSingleDocTemplate` obiektu.  
  
```  
CSingleDocTemplate(
    UINT nIDResource,  
    CRuntimeClass* pDocClass,  
    CRuntimeClass* pFrameClass,  
    CRuntimeClass* pViewClass);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDResource`  
 Określa identyfikator zasoby używane do typu dokumentu. Może to obejmować menu, ikona tabeli akceleratora i zasoby ciągów.  
  
 Zasób ciągu składa się z maksymalnie siedem podciągów oddzielone znakiem "\n" (znak "\n" jest potrzebny jako symbol zastępczy, jeśli nie dołączono podciągu jednak znakami "\n" nie są konieczne); te podciągów opisu typu dokumentu. Aby uzyskać informacje o podciągów, zobacz [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Na przykład:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_MAINFRAME "MyCalc Windows Application\nSheet\nWorksheet\n Worksheets (*.myc)\n.myc\nMyCalcSheet\n MyCalc Worksheet"`  
  
 `END`  
  
 Można edytować tego ciągu za pomocą Edytora ciągu; cały ciąg jest wyświetlany jako pojedynczy wpis w edytorze ciągu nie jako siedmiu oddzielne wpisy.  
  
 Aby uzyskać więcej informacji na temat tych typów zasobów, zobacz [edytor ciągów](../../windows/string-editor.md).  
  
 `pDocClass`  
 Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa jest **CDocument**-klasy definiowane w celu odzwierciedlenia dokumentów.  
  
 `pFrameClass`  
 Wskazuje `CRuntimeClass` obiekt klasy ramki okna. Ta klasa może być `CFrameWnd`-klasy lub może być `CFrameWnd` sam Jeśli domyślne zachowanie dla użytkownika głównego okna ramowego.  
  
 `pViewClass`  
 Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa jest `CView`-klasy zdefiniuj do wyświetlania dokumentów.  
  
### <a name="remarks"></a>Uwagi  
 Dynamiczne przydzielanie `CSingleDocTemplate` obiektu i przekaż go do `CWinApp::AddDocTemplate` z `InitInstance` funkcji członkowskiej klasy aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocViewSDI#13](../../mfc/codesnippet/cpp/csingledoctemplate-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocViewSDI#14](../../mfc/codesnippet/cpp/csingledoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC DOCKTOOL](../../visual-cpp-samples.md)   
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Cdocument — klasa](../../mfc/reference/cdocument-class.md)   
 [Cframewnd — klasa](../../mfc/reference/cframewnd-class.md)   
 [Klasa CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)   
 [Cview — klasa](../../mfc/reference/cview-class.md)   
 [Cwinapp — klasa](../../mfc/reference/cwinapp-class.md)
