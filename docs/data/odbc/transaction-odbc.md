---
title: Transakcja (ODBC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f142b4602ad1a9605987bc71e477e977902dccac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090272"
---
# <a name="transaction-odbc"></a>Transakcja (ODBC)

Ten temat dotyczy klas MFC ODBC.  
  
Transakcja jest sposobem grupy lub usługi batch, serię aktualizacji [źródła danych](../../data/odbc/data-source-odbc.md) tak, aby wszystkie dokłada wszelkich starań, jednocześnie lub żaden nie jest zatwierdzona w przypadku wycofania transakcji. Jeśli nie używasz transakcji, do źródła danych jest oznaczany automatycznie zamiast Zatwierdzanie na żądanie.  
  
> [!NOTE]
>  Nie wszystkie sterowników ODBC obsługuje transakcji. Wywołaj `CanTransact` funkcji składowej typu usługi [CDatabase](../../mfc/reference/cdatabase-class.md) lub [CRecordset](../../mfc/reference/crecordset-class.md) obiekt, aby sprawdzić, czy sterownik obsługuje transakcji określonej bazy danych. Należy pamiętać, że `CanTransact` nie poinformować Cię, czy źródło danych obsługuje pełne transakcji. Musisz również wywołać `CDatabase::GetCursorCommitBehavior` i `CDatabase::GetCursorRollbackBehavior` po `CommitTrans` i `Rollback` Aby sprawdzić efekt skonfigurowania transakcji, otwórz `CRecordset` obiektu.  
  
Wywołania `AddNew` i `Edit` funkcje elementów członkowskich `CRecordset` obiektu źródła danych natychmiast, gdy zostanie wywołana mogą wpłynąć na `Update`. `Delete` wywołuje również obowiązywać natychmiast. Z kolei można użyć transakcji składające się z wielu wywołań `AddNew`, `Edit`, `Update`, i `Delete`, które są wykonywane, ale nie wykonywane, dopóki nie wywołasz `CommitTrans` jawnie. Ustanawiając transakcji, można wykonać szereg takich połączeń, przy zachowaniu możliwości można je wycofać. Jeśli krytycznym zasobem jest niedostępny lub niektórych innych uniemożliwia cała transakcja ukończenie, można wycofać transakcji, zamiast go zatwierdzania. W takiej sytuacji żadne zmiany należących do transakcji wpływa na źródło danych.  
  
> [!NOTE]
>  Obecnie klasy `CRecordset` nie obsługuje aktualizacji do źródła danych, jeśli udało Ci się wdrożyć zbiorcze pobieranie z wiersza. Oznacza to, nie może wykonywać wywołania `AddNew`, `Edit`, `Delete`, lub `Update`. Jednakże można napisać możesz własne funkcje do wykonywania aktualizacji, a następnie wywołać te funkcje w ramach danej transakcji. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Oprócz wpływających na rekordów, transakcje wpływają na instrukcje SQL, które można wykonać bezpośrednio, tak długo, jak używać ODBC **HDBC** skojarzone z Twojej `CDatabase` obiektu lub ODBC **HSTMT** na podstawie które **HDBC**.  
  
Transakcje są szczególnie przydatne, jeśli masz wiele rekordów, które muszą być aktualizowane jednocześnie. W tym przypadku chcesz uniknąć transakcji połowie zakończony, takich jak może się zdarzyć, jeśli wystąpił wyjątek przed dokonaniem ostatniej aktualizacji. Grupowanie tych aktualizacji w transakcji umożliwia odzyskanie danych będzie (Wycofaj) zmiany i zwraca rekordy pretransaction stanu. Na przykład jeśli bank przeniesienia pieniądze z konta, A Konto B, zarówno wycofania z depozytu i b musi zakończyć się poprawnie przetworzyć środków lub cała transakcja muszą zakończyć się niepowodzeniem.  
  
W klasach bazy danych, wykonywania transakcji za pośrednictwem `CDatabase` obiektów. A `CDatabase` obiekt reprezentuje połączenie ze źródłem danych i jeden lub więcej zestawów rekordów skojarzonych z tym `CDatabase` obiektu działają w tabelach bazy danych za pomocą funkcji elementów członkowskich zestawu rekordów.  
  
> [!NOTE]
>  Obsługiwane jest tylko jeden poziom transakcji. Nie można zagnieździć transakcji ani transakcji mogą znajdować się na wielu obiektów bazy danych.  
  
Więcej informacji na temat sposobu transakcje są wykonywane można znaleźć w następujących tematach:  
  
- [Transakcja: wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
- [Transakcja: jak transakcje wpływają na aktualizacje (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## <a name="see-also"></a>Zobacz też  

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)