---
title: Polecenia i tabele
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB consumer templates, table support
- CCommand class, OLE DB consumer templates
- commands [C++], OLE DB Consumer Templates
- CTable class
- CAccessorRowset class, command and table classes
- rowsets, accessing
- tables [C++], OLE DB Consumer Templates
- OLE DB consumer templates, command support
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
ms.openlocfilehash: f65bd0f90832039d453d84ab9765781c30750318
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507370"
---
# <a name="commands-and-tables"></a>Polecenia i tabele

Polecenia i tabele umożliwiają dostęp do zestawów wierszy; oznacza to, że otwieranie zestawów wierszy, wykonywanie poleceń i kolumn powiązań. Klasy [CCommand](../../data/oledb/ccommand-class.md) i [CTable](../../data/oledb/ctable-class.md) odpowiednio tworzyją obiekty Command i Table. Te klasy pochodzą z [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) , jak pokazano na poniższej ilustracji.

![CCommand i CTable](../../data/oledb/media/vccommandstables.gif "CCommand i CTable")<br/>
Klasy poleceń i tabel

W poprzedniej tabeli `TAccessor` może być dowolnym typem metody dostępu wymienionym w [typach metod dostępu](../../data/oledb/accessors-and-rowsets.md). `TRowset` może być dowolnym typem zestawu wierszy wymienionym w [typach zestawów wierszy](../../data/oledb/accessors-and-rowsets.md). `TMultiple` Określa typ wyniku (jeden lub wiele zestawów wyników).

[Kreator OLE DB użytkownika ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) pozwala określić, czy chcesz, aby obiekt polecenia lub tabeli.

- W przypadku źródeł danych bez poleceń można użyć `CTable` klasy. Jest on zwykle używany dla prostych zestawów wierszy, które określają brak parametrów i nie wymagają wielu wyników. Ta prosta Klasa otwiera tabelę w źródle danych przy użyciu określonej nazwy tabeli.

- W przypadku źródeł danych, które obsługują polecenia, można użyć `CCommand` klasy. Aby wykonać polecenie, należy wywołać metodę [Open](./ccommand-class.md#open) dla tej klasy. Alternatywnie można wywołać, `Prepare` Aby przygotować polecenie, które ma zostać wykonane więcej niż raz.

   `CCommand` ma trzy argumenty szablonu: typ akcesora, typ zestawu wierszy i typ wyniku ( `CNoMultipleResults` , domyślnie lub `CMultipleResults` ). Jeśli określisz `CMultipleResults` , `CCommand` Klasa obsługuje `IMultipleResults` interfejs i obsługuje wiele zestawów wierszy. Przykład [DBviewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) pokazuje, jak obsługiwać wiele wyników.

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)
