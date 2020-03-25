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
ms.openlocfilehash: 0d5f6bd8d5f813497cba399e5c071f43dc1a7c4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211526"
---
# <a name="commands-and-tables"></a>Polecenia i tabele

Polecenia i tabele umożliwiają dostęp do zestawów wierszy; oznacza to, że otwieranie zestawów wierszy, wykonywanie poleceń i kolumn powiązań. Klasy [CCommand](../../data/oledb/ccommand-class.md) i [CTable](../../data/oledb/ctable-class.md) odpowiednio tworzyją obiekty Command i Table. Te klasy pochodzą z [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) , jak pokazano na poniższej ilustracji.

![CCommand i CTable](../../data/oledb/media/vccommandstables.gif "CCommand i CTable")<br/>
Klasy poleceń i tabel

W poprzedniej tabeli `TAccessor` może być dowolnym typem metody dostępu wymienionym w [typach metod dostępu](../../data/oledb/accessors-and-rowsets.md). `TRowset` może być dowolnym typem zestawu wierszy wymienionym w [typach zestawów wierszy](../../data/oledb/accessors-and-rowsets.md). `TMultiple` określa typ wyniku (jeden lub wiele zestawów wyników).

[Kreator OLE DB użytkownika ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) pozwala określić, czy chcesz, aby obiekt polecenia lub tabeli.

- W przypadku źródeł danych bez poleceń można użyć klasy `CTable`. Jest on zwykle używany dla prostych zestawów wierszy, które określają brak parametrów i nie wymagają wielu wyników. Ta prosta Klasa otwiera tabelę w źródle danych przy użyciu określonej nazwy tabeli.

- W przypadku źródeł danych, które obsługują polecenia, można zamiast tego użyć klasy `CCommand`. Aby wykonać polecenie, należy wywołać metodę [Open](../../data/oledb/ccommand-open.md) dla tej klasy. Alternatywnie można wywołać `Prepare`, aby przygotować polecenie, które ma zostać wykonane więcej niż raz.

   `CCommand` ma trzy argumenty szablonu: typ akcesora, typ zestawu wierszy i typ wyniku (`CNoMultipleResults`, domyślnie lub `CMultipleResults`). W przypadku określenia `CMultipleResults`Klasa `CCommand` obsługuje interfejs `IMultipleResults` i obsługuje wiele zestawów wierszy. Przykład [DBviewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) pokazuje, jak obsługiwać wiele wyników.

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)
