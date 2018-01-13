---
title: "Transakcja: Jak transakcje wpływają na aktualizacje (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59eb8aecbf2dd2138c8a0469d71364b55fd82774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transakcja: jak transakcje wpływają na aktualizacje (ODBC)
Aktualizacje [źródła danych](../../data/odbc/data-source-odbc.md) są zarządzane podczas transakcji przy użyciu buforu edycji (tej samej metody poza transakcji). Elementy członkowskie danych pola rekordów zbiorczo służyć jako edycji buforu, który zawiera rekord bieżący zestaw rekordów kopię zapasową tymczasowego podczas `AddNew` lub **Edytuj**. Podczas **usunąć** operacji, bieżący rekord nie kopii zapasowej w obrębie transakcji. Aby uzyskać więcej informacji na temat buforu edycji i jak przechowywać bieżącego rekordu w aktualizacji, zobacz [zestaw rekordów: jak zestawy rekordów aktualizacji rekordów (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
> [!NOTE]
>  Jeśli zaimplementowano zbiorcze pobieranie z wiersza, nie można wywołać `AddNew`, **Edytuj**, lub **usunąć**. Zamiast tego należy napisać funkcji przeprowadzania aktualizacji do źródła danych. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Podczas transakcji `AddNew`, **Edytuj**, i **usunąć** operacje można zatwierdzona lub wycofana. Efekty **CommitTrans** i **wycofywania** może spowodować bieżącego rekordu nie można przywrócić w buforze edycji. Aby upewnić się, że bieżącego rekordu zostaną prawidłowo przywrócone, ważne jest, aby zrozumieć, jak **CommitTrans** i **wycofywania** funkcji Członkowskich `CDatabase` korzystanie z funkcji aktualizacji `CRecordset`.  
  
##  <a name="_core_how_committrans_affects_updates"></a>Wpływ CommitTrans aktualizacji  
 W poniższej tabeli opisano skutków **CommitTrans** transakcji.  
  
### <a name="how-committrans-affects-updates"></a>Wpływ CommitTrans aktualizacji  
  
|Operacja|Stan źródła danych|  
|---------------|---------------------------|  
|`AddNew`i **aktualizacji**, a następnie **CommitTrans**|Nowy rekord są dodawane do źródła danych.|  
|`AddNew`(bez **aktualizacji**), a następnie **CommitTrans**|Nowy rekord zostaną utracone. Rekord nie został dodany do źródła danych.|  
|**Edytuj** i **aktualizacji**, a następnie **CommitTrans**|Edycja przekazane do źródła danych.|  
|**Edytuj** (bez **aktualizacji**), a następnie **CommitTrans**|Zmiany w rekordzie zostaną utracone. Rekord pozostaje bez zmian w źródle danych.|  
|**Usuń** następnie **CommitTrans**|Rekordy zostały usunięte ze źródła danych.|  
  
##  <a name="_core_how_rollback_affects_updates"></a>Wpływ wycofywania transakcji  
 W poniższej tabeli opisano skutków **wycofywania** transakcji.  
  
### <a name="how-rollback-affects-transactions"></a>Wpływ wycofywania transakcji  
  
|Operacja|Stan bieżącego rekordu|Należy również|Stan źródła danych|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew`i **aktualizacji**, następnie **wycofywania**|Zawartość bieżącego rekordu są tymczasowo przechowywane w celu zwolnienia miejsca dla nowego rekordu. Nowy rekord jest wprowadzany do edycji buforu. Po **aktualizacji** jest nazywany bieżącego rekordu jest przywracany do buforu edycji.||Dodawanie do źródła danych wprowadzonych przez **aktualizacji** została wycofana.|  
|`AddNew`(bez **aktualizacji**), następnie **wycofywania**|Zawartość bieżącego rekordu są tymczasowo przechowywane w celu zwolnienia miejsca dla nowego rekordu. Edytuj bufor zawiera nowy rekord.|Wywołanie `AddNew` ponownie, aby przywrócić buforu edycji pusta, nowy rekord. Lub zadzwoń **Przenieś**(0), aby przywrócić starych wartości w buforze edycji.|Ponieważ **aktualizacji** nie została wywołana, nie wprowadzono żadnych zmian wprowadzonych w źródle danych.|  
|**Edytuj** i **aktualizacji**, następnie **wycofywania**|Nie do edycji wersję bieżącego rekordu są tymczasowo przechowywane. Zmiany zostały wprowadzone do zawartości buforu edycji. Po **aktualizacji** jest wywoływana, nie do edycji wersji rekordu jest wciąż tymczasowo przechowywane.|*Zestaw dynamiczny*: przewiń poza bieżącego rekordu, a następnie do przywracania nie do edycji wersji rekordu w buforze edycji.<br /><br /> *Migawki*: wywołanie **Requery** do odświeżenia zestawu rekordów ze źródła danych.|Zmiany wprowadzone przez źródło danych **aktualizacji** zostały zamienione.|  
|**Edytuj** (bez **aktualizacji**), następnie **wycofywania**|Nie do edycji wersję bieżącego rekordu są tymczasowo przechowywane. Zmiany zostały wprowadzone do zawartości buforu edycji.|Wywołanie **Edytuj** ponownie, aby przywrócić nie do edycji wersji rekordu w buforze edycji.|Ponieważ **aktualizacji** nie została wywołana, nie wprowadzono żadnych zmian wprowadzonych w źródle danych.|  
|**Usuń** następnie **wycofywania**|Zawartość bieżącego rekordu zostanie usunięta.|Wywołanie **Requery** do przywrócenia zawartości bieżącego rekordu ze źródła danych.|Usuwanie danych z źródła danych został wycofany.|  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transakcja (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transakcja: Wykonywanie transakcji w zestawie rekordów (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [Cdatabase — klasa](../../mfc/reference/cdatabase-class.md)   
 [Klasa CRecordset](../../mfc/reference/crecordset-class.md)