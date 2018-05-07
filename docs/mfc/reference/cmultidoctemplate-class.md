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
ms.openlocfilehash: 7b53228b6983c0293eb288cd0f38669d1b5db928
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cmultidoctemplate-class"></a>Klasa CMultiDocTemplate
Definiuje szablonu dokumentu, który implementuje interfejs dokumentu wielokrotnego (MDI).  
  
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
 Aplikacja MDI wykorzystuje głównego okna ramowego jako obszaru roboczego, w którym użytkownik może otwierać okien ramowych dokumentu zero lub więcej, z których każdy zawiera dokument. Aby uzyskać bardziej szczegółowy opis MDI, zobacz *Windows interfejsu wskazówki dotyczące projektowania oprogramowania*.  
  
 Szablon dokumentu definiuje relacje trzy typy klas:  
  
-   Klasy dokumentów, który pochodzi od [CDocument](../../mfc/reference/cdocument-class.md).  
  
-   Klasy widoku, która zawiera dane z klasy dokumentu wymienionych powyżej. Można pochodzi ta klasa z [CView](../../mfc/reference/cview-class.md), `CScrollView`, `CFormView`, lub `CEditView`. (Można również użyć `CEditView` bezpośrednio.)  
  
-   Klasy okna ramki, który zawiera widok. Dla szablonu dokumentów MDI może pochodzi ta klasa z `CMDIChildWnd`, lub jeśli nie potrzebujesz dostosować zachowanie okien ramowych dokumentu, można użyć [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) bezpośrednio, bez wyprowadzanie własne klasy.  
  
 Aplikacja MDI może obsługiwać więcej niż jednego typu dokumentu, a dokumenty różnych typów może być otwarty, w tym samym czasie. Aplikacja ma jeden szablon dokumentu dla każdego typu dokumentu, który go obsługuje. Na przykład jeśli aplikacja MDI obsługuje arkusze kalkulacyjne i dokumenty tekstowe, aplikacja ma dwa `CMultiDocTemplate` obiektów.  
  
 Aplikacja używa szablony dokumentu, podczas tworzenia nowego dokumentu. Jeśli aplikacja obsługuje więcej niż jednego typu dokumentu, ramach pobiera nazwy typów obsługiwanych dokumentu z szablonów dokumentów i wyświetla je na liście w oknie dialogowym Nowy plik. Gdy użytkownik wybrał typu dokumentu, aplikacja tworzy obiekt klasy dokumentu, obiekt window ramki i obiekt widoku i dołącza je do siebie.  
  
 Nie należy wywołać żadnego członka funkcji `CMultiDocTemplate` z wyjątkiem konstruktora. Uchwyty framework `CMultiDocTemplate` obiekty wewnętrznie.  
  
 Aby uzyskać więcej informacji na temat `CMultiDocTemplate`, zobacz [szablony dokumentów i proces tworzenia dokumentu/widoku](../../mfc/document-templates-and-the-document-view-creation-process.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [Cdoctemplate —](../../mfc/reference/cdoctemplate-class.md)  
  
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
 `nIDResource`  
 Określa identyfikator zasoby używane do typu dokumentu. Może to obejmować menu, ikona tabeli akceleratora i zasoby ciągów.  
  
 Zasób ciągu składa się z maksymalnie siedem podciągów oddzielone znakiem "\n" (znak "\n" jest potrzebny jako symbolu zastępczego, jeśli nie dołączono podciągu jednak znakami "\n" nie są konieczne); te podciągów opisu typu dokumentu. Aby uzyskać informacje na podciągów, zobacz [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Ten zasób ciągu znajduje się w pliku zasobów aplikacji. Na przykład:  
  
 `// MYCALC.RC`  
  
 `STRINGTABLE PRELOAD DISCARDABLE`  
  
 `BEGIN`  
  
 `IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"`  
  
 `END`  
  
 Należy pamiętać, że ciąg rozpoczyna się od znaku "\n"; jest to spowodowane pierwszego podciągu nie jest używany przez aplikacje MDI i dlatego nie jest dołączana. Można edytować tego ciągu za pomocą Edytora ciągu; cały ciąg jest wyświetlany jako pojedynczy wpis w edytorze ciągu nie jako siedmiu oddzielne wpisy.  
  
 Aby uzyskać więcej informacji na temat tych typów zasobów, zobacz [edytory zasobów](../../windows/resource-editors.md).  
  
 `pDocClass`  
 Wskazuje `CRuntimeClass` obiekt klasy dokumentu. Ta klasa jest **CDocument**-klasy definiowane w celu odzwierciedlenia dokumentów.  
  
 `pFrameClass`  
 Wskazuje `CRuntimeClass` obiekt klasy okien ramowych. Ta klasa może być `CMDIChildWnd`-klasy lub może być `CMDIChildWnd` sam Jeśli domyślne zachowanie dla Twojego okien ramowych dokumentu.  
  
 `pViewClass`  
 Wskazuje `CRuntimeClass` obiekt klasy widoku. Ta klasa jest `CView`-klasy zdefiniuj do wyświetlania dokumentów.  
  
### <a name="remarks"></a>Uwagi  
 Dynamiczne przydzielanie jedną `CMultiDocTemplate` obiekt dla każdego typu dokumentu, który obsługuje i każdy z nich do przekazania aplikacji `CWinApp::AddDocTemplate` z `InitInstance` funkcji członkowskiej klasy aplikacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#92](../../mfc/codesnippet/cpp/cmultidoctemplate-class_1.cpp)]  
  
 Oto przykład drugiego.  
  
 [!code-cpp[NVC_MFCDocView#93](../../mfc/codesnippet/cpp/cmultidoctemplate-class_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cdoctemplate — klasa](../../mfc/reference/cdoctemplate-class.md)   
 [Klasa CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)   
 [Klasa CWinApp](../../mfc/reference/cwinapp-class.md)
