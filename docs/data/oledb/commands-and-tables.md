---
title: Polecenia i tabele
ms.date: 10/22/2018
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
ms.openlocfilehash: 0baa388fc1667769892c841a4cc5d68a1b9d0255
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543484"
---
# <a name="commands-and-tables"></a>Polecenia i tabele

Zezwalaj na dostęp do zestawów wierszy; polecenia i tabele oznacza to należy otworzyć zestawów wierszy, wykonaj polecenia i powiązać kolumny. [CCommand](../../data/oledb/ccommand-class.md) i [CTable](../../data/oledb/ctable-class.md) klasy wystąpienia obiektów polecenia i tabeli, odpowiednio. Te klasy pochodzić od [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) jak pokazano na poniższej ilustracji.

![CCommand i CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")<br/>
Polecenie i klasy tabeli

W poprzedniej tabeli `TAccessor` mogą być dowolnego typu metody dostępu na liście [typy metod dostępu](../../data/oledb/accessors-and-rowsets.md). `TRowset` może być dowolnego typu zestawu wierszy na liście [typów w zestawie wierszy](../../data/oledb/accessors-and-rowsets.md). `TMultiple` Określa typ wyniku (jednej lub wielu zestawu wyników).

[OLE DB Kreator konsumenta ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) pozwala określić, czy obiekt polecenia lub tabeli.

- W przypadku źródeł danych bez poleceń, można użyć `CTable` klasy. Zazwyczaj służy ono do proste zestawy wierszy, które nie określono żadnych parametrów, wymagają wielu wyników. Ta klasa prostych otwiera tabeli w źródle danych, za pomocą nazwy tabeli, który określisz.

- W przypadku źródeł danych, które obsługują polecenia, można użyć `CCommand` klasy zamiast tego. Aby wykonanie polecenia, należy wywołać [Otwórz](../../data/oledb/ccommand-open.md) od tej klasy. Alternatywnie, można wywołać `Prepare` przygotować polecenie, które chcesz wykonać więcej niż jeden raz.

   `CCommand` ma trzy argumenty szablonu: typu dostępu, typ zestawu wierszy i typ wyniku (`CNoMultipleResults`, domyślnie lub `CMultipleResults`). Jeśli określisz `CMultipleResults`, `CCommand` klasy obsługuje `IMultipleResults` interfejs i obsługuje wiele zestawów wierszy. [DBVIEWER](https://github.com/Microsoft/VCSamples) przykład pokazuje, jak obsługiwać wiele wyników.

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)