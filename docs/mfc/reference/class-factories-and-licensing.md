---
title: Fabryki klas i Licencjonowanie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79710cb1fa67ec8315fe287364126f88b4b498d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="class-factories-and-licensing"></a>Fabryki klas i licencjonowanie
Aby utworzyć wystąpienia formantu OLE, aplikacji kontenera wywołania funkcji członkowskiej klasy fabryki klasy formantu. Ponieważ formantu rzeczywistego obiektu OLE, fabryki klasy jest odpowiedzialny za tworzenie wystąpienia formantu. Każda klasa formantu OLE musi mieć fabrykę klas.  
  
 Inną ważną funkcją formantów OLE jest możliwość wymuszania licencji. ControlWizard pozwala na uwzględnienie licencjonowania podczas tworzenia projektu kontroli. Aby uzyskać więcej informacji dotyczących licencji formantu, zobacz artykuł [formantów ActiveX: Licencjonowanie formantu ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
 W poniższej tabeli wymieniono kilka makra i funkcje używane zadeklarować i wdrożenie fabryki klasy formantu i licencji formantu.  
  
### <a name="class-factories-and-licensing"></a>Fabryki klas i licencjonowanie  
  
|||  
|-|-|  
|[DECLARE_OLECREATE_EX —](#declare_olecreate_ex)|Deklaruje fabryki klasy dla formantu lub właściwości strony dla obiektów OLE.|  
|[IMPLEMENT_OLECREATE_EX —](#implement_olecreate_ex)|Implementuje formantu `GetClassID` funkcji i deklaruje wystąpienie fabryki klasy.|  
|[BEGIN_OLEFACTORY —](#begin_olefactory)|Rozpoczyna się deklaracji funkcji licencjonowania.|  
|[END_OLEFACTORY —](#end_olefactory)|Kończy się deklaracji funkcji licencjonowania.|  
|[Afxverifylicfile —](#afxverifylicfile)|Sprawdza, czy formant jest licencjonowany do użycia na danym komputerze.|  
  
##  <a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX —  
 Deklaruje fabrykę klas i `GetClassID` funkcji członkowskiej klasy formantu.  
  
```   
DECLARE_OLECREATE_EX(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy formantu.  
  
### <a name="remarks"></a>Uwagi  
 Używanie tego makra w pliku nagłówka klasy formantu, który nie obsługuje licencjonowania.  
  
 Należy pamiętać, że to makro pełni tę samą funkcję jak w poniższym przykładzie kodu:  
  
 [!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX —  
 Implementuje fabryki klasy formantu i [Procedura GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) funkcji członkowskiej klasy formantu.  
  
```   
IMPLEMENT_OLECREATE_EX(
   class_name,   
    external_name,    
    l,   
    w1,   
    w2,   
    b1,   
    b2,   
    b3,   
    b4,   
    b5,   
    b6,   
    b7,
    b8)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy strony właściwości formantu.  
  
 *external_name*  
 Nazwa obiektu widoczne dla aplikacji.  
  
 *l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*  
 Składniki klasy **CLSID**. Aby uzyskać więcej informacji o tych parametrów, zobacz uwagi dla [implement_olecreate —](run-time-object-model-services.md#implement_olecreate).  
  
### <a name="remarks"></a>Uwagi  
 To makro musi występować w pliku implementacji dla dowolnej klasy formantu, który używa `DECLARE_OLECREATE_EX` makro lub `BEGIN_OLEFACTORY` i `END_OLEFACTORY` makra. Zewnętrzna nazwa to identyfikator formantu OLE, który jest dostępny dla innych aplikacji. Kontenery ta nazwa jest używana do żądania obiektu tej klasy formantu.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="begin_olefactory"></a>BEGIN_OLEFACTORY —  
 Rozpoczyna się deklaracja fabryce klasy w pliku nagłówka klasy formantu.  
  
``` 
BEGIN_OLEFACTORY(class_name)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Określa nazwę klasy formantu fabryki klasy, których to.  
  
### <a name="remarks"></a>Uwagi  
 Deklaracje funkcji licencjonowania fabryki klasy powinny one zacząć od razu po `BEGIN_OLEFACTORY`.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="end_olefactory"></a>END_OLEFACTORY —  
 Kończy się deklaracja fabryki klasy formantu.  
  
```  
END_OLEFACTORY(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa fabryki klasy, których to klasy formantu.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="afxverifylicfile"></a>Afxverifylicfile —  
 Wywołanie tej funkcji, aby sprawdzić, czy plik licencji o nazwie `pszLicFileName` jest nieprawidłowa dla formantu OLE.  
  
```   
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,  
    LPCTSTR  pszLicFileName,  
    LPOLESTR  pszLicFileContents,  
    UINT cch = -1); 
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Dojście wystąpienia skojarzony z formantem licencjonowane biblioteki dll.  
  
 `pszLicFileName`  
 Wskazuje ciąg znaków zakończony znakiem null, zawierający nazwę pliku licencji.  
  
 `pszLicFileContents`  
 Punkty sekwencji bajtów, która musi być zgodna sekwencji znaleziono na początku pliku licencji.  
  
 `cch`  
 Liczba znaków w `pszLicFileContents`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli istnieje plik licencji rozpoczyna się od sekwencja znaków w `pszLicFileContents`; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `cch` wynosi -1, korzysta z tej funkcji:  
  
 [!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
