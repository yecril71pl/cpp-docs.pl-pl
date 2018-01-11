---
title: Transakcja (ODBC) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2816e1cfe3c62fecede5c909bc1593779aa90d54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-odbc"></a>Transakcja (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 Transakcja jest sposób grupę lub partii szereg aktualizacje [źródła danych](../../data/odbc/data-source-odbc.md) tak, aby wszystkie są zatwierdzone na raz lub żaden nie jest zatwierdzona Jeśli Wycofaj tę transakcję. Jeśli nie używasz transakcji, ze źródłem danych jest oznaczany automatycznie zamiast trwa deklarowanej na żądanie.  
  
> [!NOTE]
>  Nie wszystkie sterowników ODBC obsługuje transakcji. Wywołanie `CanTransact` funkcji członkowskiej klasy z [cdatabase —](../../mfc/reference/cdatabase-class.md) lub [crecordset —](../../mfc/reference/crecordset-class.md) obiektem, aby określić, czy sterownik obsługuje transakcji określonej bazy danych. Należy pamiętać, że `CanTransact` właściwość nie określa, czy źródło danych umożliwia obsługę pełne transakcji. Musisz również wywołać `CDatabase::GetCursorCommitBehavior` i `CDatabase::GetCursorRollbackBehavior` po **CommitTrans** i **wycofywania** Aby sprawdzić efekt transakcji na otwieranie `CRecordset` obiektu.  
  
 Wywołań `AddNew` i **Edytuj** funkcji Członkowskich `CRecordset` obiekt źródła danych, natychmiast po wywołaniu wpływają na **aktualizacji**. **Usuń** wywołania również zaczynają obowiązywać natychmiast. Z kolei, można użyć transakcji składające się z wielu wywołań `AddNew`, **Edytuj**, **aktualizacji**, i **usunąć**, które są wykonywane, ale nie zostały przekazane do należy wywołać **CommitTrans** jawnie. Ustanawiając transakcji, możesz wykonać szereg takie połączenia przy zachowaniu możliwości je wycofać. Jeśli krytyczne zasób jest niedostępny lub innej sytuacji uniemożliwia ukończenie cała transakcja, możesz można wycofać transakcji zamiast zatwierdzania go. W takim przypadku należących do transakcji zmiany wpływają na źródła danych.  
  
> [!NOTE]
>  Obecnie klasy `CRecordset` nie obsługuje aktualizacji do źródła danych, jeśli zostały zaimplementowane zbiorcze pobieranie z wiersza. Oznacza to, nie można wprowadzić wywołań `AddNew`, **Edytuj**, **usunąć**, lub **aktualizacji**. Jednak można napisać możesz własnych funkcji w celu przeprowadzania aktualizacji, a następnie wywołać tych funkcji w ramach danej transakcji. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Oprócz wpływających na zestawu rekordów, transakcje wpływają na instrukcji SQL, które można wykonywać bezpośrednio tak długo, jak używać ODBC **HDBC** skojarzone z Twojej `CDatabase` obiektu lub ODBC **HSTMT** na podstawie który **HDBC**.  
  
 Transakcje są szczególnie przydatne, jeśli masz wiele rekordów, które muszą zostać zaktualizowane jednocześnie. W takim przypadku chce się uniknąć ukończone połowie transakcji, takich jak może się zdarzyć, gdy wyjątek został zgłoszony przed ostatniej aktualizacji. Grupowanie takie aktualizacje w transakcji umożliwia odzyskiwania (wycofywania) z zmiany i zwraca rekordy pretransaction stan. Na przykład jeśli bank przenosi pieniędzy z konta, A Konto B, zarówno wycofania z złożenia i b musi się zakończyć powodzeniem poprawnie przetworzyć funduszy lub cała transakcja musi zakończyć się niepowodzeniem.  
  
 W klasach bazy danych, wykonywać transakcje za pośrednictwem `CDatabase` obiektów. A `CDatabase` obiekt reprezentuje połączenie ze źródłem danych i jeden lub więcej zestawów rekordów skojarzone z tym `CDatabase` obiektu działają w tabelach bazy danych za pośrednictwem funkcji elementów członkowskich zestawu rekordów.  
  
> [!NOTE]
>  Obsługiwane jest tylko jeden poziom transakcji. Nie można zagnieździć transakcji nie może obejmować transakcji wielu obiektów bazy danych.  
  
 Więcej informacji na temat realizację transakcji można znaleźć w następujących tematach:  
  
-   [Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
-   [Transakcja: jak transakcje wpływają na aktualizacje (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)