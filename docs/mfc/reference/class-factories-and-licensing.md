---
title: Fabryki klas i Licencjonowanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: abb9d5ca169edf28bb3f72c26e644894c12ccb93
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336235"
---
# <a name="class-factories-and-licensing"></a>Fabryki klas i licencjonowanie
Aby utworzyć wystąpienie kontrolki OLE, aplikacji kontenera wywołania funkcji składowej typu fabryki klas formantu. Ponieważ formant do rzeczywistego obiektu OLE, fabryki klas jest odpowiedzialny za tworzenie wystąpienia formantu. Każda klasa sterowania OLE musi mieć fabrykę klas.  
  
 Inną ważną cechą formantów OLE jest możliwość wymuszania licencji. ControlWizard umożliwia wykorzystanie, licencjonowania podczas tworzenia projektu kontroli. Aby uzyskać więcej informacji na temat licencjonowania formantów, zobacz artykuł [kontrolek ActiveX: Licencjonowanie kontrolki ActiveX](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
 W poniższej tabeli wymieniono kilka makra i funkcje używane do deklarowania i implementowanie kontroli nad fabryki klas i licencji formantu.  
  
### <a name="class-factories-and-licensing"></a>Fabryki klas i licencjonowanie  
  
|||  
|-|-|  
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Deklaruje fabryki klas dla formantu lub właściwości strony dla obiektów OLE.|  
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementuje formant `GetClassID` funkcji i deklaruje wystąpienie fabryki klas.|  
|[BEGIN_OLEFACTORY](#begin_olefactory)|Rozpoczyna się deklaracji wszystkie funkcje licencjonowania.|  
|[END_OLEFACTORY](#end_olefactory)|Kończy się w deklaracji funkcji licencjonowania.|  
|[Afxverifylicfile —](#afxverifylicfile)|Sprawdza, czy formant jest licencjonowany do użycia na danym komputerze.|  
  
##  <a name="declare_olecreate_ex"></a>  DECLARE_OLECREATE_EX  
 Deklaruje fabryki klas i `GetClassID` funkcji składowej klasy kontrolki.  
  
```   
DECLARE_OLECREATE_EX(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy kontrolki.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra w plik nagłówkowy klasy formantu, formant, który nie obsługuje licencjonowania.  
  
 Należy zwrócić uwagę na to, że to makro pełni tę samą funkcję, jak w następującym przykładzie kodu:  
  
 [!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="implement_olecreate_ex"></a>  IMPLEMENT_OLECREATE_EX  
 Implementuje kontroli nad fabryki klas i [Procedura GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) funkcji składowej klasy kontrolki.  
  
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
 Składniki CLSID tej klasy. Aby uzyskać więcej informacji na temat tych parametrów, zobacz uwagi dla [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).  
  
### <a name="remarks"></a>Uwagi  
 To makro musi znajdować się w pliku implementacji dla każdej klasy kontrolki, która używa DECLARE_OLECREATE_EX — makro lub BEGIN_OLEFACTORY i END_OLEFACTORY makra. Zewnętrzna nazwa to identyfikator kontrolki OLE, która jest widoczna dla innych aplikacji. Ta nazwa jest używana przez kontenery na żądanie obiekt tej klasy kontrolki.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="begin_olefactory"></a>  BEGIN_OLEFACTORY  
 Rozpoczyna się deklaracji fabryki klas w pliku nagłówkowym Twojej klasy kontrolki.  
  
``` 
BEGIN_OLEFACTORY(class_name)  
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Określa nazwę klasy kontrolki fabryki klas, których to.  
  
### <a name="remarks"></a>Uwagi  
 Deklaracje fabryki klas licencjonowania funkcji ma się zacząć od razu po BEGIN_OLEFACTORY.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="end_olefactory"></a>  END_OLEFACTORY  
 Kończy się deklaracji kontroli nad fabryki klas.  
  
```  
END_OLEFACTORY(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy kontrolki fabryki klas, których to.  
  
### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  
  
##  <a name="afxverifylicfile"></a>  Afxverifylicfile —  
 Wywołaj tę funkcję, aby sprawdzić, czy plik licencji o nazwie określonej przez `pszLicFileName` nadaje się do sterowania OLE.  
  
```   
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,  
    LPCTSTR  pszLicFileName,  
    LPOLESTR  pszLicFileContents,  
    UINT cch = -1); 
```  
  
### <a name="parameters"></a>Parametry  
 *hInstance*  
 Dojście wystąpienia jest skojarzony z licencjonowany formant biblioteki dll.  
  
 *pszLicFileName*  
 Wskazuje ciąg znaków zakończony znakiem null zawierający nazwę pliku licencji.  
  
 *pszLicFileContents*  
 Wskazuje na sekwencję bajtów, która musi być zgodna z sekwencji znalezione na początku pliku licencji.  
  
 *CCH*  
 Liczba znaków w *pszLicFileContents*.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli istnieje plik licencji i zaczyna się od sekwencji znaków w *pszLicFileContents*; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *cch* wynosi -1, korzysta z tej funkcji:  
  
 [!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]  

### <a name="requirements"></a>Wymagania  
  **Nagłówek** afxctl.h  

## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
