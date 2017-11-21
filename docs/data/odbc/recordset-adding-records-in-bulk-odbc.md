---
title: "Zestaw rekordów: Dodawanie rekordów (ODBC) zbiorczo | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 937e5273a0b999672dbbc98a927d34909d04136b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Zestaw rekordów: zbiorcze dodawanie rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 MFC [crecordset —](../../mfc/reference/crecordset-class.md) klasa ma nowy optymalizacji, która zwiększa wydajność podczas dodawania nowych rekordów zbiorczo do tabeli.  
  
> [!NOTE]
>  Ten temat dotyczy obiektów pochodzących od `CRecordset` w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli korzystasz z zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Nową opcję **dwOptions** parametr [CRecordset::Open](../../mfc/reference/crecordset-class.md#open) funkcji członkowskiej **optimizeBulkAdd**, zwiększa wydajność podczas dodawania wielu rekordów po kolei bez wywoływania elementu **Requery** lub **Zamknij**. Tylko pola, które zostały zmienione przed pierwszym **aktualizacji** wywołania oznaczonych jako zakłócone dla kolejnych `AddNew` / **aktualizacji** wywołania.  
  
 Jeśli używasz klasy baz danych, aby móc korzystać z **:: SQLSetPos** interfejsu API ODBC funkcji dodawania, edytowania i usuwania rekordów, ten rodzaj optymalizacji jest niepotrzebna.  
  
 Jeśli z biblioteki kursorów ODBC został załadowany lub sterownik ODBC nie obsługuje dodawania, edytowania i usuwania za pośrednictwem **:: SQLSetPos**, tego rodzaju optymalizacji należy poprawić zbiorcze Dodawanie wydajności. Aby włączyć tego rodzaju optymalizacji, ustaw **dwOptions** parametru w **Otwórz** wywołania dla zestawu rekordów do następującego:  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Zestaw rekordów: Dodawanie, aktualizowanie i usuwanie rekordów (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Zestaw rekordów: Blokowanie rekordów (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)