---
title: "Obsługa transakcji w OLE DB | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9be6fb1c86b43f7833818648d84875b1e4c55b59
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-transactions-in-ole-db"></a>Obsługa transakcji w OLE DB
A [transakcji](../../data/transactions-mfc-data-access.md) sposób grupowania lub partii szereg aktualizacji ze źródłem danych, aby albo wszystkie powiedzie się i są zatwierdzone jednocześnie (jeśli jeden z nich kończy się niepowodzeniem) żaden nie jest zatwierdzona i cała transakcja zostanie wycofana. Ten proces zapewnia integralność wyniku w źródle danych.  
  
 OLE DB obsługuje transakcje z trzech poniższych metod:  
  
-   [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)  
  
-   [Metody ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx)  
  
-   [ITransaction::Abort](https://msdn.microsoft.com/en-us/library/ms709833.aspx)  
  
## <a name="relationship-of-sessions-and-transactions"></a>Relacja sesji i transakcji  
 Obiekt źródła danych można tworzyć obiektów sesji, z których każdy może być wewnątrz lub na zewnątrz zakresu transakcji w danym momencie.  
  
 Podczas sesji nie wprowadził transakcji, pracy wszystkie w ramach tej sesji w magazynie danych jest natychmiast zostało zatwierdzone na poziomie każdego wywołania metody. (Jest to czasami określane jako trybie autozatwierdzania lub niejawnych.)  
  
 Podczas sesji wprowadzania transakcji, pracy wszystkie w ramach tej sesji w magazynie danych jest częścią tej transakcji i jest zatwierdzona lub przerwana jako pojedyncza jednostka. (Jest to czasami określane jako tryb ręcznego zatwierdzania.)  
  
 Obsługa transakcji jest specyficznych dla dostawcy. Jeśli używasz dostawca obsługuje transakcje, obiekt sesji, który obsługuje **ITransaction** i **ITransactionLocal** można wprowadzać proste (to znaczy-nested) transakcji. Klasy szablonów OLE DB [CSession](../../data/oledb/csession-class.md) obsługuje tych interfejsów i jest zalecanym sposobem wykonania Obsługa transakcji w programie Visual C++.  
  
## <a name="starting-and-ending-the-transaction"></a>Początkowa i końcowa transakcji  
 Należy wywołać `StartTransaction`, **zatwierdzić**, i **przerwać** metodach obiektu zestawu wierszy w konsumenta.  
  
 Wywoływanie **ITransactionLocal::StartTransaction** uruchamia nowej transakcji lokalnej. Po uruchomieniu transakcji upoważnieni przez kolejnych operacji zmiany nie są faktycznie stosowane do magazynu danych do momentu zatwierdzić transakcji.  
  
 Wywoływanie **metody ITransaction::Commit** lub **ITransaction::Abort** kończy się transakcji. **Zatwierdź** powoduje, że wszystkie zmiany w zakresie transakcji, które ma zostać zastosowany do magazynu danych. **Przerwij** powoduje, że wszystkie zmiany w zakresie transakcji do anulowania i magazynu danych jest w stanie, że pozostała miał przed rozpoczęciem transakcji.  
  
## <a name="nested-transactions"></a>Transakcje zagnieżdżone  
 A [zagnieżdżonych transakcji](https://msdn.microsoft.com/en-us/library/ms716985.aspx) występuje, gdy rozpocząć nowej transakcji lokalnej, gdy istnieje już aktywna transakcja w tej sesji. Nowa transakcja jest uruchomiona jako zagnieżdżoną poniżej bieżącej transakcji. Jeśli dostawca nie obsługuje transakcji zagnieżdżonych, wywoływania `StartTransaction` gdy istnieje już aktywna transakcja w sesji zwraca **XACT_E_XTIONEXISTS**.  
  
## <a name="distributed-transactions"></a>Transakcje rozproszone  
 Transakcja rozproszona jest transakcji, która aktualizuje dane rozproszonej; oznacza to, że dane na więcej niż jednego systemu komputera sieciowego. Jeśli chcesz obsługuje transakcje za pośrednictwem Rozproszony system należy użyć zamiast Obsługa transakcji w OLE DB programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)