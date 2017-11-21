---
title: "Połączenie ze źródłem danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ea788921b72d06deb44ed67ecdfa49c5efe43ed2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="connecting-to-a-data-source"></a>Nawiązywanie połączenia ze źródłem danych
Źródła danych ODBC jest określony zbiór danych, informacje wymagane do uzyskania dostępu do danych oraz lokalizację źródła danych, które można opisać za pomocą nazwy źródła danych. Z punktu widzenia programu źródło danych zawiera dane, systemu DBMS, sieci (jeśli istnieje) i ODBC.  
  
 Aby uzyskać dostęp do danych ze źródła danych, program nawiązania połączenia ze źródłem danych. Dostęp do wszystkich danych odbywa się za pośrednictwem tego połączenia.  
  
 Połączenia źródła danych są hermetyzowane przez klasę [cdatabase —](../../mfc/reference/cdatabase-class.md). Gdy `CDatabase` obiekt jest połączony ze źródłem danych, można wykonywać następujące czynności:  
  
-   Utworzyć [zestawy rekordów](../../mfc/reference/crecordset-class.md), który wybierania rekordów z tabel lub kwerend.  
  
-   Zarządzanie [transakcji](../../data/odbc/transaction-odbc.md), przetwarzanie wsadowe aktualizacji, więc cała są jednocześnie zatwierdzone do źródła danych (lub cała transakcja jest wycofywany ponownie, więc źródło danych jest w niezmienionym) — Jeśli źródło danych obsługuje poziomu transakcji.  
  
-   Wykonaj bezpośrednio [SQL](../../data/odbc/sql.md) instrukcje.  
  
 Po zakończeniu pracy z połączeniem źródła danych, Zamknij `CDatabase` obiektu i zniszczyć lub użyć go ponownie dla nowego połączenia. Aby uzyskać więcej informacji na temat połączeń ze źródłem danych, zobacz [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [ODBC i MFC](../../data/odbc/odbc-and-mfc.md)