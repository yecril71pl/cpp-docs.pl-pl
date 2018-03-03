---
title: Klasa CUserException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CUserException
dev_langs:
- C++
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4613f2ba06ffa697df219172b98a5cf193c1f3b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cuserexception-class"></a>Klasa CUserException
Element zgłaszany, aby zatrzymać operację użytkownika końcowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CUserException : public CSimpleException  
```  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CUserException` Jeśli chcesz użyć mechanizm wyjątków throw/catch wyjątków specyficzne dla aplikacji. "Użytkownika" w nazwie klasy mogą być interpretowane jako "Mój użytkownika wykonała wyjątkowych o konieczności obsługi."  
  
 A `CUserException` jest zazwyczaj zgłaszany po wywołaniu funkcji globalnej `AfxMessageBox` do powiadamiania użytkownika, że operacja nie powiodła się. Podczas pisania program obsługi wyjątku obsługuje wyjątek specjalnie, ponieważ użytkownik zwykle już został powiadomiony o awarii. Platformę zgłasza wyjątek w niektórych przypadkach. Aby zgłosić `CUserException` samodzielnie, użytkownika, a następnie wywołać funkcji globalnej `AfxThrowUserException`.  
  
 W poniższym przykładzie funkcja zawierająca operacje, które mogą się nie powieść ostrzega o tym użytkownika i zgłasza `CUserException`. Wywołania funkcji przechwytuje wyjątek i obsługuje on specjalnie:  
  
 [!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]  
  
 Aby uzyskać więcej informacji na temat używania `CUserException`, zapoznaj się z artykułem [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 [CSimpleException](../../mfc/reference/csimpleexception-class.md)  
  
 `CUserException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CException](../../mfc/reference/cexception-class.md)
