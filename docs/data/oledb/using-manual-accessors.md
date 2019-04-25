---
title: Korzystanie z ręcznych metod dostępu
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: 4a7e2dcde20cdb06a2f4e708149e24ee7144597c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311998"
---
# <a name="using-manual-accessors"></a>Korzystanie z ręcznych metod dostępu

Istnieją cztery czynności wykonywane podczas obsługi nieznane polecenie:

- Określanie parametrów

- Wykonaj polecenie

- Określić kolumny wyjściowe

- Czy istnieją wielu zwracane zestawy wierszy

W celu obeznani z szablonami konsumentów DB OLE `CManualAccessor` klasy i wykonaj następujące czynności:

1. Otwórz `CCommand` obiekt z `CManualAccessor` jako parametr szablonu.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Kwerendy sesji dla `IDBSchemaRowset` interfejs i użyć zestawu wierszy parametrów procedury. Jeśli `IDBSchemaRowset` interfejsu nie jest dostępny, wykonanie kwerendy `ICommandWithParameters` interfejsu. Wywołaj `GetParameterInfo` informacji. Jeśli żadna interfejs jest dostępny, można założyć, że nie ma żadnych parametrów.

1. Dla każdego parametru wywołania `AddParameterEntry` Dodaj parametry i ich ustawiania.

1. Otwórz zestaw wierszy, ale wartość parametru powiązania **false**.

1. Wywołaj `GetColumnInfo` można pobrać kolumn wyjściowych. Użyj `AddBindEntry` można dodać kolumnę wyjściową do powiązania.

1. Wywołaj `GetNextResult` do określenia, czy więcej zestawów wierszy są dostępne. Powtórz kroki od 2 do 5.

Na przykład ręczne metody dostępu Zobacz `CDBListView::CallProcedure` w [DBVIEWER](https://github.com/Microsoft/VCSamples) próbki.

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)