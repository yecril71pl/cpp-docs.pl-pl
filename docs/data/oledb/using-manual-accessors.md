---
title: Korzystanie z ręcznych metod dostępu
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: a6c0e5236702229a61a828344ba5d0d288898aee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209329"
---
# <a name="using-manual-accessors"></a>Korzystanie z ręcznych metod dostępu

Podczas obsługi nieznanego polecenia należy wykonać cztery czynności:

- Określanie parametrów

- Wykonaj polecenie

- Określanie kolumn wyjściowych

- Sprawdź, czy istnieje wiele zestawów wierszy powrotu

Aby wykonać te czynności za pomocą OLE DB szablonów konsumentów, użyj klasy `CManualAccessor` i wykonaj następujące czynności:

1. Otwórz obiekt `CCommand` z `CManualAccessor` jako parametr szablonu.

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. Wykonaj zapytanie dotyczące sesji dla interfejsu `IDBSchemaRowset` i użyj zestawu wierszy parametrów procedury. Jeśli interfejs `IDBSchemaRowset` nie jest dostępny, zapytaj o interfejs `ICommandWithParameters`. Wywołaj `GetParameterInfo`, aby uzyskać informacje. Jeśli żaden interfejs nie jest dostępny, można założyć, że nie ma żadnych parametrów.

1. Dla każdego parametru Wywołaj `AddParameterEntry`, aby dodać parametry i ustawić je.

1. Otwórz zestaw wierszy, ale ustaw parametr bind na **wartość false**.

1. Wywołaj `GetColumnInfo`, aby pobrać kolumny wyjściowe. Użyj `AddBindEntry`, aby dodać kolumnę wyjściową do powiązania.

1. Wywołaj `GetNextResult`, aby określić, czy są dostępne więcej zestawów wierszy. Powtórz kroki od 2 do 5.

Aby zapoznać się z przykładem ręcznej metody dostępu, zobacz `CDBListView::CallProcedure` w przykładowym programie [dbview](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .

## <a name="see-also"></a>Zobacz też

[Korzystanie z metod dostępu](../../data/oledb/using-accessors.md)
