---
title: Klasa CInvalidArgException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
dev_langs: C++
helpviewer_keywords: CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 03f9bea1c9e5e88856bbf5a5aa2e824a2c99963c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cinvalidargexception-class"></a>Klasa CInvalidArgException
Ta klasa reprezentuje nieprawidłowy argument warunku wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CInvalidArgException : public CSimpleException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|Konstruktor.|  
  
## <a name="remarks"></a>Uwagi  
 A `CInvalidArgException` obiekt reprezentuje nieprawidłowy argument warunku wyjątku.  
  
 Aby uzyskać więcej informacji dotyczących obsługi wyjątków, zobacz [cexception — klasa](../../mfc/reference/cexception-class.md) tematu i [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CInvalidArgException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="cinvalidargexception"></a>CInvalidArgException::CInvalidArgException  
 Konstruktor.  
  
```  
CInvalidArgException();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie używaj tego konstruktora bezpośrednio; Wywołanie funkcji globalnych **AfxThrowInvalidArgException**.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CSimpleException](../../mfc/reference/csimpleexception-class.md)
