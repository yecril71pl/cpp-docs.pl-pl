---
title: Korzystanie z ręcznych metod dostępu
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: b76c6a2d0af404bc526fee8f511320a58ffd86ec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218289"
---
# <a name="using-manual-accessors"></a>Korzystanie z ręcznych metod dostępu

Podczas obsługi nieznanego polecenia należy wykonać cztery czynności:

- Określanie parametrów

- Wykonaj polecenie

- Określanie kolumn wyjściowych

- Sprawdź, czy istnieje wiele zestawów wierszy powrotu

Aby wykonać te czynności za pomocą OLE DB szablonów konsumentów, użyj `CManualAccessor` klasy i wykonaj następujące kroki:

1. Otwórz `CCommand` obiekt za pomocą `CManualAccessor` jako parametru szablonu.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Wykonaj zapytanie dotyczące sesji dla `IDBSchemaRowset` interfejsu i użyj zestawu wierszy parametrów procedury. Jeśli `IDBSchemaRowset` interfejs nie jest dostępny, należy wykonać zapytanie dotyczące `ICommandWithParameters` interfejsu. Wywołaj, `GetParameterInfo` Aby uzyskać informacje. Jeśli żaden interfejs nie jest dostępny, można założyć, że nie ma żadnych parametrów.

1. Dla każdego parametru Wywołaj polecenie, `AddParameterEntry` Aby dodać parametry i ustawić je.

1. Otwórz zestaw wierszy, ale ustaw parametr bind na **`false`** .

1. Wywołaj `GetColumnInfo` , aby pobrać kolumny wyjściowe. Służy `AddBindEntry` do dodawania kolumny danych wyjściowych do powiązania.

1. Wywołaj `GetNextResult` , aby określić, czy są dostępne więcej zestawów wierszy. Powtórz kroki od 2 do 5.

Przykład ręcznej metody dostępu można znaleźć `CDBListView::CallProcedure` w sekcji w przykładzie [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .

## <a name="see-also"></a>Zobacz także

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
