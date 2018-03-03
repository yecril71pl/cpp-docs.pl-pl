---
title: Klasa CNotSupportedException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
dev_langs:
- C++
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4013b26e3c07d6ec2a729bf9868db48923e35f86
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cnotsupportedexception-class"></a>Klasa CNotSupportedException
Reprezentuje wyjątek, który jest wynikiem żądania nieobsługiwanej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CNotSupportedException : public CSimpleException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Konstruuje `CNotSupportedException` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Nie dalsze kwalifikacja jest konieczne lub niemożliwe.  
  
 Aby uzyskać więcej informacji na temat używania `CNotSupportedException`, zapoznaj się z artykułem [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CNotSupportedException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="cnotsupportedexception"></a>CNotSupportedException::CNotSupportedException  
 Konstruuje `CNotSupportedException` obiektu.  
  
```  
CNotSupportedException();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie używaj tego konstruktora bezpośrednio, ale raczej wywołanie funkcji globalnych [afxthrownotsupportedexception —](exception-processing.md#afxthrownotsupportedexception). Aby uzyskać więcej informacji na temat wyjątek podczas przetwarzania, zobacz artykuł [obsługi wyjątków w MFC](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Cexception — klasa](cexception-class.md)   
 [Wykres hierarchii](../hierarchy-chart.md)


