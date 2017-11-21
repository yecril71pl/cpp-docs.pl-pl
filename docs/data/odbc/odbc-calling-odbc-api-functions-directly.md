---
title: "ODBC: Wywołanie interfejsu API ODBC funkcje bezpośrednio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC API functions [C++], calling
- ODBC [C++], catalog functions
- ODBC API functions [C++]
- APIs [C++], calling
- ODBC classes [C++], vs. ODBC API
- direct ODBC API calls
- catalog functions (ODBC)
- catalog functions (ODBC), calling
- ODBC [C++], API functions
ms.assetid: 4295f1d9-4528-4d2e-bd6a-c7569953c7fa
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b7304d83eca004952eb65ed6c5d16e4ce816bb56
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="odbc-calling-odbc-api-functions-directly"></a>ODBC: bezpośrednie wywoływanie funkcji ODBC API
Klasy baz danych zapewnia prostszy interfejs do [źródła danych](../../data/odbc/data-source-odbc.md) niż ODBC. W związku z tym klasy nie hermetyzować wszystkich interfejsu API ODBC. Dla żadnej funkcji, która znajduje się poza możliwości klas należy wywołać funkcji ODBC API bezpośrednio. Na przykład, należy wywołać funkcji katalogu ODBC (**:: SQLColumns**, **:: SQLProcedures**, **:: SQLTables**i inne) bezpośrednio.  
  
> [!NOTE]
>  ODBC — źródła danych są dostępne za pośrednictwem klas MFC ODBC, zgodnie z opisem w tym temacie lub za pośrednictwem klas MFC obiekt DAO (Data Access).  
  
 Aby wywoływanie funkcji ODBC API bezpośrednio, należy wykonać te same kroki, które może wykonać, jeśli zostały wywołania bez struktury. One kroki są:  
  
-   Przydziel magazyn do żadnych wyników, który wywołanie zwraca.  
  
-   Przekaż ODBC **HDBC** lub **HSTMT** obsługi, w zależności od parametru podpisu funkcji. Użyj [afxgethenv —](../../mfc/reference/database-macros-and-globals.md#afxgethenv) makro można pobrać dojścia ODBC.  
  
     Zmienne Członkowskie **CDatabase::m_hdbc** i **CRecordset::m_hstmt** są dostępne, dzięki czemu nie trzeba przydzielić i zainicjować te samodzielnie.  
  
-   Być może wywoływać dodatkowe funkcje ODBC przygotować do lub wykonaj połączenie główne.  
  
-   Cofnięcie przydziału magazynu, aby zakończyć.  
  
 Aby uzyskać więcej informacji na temat tych kroków, zobacz [Otwórz połączenie bazy danych (ODBC)](https://msdn.microsoft.com/en-us/library/ms710252.aspx) zestawu SDK w dokumentacji MSDN.  
  
 Oprócz tych kroków należy wykonać dodatkowe czynności, aby sprawdzić wartości zwracane przez funkcję, upewnij się, że program nie oczekuje na wywołanie asynchroniczne zakończyć i tak dalej. Te kroki ostatniego może uprościć przy użyciu `AFX_SQL_ASYNC` i `AFX_SQL_SYNC` makra. Aby uzyskać więcej informacji, zobacz [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołania MFC*.  

  
## <a name="see-also"></a>Zobacz też  
 [Podstawy ODBC](../../data/odbc/odbc-basics.md)
