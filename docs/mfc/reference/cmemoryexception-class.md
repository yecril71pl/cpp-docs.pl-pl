---
title: Klasa CMemoryException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
dev_langs:
- C++
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12971af6bed7c04c6f6f214f0b583a4f7e6eb7a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366307"
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
  
##  <a name="cmemoryexception"></a>  CMemoryException::CMemoryException  
 Konstruuje `CMemoryException` obiektu.  
  
```  
CMemoryException();  
```  
  
### <a name="remarks"></a>Uwagi  
 Nie używaj tego konstruktora bezpośrednio, ale raczej wywołanie funkcji globalnych [afxthrowmemoryexception —](exception-processing.md#afxthrowmemoryexception). tym globalnych funkcji będzie możliwe w sytuacji braku pamięci, ponieważ tworzy on obiekt wyjątku w uprzednio alokacji pamięci. Aby uzyskać więcej informacji na temat wyjątek podczas przetwarzania, zobacz artykuł [wyjątki](../exception-handling-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Cexception — klasa](cexception-class.md)   
 [Wykres hierarchii](../hierarchy-chart.md)



