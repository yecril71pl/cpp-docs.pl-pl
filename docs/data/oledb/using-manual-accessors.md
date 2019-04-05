---
title: Korzystanie z ręcznych metod dostępu
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: 4a7e2dcde20cdb06a2f4e708149e24ee7144597c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028338"
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