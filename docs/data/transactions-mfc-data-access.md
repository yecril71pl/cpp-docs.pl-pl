---
title: Transakcje (dostęp do danych MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions [C++], support for
- transactions [C++]
- databases [C++], transactions
ms.assetid: f80afbfe-1517-4fec-8870-9ffc70a58b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9dd531aee6ac8014f2ce47ddee7fc5f82e35a63
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33107821"
---
# <a name="transactions--mfc-data-access"></a>Transakcje (dostęp do danych MFC)
Pojęcie transakcji został opracowany do obsługi przypadków, w których Wynikowy stan bazy danych zależy od całkowitej Powodzenie czynności. Może to występować ponieważ kolejne czynności może zmodyfikować wyniki poprzednich operacji. W takich przypadkach Jeśli wszystkie jedna operacja nie powiedzie się, Wynikowy stan może być nieokreślony.  
  
 Aby rozwiązać ten problem, transakcje grupy serii operacji w taki sposób, aby integralność wynik końcowy można mieć pewność. Wszystkie operacje musi się powieść, a następnie można zatwierdzić (zapisane w bazie danych) albo cała transakcja nie powiedzie się. Anulowanie transakcji jest nazywany wycofywania. Wycofanie umożliwia odzyskanie zmiany i przywraca bazę danych do stanu pretransaction.  
  
 Na przykład w transakcji automatycznych bankowości oszczędność pieniędzy w przypadku transferu z konta, A Konto B, zarówno wycofania z złożenia i b musi się zakończyć powodzeniem poprawnie przetworzyć funduszy lub cała transakcja musi zakończyć się niepowodzeniem.  
  
 Transakcja musi mieć ACID właściwości, które na następujących czynności:  
  
-   **Niepodzielność** transakcji jest Atomowej jednostki pracy, a dokładnie raz wykonuje; wszystkie praca jest wykonywana lub żadne z nich.  
  
-   **Spójność** transakcji umożliwia zachowanie spójności danych przekształcania jeden stan spójności danych w inny stan spójności danych. Dane związane z transakcją muszą zostać zachowane semantycznie.  
  
-   **Izolacja** transakcji jest jednostką izolacji i każdego wystąpienia oddzielnie i niezależnie od równoczesnych transakcji. Transakcji nigdy nie powinna być widoczna pośrednich etapach innej transakcji.  
  
-   **Trwałość** transakcji jest jednostką odzyskiwania. Jeśli transakcja się powiedzie, jego aktualizacje będą się powtarzać, nawet wtedy, gdy system ulegnie awarii lub zostanie zamknięty. Jeśli transakcja się nie powiedzie, system pozostaje w stanie przed zatwierdzeniem transakcji.  
  
 Może obsługiwać transakcji w OLE DB (zobacz [Obsługa transakcji w OLE DB](../data/oledb/supporting-transactions-in-ole-db.md)) lub ODBC (zobacz [transakcja (ODBC)](../data/odbc/transaction-odbc.md)).  
  
 Transakcja rozproszona jest transakcji, która aktualizuje dane rozproszonych, oznacza to, że dane na więcej niż jednego systemu komputera sieciowego. Jeśli chcesz obsługuje transakcje za pośrednictwem Rozproszony system należy używać ADO.NET zamiast Obsługa transakcji w OLE DB.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do danych programowania (MFC/ATL)](../data/data-access-programming-mfc-atl.md)