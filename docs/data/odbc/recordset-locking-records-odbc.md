---
title: "Zestaw rekordów: Blokowanie rekordów (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3c9e8336e0ef26c1547d5bc495dfbb3e89e7ee91
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-locking-records-odbc"></a>Zestaw rekordów: blokowanie rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 W tym temacie opisano:  
  
-   [Rodzaje dostępne blokowanie rekordów](#_core_record.2d.locking_modes).  
  
-   [Jak zablokować rekordów w twoim zestawie rekordów podczas aktualizacji](#_core_locking_records_in_your_recordset).  
  
 Gdy używasz zestawu rekordów próbę zaktualizowania rekordu w źródle danych aplikacji można zablokować rekordu, więc żaden inny użytkownik może zaktualizować rekord w tym samym czasie. Stan rekordu, który został zaktualizowany przez dwóch użytkowników jednocześnie jest niezdefiniowana, chyba że system może zagwarantować, że dwóch użytkowników nie można zaktualizować rekord jednocześnie.  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, niektóre informacje nie ma zastosowania. Na przykład nie można wywołać **Edytuj** i **aktualizacji** funkcji elementów członkowskich. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_record.2d.locking_modes"></a>Tryby blokowanie rekordów  
 Klasy baz danych Podaj dwie [tryby blokowanie rekordów](../../mfc/reference/crecordset-class.md#setlockingmode):  
  
-   Optymistyczne blokowanie (ustawienie domyślne)  
  
-   Pesymistyczne blokowanie  
  
 Aktualizowania rekordu przebiega w trzech etapach:  
  
1.  Rozpocznij operację przez wywołanie metody [Edytuj](../../mfc/reference/crecordset-class.md#edit) funkcji członkowskiej.  
  
2.  Możesz zmienić odpowiednich pól bieżącego rekordu.  
  
3.  Zakończyć operację — i zwykle zatwierdzić aktualizację — wywołując [aktualizacji](../../mfc/reference/crecordset-class.md#update) funkcji członkowskiej.  
  
 Optymistyczne blokowanie blokuje rekord w źródle danych tylko podczas **aktualizacji** wywołania. Jeśli używasz optymistyczne blokowanie w środowisku wielodostępnym, aplikacja powinna obsługiwać **aktualizacji** stanu błędu. Pesymistyczne blokowanie blokuje rekord, jak należy wywołać **Edytuj** i nie zwalnia jego dopóki wywołania **aktualizacji** (błędy są oznaczone za pomocą `CDBException` mechanizmu, a nie przez wartość **FALSE** zwrócony przez **aktualizacji**). Pesymistyczne blokowanie ma potencjalne zmniejszenie wydajności dla innych użytkowników, ponieważ równoczesny dostęp do tego samego rekordu może być konieczne poczekanie, aż do zakończenia aplikacji **aktualizacji** procesu.  
  
##  <a name="_core_locking_records_in_your_recordset"></a>Blokowanie rekordów zestawu rekordów  
 Jeśli chcesz zmienić obiekt zestawu rekordów [tryb blokowania](#_core_record.2d.locking_modes) od domyślnej, należy zmienić tryb przed wywołaniem **Edytuj**.  
  
#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Aby zmienić bieżący tryb blokowania dla zestawu rekordów  
  
1.  Wywołanie [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) funkcji członkowskiej, określając albo **CRecordset::pessimistic** lub **CRecordset::optimistic**.  
  
 Nowy tryb blokowania pozostaje, dopóki ponownie zmienić lub zestawu rekordów jest zamknięty.  
  
> [!NOTE]
>  ODBC — sterowniki względnie mało obsługuje obecnie pesymistyczne blokowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Wykonywanie sprzężenia (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)   
 [Zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)