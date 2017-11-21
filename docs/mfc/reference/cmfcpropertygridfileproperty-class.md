---
title: Klasa CMFCPropertyGridFileProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
dev_langs: C++
helpviewer_keywords: CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9f21922a2461602124c54cc3974cae4762e2bc27
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcpropertygridfileproperty-class"></a>Klasa CMFCPropertyGridFileProperty
`CMFCPropertyGridFileProperty` Klasa obsługuje elementu formantu listy właściwości, które otwiera okno dialogowe wyboru pliku.  
  
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
|`CMFCPropertyGridFileProperty::GetThisClass`|Używany przez platformę do uzyskania wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) obiekt, który jest skojarzony z tym typem klasy.|  
|`CMFCPropertyGridFileProperty::OnClickButton`|(Przesłania [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|  
  
### <a name="remarks"></a>Uwagi  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty  
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
 [in]`strName`  
 Nazwa właściwości.  
  
 [in]`bOpenFileDialog`  
 `TRUE`Aby otworzyć **Otwieranie pliku** okno dialogowe; `FALSE` otworzyć **Zapisz plik** okno dialogowe.  
  
 [in]`strFileName`  
 Początkowa nazwa pliku.  
  
 [in]`lpszDefExt`  
 Ciąg jednego lub więcej rozszerzeń nazw plików. Wartość domyślna to `NULL`.  
  
 [in]`dwFlags`  
 Flagi — okno dialogowe. Wartość domyślna to bitowe połączenie (lub) `OFN_HIDEREADONLY` i `OFN_OVERWRITEPROMPT`.  
  
 [in]`lpszFilter`  
 Ciąg co najmniej jeden filtr plików. Wartość domyślna to `NULL`.  
  
 [in]`lpszDescr`  
 Opis elementu właściwości. Wartość domyślna to `NULL`.  
  
 [in]`dwData`  
 Dane specyficzne dla aplikacji, które jest skojarzone z elementem właściwości. Na przykład 32-bitową liczbą całkowitą lub wskaźnik do innych danych. Wartość domyślna to 0.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać pełną listę dostępnych flag, zobacz [struktury OPENFILENAME](https://msdn.microsoft.com/library/ms646839.aspx).  
  
### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia obiektu przy użyciu konstruktora `CMFCPropertyGridFileProperty` klasy. Ten przykład jest częścią [programu Visual Studio przykład](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [Klasa CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)
