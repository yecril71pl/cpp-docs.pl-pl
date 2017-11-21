---
title: Klasa COleControlModule | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: OleControlModule
dev_langs: C++
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0153adbae458d0f4ab432c2c7cb8c71621d76418
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="colecontrolmodule-class"></a>Klasa COleControlModule
Klasa podstawowa, z którego pochodzi obiektu modułu formantu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleControlModule : public CWinApp  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia funkcje Członkowskie inicjowania modułu formantu. Każdego modułu OLE używa Microsoft Foundation classes może zawierać tylko jeden obiekt pochodzący od `COleControlModule`. Ten obiekt jest tworzony w przypadku innych obiektów globalnych C++ są wykonane. Zadeklarować Twojej pochodnej `COleControlModule` obiektów na poziomie globalnym.  
  
 Aby uzyskać więcej informacji na temat używania `COleControlModule` , zobacz [CWinApp](../../mfc/reference/cwinapp-class.md) klasy i artykułu [formantów ActiveX](../../mfc/mfc-activex-controls.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [Cwinthread —](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC TESTHELP](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)



