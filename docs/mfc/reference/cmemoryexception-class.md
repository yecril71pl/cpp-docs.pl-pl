---
title: Klasa CMemoryException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
dev_langs: C++
helpviewer_keywords: CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 13130321dd26612b2bbd24457e02e09ce5fe1ec6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmemoryexception-class"></a>Klasa CMemoryException
Reprezentuje warunku wyjątku braku pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMemoryException : public CSimpleException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMemoryException::CMemoryException](#cmemoryexception)|Konstruuje `CMemoryException` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Nie dalsze kwalifikacja jest konieczne lub niemożliwe. Wyjątki pamięci są generowane automatycznie przez **nowe**. Jeśli piszesz funkcji pamięci przy użyciu `malloc`, na przykład, możesz są odpowiedzialne za zgłaszanie wyjątków pamięci.  
  
 Aby uzyskać więcej informacji na temat `CMemoryException`, zapoznaj się z artykułem [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CMemoryException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="cmemoryexception"></a>CMemoryException::CMemoryException  
 Konstruuje `CMemoryException` obiektu.  
  
```  
CMemoryException();  
```  
  
### <a name="remarks"></a>Uwagi  
 Nie używaj tego konstruktora bezpośrednio, ale raczej wywołanie funkcji globalnych [afxthrowmemoryexception —](exception-processing.md#afxthrowmemoryexception). tym globalnych funkcji będzie możliwe w sytuacji braku pamięci, ponieważ tworzy on obiekt wyjątku w uprzednio alokacji pamięci. Aby uzyskać więcej informacji na temat wyjątek podczas przetwarzania, zobacz artykuł [wyjątki](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Cexception — klasa](cexception-class.md)   
 [Diagram hierarchii](../hierarchy-chart.md)



