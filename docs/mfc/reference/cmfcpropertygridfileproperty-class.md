---
title: Klasa CMFCPropertyGridFileProperty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82d1b4c3790f50032ac9775febf920e0e8c6c547
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700841"
---
# <a name="cmfcpropertygridfileproperty-class"></a>Klasa CMFCPropertyGridFileProperty
`CMFCPropertyGridFileProperty` Klasa obsługuje element formantu listy właściwości, które otwiera okno dialogowe wyboru pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Konstruuje `CMFCPropertyGridFileProperty` obiektu.|  
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CMFCPropertyGridFileProperty::GetThisClass`|Używane przez architekturę, aby uzyskać wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiektu, który jest skojarzony z tym typem klasy.|  
|`CMFCPropertyGridFileProperty::OnClickButton`|(Przesłania [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfileproperty"></a>  CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty  
 Konstruuje `CMFCPropertyGridFileProperty` obiektu.  
  
```  
CMFCPropertyGridFileProperty(
    const CString& strName,  
    BOOL bOpenFileDialog,  
    const CString& strFileName,  
    LPCTSTR lpszDefExt=NULL,  
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,  
    LPCTSTR lpszFilter=NULL,  
    LPCTSTR lpszDescr=NULL,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parametry  
*strName*<br/>
[in] Nazwa właściwości.  
  
*bOpenFileDialog*<br/>
[in] Wartość true, otwórz **Otwórz plik** okno dialogowe; Wartość FALSE, aby otworzyć **Zapisz plik** okno dialogowe.  
  
*strFileName*<br/>
[in] Początkowa nazwa pliku.  
  
*lpszDefExt*<br/>
[in] Ciąg o jeden lub więcej rozszerzeń nazw plików. Wartością domyślną jest NULL.  
  
*Flagidw*<br/>
[in] Flagi okno dialogowe. Wartością domyślną jest bitową kombinacją (lub) OFN_HIDEREADONLY i OFN_OVERWRITEPROMPT.  
  
*lpszFilter*<br/>
[in] Ciąg o co najmniej jeden filtr pliku. Wartością domyślną jest NULL.  
  
*lpszDescr*<br/>
[in] Opis elementu właściwości. Wartością domyślną jest NULL.  
  
*dwData*<br/>
[in] Dane specyficzne dla aplikacji, które jest skojarzone z elementem właściwości. Na przykład 32-bitowej liczby całkowitej lub wskaźnika z innymi danymi. Wartość domyślna to 0.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać pełną listę dostępnych flag, zobacz [LPSTRFILE struktury openfilename](/windows/desktop/api/commdlg/ns-commdlg-tagofna).  
  
### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia obiektu przy użyciu konstruktora `CMFCPropertyGridFileProperty` klasy. W tym przykładzie jest częścią [Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
