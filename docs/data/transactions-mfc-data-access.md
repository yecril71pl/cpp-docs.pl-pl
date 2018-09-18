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
ms.openlocfilehash: 332568d0a4a275247c95fc6b5ecfbbfcb8712acc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052215"
---
# <a name="transactions--mfc-data-access"></a>Transakcje (dostęp do danych MFC)

Pojęcie transakcji został opracowany, aby obsługiwać przypadki, w których Wynikowy stan bazy danych zależy od łączna liczba sukcesów szereg operacji. To może pochodzić, ponieważ kolejne czynności można modyfikować wyników poprzedniej operacji. W takich przypadkach Jeśli wszystkie jedna operacja zakończy się niepowodzeniem, Wynikowy stan może być nieokreślone.  
  
Aby rozwiązać ten problem, transakcje grupy serii operacji w taki sposób, który można czuwać integralności wynik końcowy. Wszystkie operacje musi powiedzie się, a następnie można zatwierdzić (zapisane w bazie danych) albo cała transakcja nie powiedzie się. Anulowanie transakcji jest nazywany wycofywania. Wycofywanie umożliwia odzyskanie danych z zmiany i zwraca bazy danych do pretransaction stanu.  
  
Na przykład w transakcji bankowych automatycznych, jeżeli przeniesiesz pieniądze z konta, A Konto B, zarówno wycofania z depozytu i b musi zakończyć się poprawnie przetworzyć środków lub cała transakcja muszą zakończyć się niepowodzeniem.  
  
Transakcji musi mieć właściwości ACID, które utrudniają do wykonania poniższych czynności:  
  
- **Niepodzielność** transakcji jest pojedynczej Atomowej jednostki pracy i jest wykonywana tylko raz; wszystkie prace wykonywane lub żaden z jej.  
  
- **Spójność** transakcji zachowuje spójności danych, przekształcanie jednego spójnego stanu danych na inny stan spójności danych. Muszą być semantycznie zachowane dane powiązane przez transakcję.  
  
- **Izolacja** transakcji jest jednostką izolacji i każdego wystąpienia oddzielnie i niezależnie od jednoczesnych transakcji. Transakcji nigdy nie powinna zostać wyświetlona pośrednich etapach inną transakcję.  
  
- **Trwałość** transakcji jest jednostką odzyskiwania. Jeśli transakcja zakończy się powodzeniem, jego aktualizacje będą się powtarzać, nawet jeśli systemu ulegnie awarii lub zostanie zamknięty. Jeśli transakcja zakończy się niepowodzeniem, system pozostaje w stanie wstecz Zatwierdzanie transakcji.  
  
Może obsługiwać transakcji w OLE DB (zobacz [Obsługa transakcji w OLE DB](../data/oledb/supporting-transactions-in-ole-db.md)) lub ODBC (zobacz [transakcja (ODBC)](../data/odbc/transaction-odbc.md)).  
  
Transakcja rozproszona jest transakcji, która aktualizuje rozproszonej dane, oznacza to, że dane na więcej niż jednym komputerze sieciowym. Jeśli chcesz obsługiwać transakcji za pośrednictwem systemu rozproszonego, należy użyć programu ADO.NET, a nie Obsługa transakcji w OLE DB.  
  
## <a name="see-also"></a>Zobacz też  

[Programowanie (MFC/ATL) dostępu do danych](../data/data-access-programming-mfc-atl.md)