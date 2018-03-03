---
title: "Dostęp do ODBC i SQL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- API calls [C++], calling DAO or ODBC directly
- Windows API [C++], calling from MFC
- ODBC API functions [C++]
- ODBC API functions [C++], calling from MFC
- SQL [C++], calling ODBC API functions
- ODBC [C++], API functions
ms.assetid: 5613d7dc-00b7-4646-99ae-1116c05c52b4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25e9533752e47e5cf3ea50e594a23b99e19355ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="access-to-odbc-and-sql"></a>Dostęp do ODBC i SQL
Microsoft Foundation Class Library hermetyzuje wiele wywołań interfejsu API systemu Windows i nadal umożliwia bezpośrednie wywołania dowolnej funkcji interfejsu API systemu Windows. Klasy baz danych zapewniają elastyczność sam w odniesieniu do interfejsu API ODBC. Gdy klasy baz danych zabezpieczyć z znacznie złożoność ODBC, należy wywołać funkcji ODBC API bezpośrednio z dowolnego miejsca w programie.  
  
 Podobnie, klas baz danych zabezpieczyć możesz z konieczności przechodzenia bardzo z [SQL](../../data/odbc/sql.md), ale można użyć SQL bezpośrednio, jeśli chcesz. Obiekty rekordów można dostosować przez przekazanie niestandardową instrukcję SQL (lub ustawienie fragmenty instrukcji domyślny) po otwarciu zestawu rekordów. Można również ustawić bezpośrednio za pomocą wywołania SQL [ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) funkcji członkowskiej klasy [cdatabase —](../../mfc/reference/cdatabase-class.md).  
  
 Aby uzyskać więcej informacji, zobacz [ODBC: wywołanie ODBC API funkcji bezpośrednio](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) i [SQL: Tworzenie wywołań SQL bezpośredniego (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [ODBC i MFC](../../data/odbc/odbc-and-mfc.md)