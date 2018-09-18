---
title: Łączenie ze źródłem danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- database connections [C++], ODBC
- ODBC connections [C++], using
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: ef6c8c98-5979-43a8-9fb5-5bb06fc59f36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4be8214ad036d67a02ce4b9c5935d3deb92252c1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061100"
---
# <a name="connecting-to-a-data-source"></a>Nawiązywanie połączenia ze źródłem danych

Źródła danych ODBC jest określony zbiór danych, informacje wymagane do dostępu do danych i lokalizacja źródła danych, które można opisać za pomocą nazwy źródła danych. Z punktu widzenia programu źródło danych zawiera dane, systemu DBMS, sieci (jeśli istnieje) i ODBC.  
  
Dostęp do danych ze źródła danych, program musi najpierw nawiąż połączenie ze źródłem danych. Dostępu do wszystkich danych odbywa się za pośrednictwem tego połączenia.  
  
Połączenia źródła danych są hermetyzowane przez klasę [CDatabase](../../mfc/reference/cdatabase-class.md). Gdy `CDatabase` obiekt jest połączony ze źródłem danych, możesz:  
  
- Konstruowania [zestawy rekordów](../../mfc/reference/crecordset-class.md), które wybrać rekordy z tabel lub kwerend.  
  
- Zarządzanie [transakcji](../../data/odbc/transaction-odbc.md), aktualizacje przetwarzania wsadowego, więc wszystkie zobowiązujemy się do źródła danych tylko raz (lub cała transakcja została wycofana, ponownie, aby źródła danych ulega) — Jeśli źródło danych obsługuje wymaganego poziomu transakcji.  
  
- Bezpośrednie wykonywanie [SQL](../../data/odbc/sql.md) instrukcji.  
  
Po zakończeniu pracy z połączenia źródła danych, Zamknij `CDatabase` obiektu, a następnie go zniszcz lub użyć go ponownie do nowego połączenia. Aby uzyskać więcej informacji na temat połączeń ze źródłami danych, zobacz [źródła danych (ODBC)](../../data/odbc/data-source-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  

[ODBC i MFC](../../data/odbc/odbc-and-mfc.md)