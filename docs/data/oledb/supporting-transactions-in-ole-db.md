---
title: Obsługa transakcji w OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 658313ddaf29e67c7be5c83dbc38c3b5da95eba9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055388"
---
# <a name="supporting-transactions-in-ole-db"></a>Obsługa transakcji w OLE DB

A [transakcji](../../data/transactions-mfc-data-access.md) to sposób grupowania lub usługi batch, serię aktualizacji ze źródłem danych, aby wszystkie powiedzie się i dokłada wszelkich starań, jednocześnie lub (jeśli jeden z nich ulegnie awarii) żaden nie jest zatwierdzona i cała transakcja zostanie wycofana. Ten proces zapewnia integralność wynik w źródle danych.

OLE DB obsługuje transakcji z trzech poniższych metod:

- [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786)

- [Metody ITransaction::Commit](/previous-versions/windows/desktop/ms713008)

- [ITransaction::Abort](/previous-versions/windows/desktop/ms709833)

## <a name="relationship-of-sessions-and-transactions"></a>Relacja między sesjami i transakcji

Obiekt źródłowy danych jednego można tworzyć obiektów sesji, z których każdy może być wewnątrz lub na zewnątrz zakresu transakcji w danym momencie.

Podczas sesji nie można przejść do transakcji, całej pracy wykonywanej w ramach tej sesji na magazyn danych jest natychmiast przydzielonej przy każdym wywołaniu metody. (To jest czasami określane jako trybie autozatwierdzania lub niejawnych.)

Gdy sesja wprowadza transakcji, całej pracy wykonywanej w ramach tej sesji na magazyn danych jest częścią tej transakcji i jest zatwierdzeniu lub przerwaniu jako pojedyncza jednostka. (To jest czasami określane jako tryb ręcznego zatwierdzania.)

Obsługa transakcji jest specyficzny dla dostawcy. Jeśli dostawca używasz obsługuje transakcje, obiekt sesji, który obsługuje `ITransaction` i `ITransactionLocal` można wprowadzić transakcji (niezagnieżdżonego). Klasy szablonów OLE DB [CSession](../../data/oledb/csession-class.md) obsługuje tych interfejsów i jest zalecany sposób wdrożenia Obsługa transakcji w programie Visual C++.

## <a name="starting-and-ending-the-transaction"></a>Początkowe i końcowe transakcji

Należy wywołać `StartTransaction`, `Commit`, i `Abort` metody obiektu zestawu wierszy u odbiorcy.

Wywoływanie `ITransactionLocal::StartTransaction` rozpoczyna się nowej transakcji lokalnej. Po rozpoczęciu transakcji wszelkie zmiany wymagane na podstawie stosownych późniejszych operacji nie są stosowane do magazynu danych, dopóki nie można zatwierdzić transakcji.

Wywoływanie `ITransaction::Commit` lub `ITransaction::Abort` kończy się transakcji. `Commit` powoduje, że wszystkie zmiany w zakresie transakcji, które mają być stosowane do magazynu danych. `Abort` powoduje, że wszystkie zmiany w zakresie transakcji zostaną anulowane i magazynem danych pozostanie w stanie go miał przed rozpoczęciem transakcji.

## <a name="nested-transactions"></a>Transakcje zagnieżdżone

A [zagnieżdżonych transakcji](/previous-versions/windows/desktop/ms716985) po uruchomieniu nowej transakcji lokalnej, gdy w sesji istnieje już aktywna transakcja. Nowa transakcja jest uruchomiony jako transakcji zagnieżdżonej poniżej bieżącej transakcji. Jeśli dostawca nie obsługuje transakcji zagnieżdżonych, wywołanie `StartTransaction` gdy istnieje już aktywna transakcja sesji zwraca XACT_E_XTIONEXISTS.

## <a name="distributed-transactions"></a>Transakcje rozproszone

Transakcja rozproszona jest transakcji, która aktualizuje rozproszonych danych; oznacza to, że dane na więcej niż jednym komputerze sieciowym. Jeśli chcesz obsługiwać transakcji za pośrednictwem systemu rozproszonego, należy użyć programu .NET Framework, a nie Obsługa transakcji w OLE DB.

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)