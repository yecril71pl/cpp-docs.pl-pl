---
title: Polecenia i tabele | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a3d045035ad757286b30b4adecf2f04f4dfbfd25
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340198"
---
# <a name="commands-and-tables"></a>Polecenia i tabele
Zezwalaj na dostęp do zestawów wierszy; polecenia i tabele oznacza to należy otworzyć zestawów wierszy, wykonaj polecenia i powiązać kolumny. [CCommand](../../data/oledb/ccommand-class.md) i [CTable](../../data/oledb/ctable-class.md) klasy wystąpienia obiektów polecenia i tabeli, odpowiednio. Te klasy pochodzić od [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) jak pokazano na poniższej ilustracji.  
  
 ![CCommand i CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")  
Polecenie i klasy tabeli  
  
 W poprzedniej tabeli `TAccessor` mogą być dowolnego typu metody dostępu na liście [typy metod dostępu](../../data/oledb/accessors-and-rowsets.md). *TRowset* mogą być dowolnego typu zestawu wierszy na liście [typów w zestawie wierszy](../../data/oledb/accessors-and-rowsets.md). *TMultiple* Określa typ wyniku (jednej lub wielu zestawu wyników).  
  
 [OLE DB Kreator konsumenta ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) pozwala określić, czy obiekt polecenia lub tabeli.  
  
-   W przypadku źródeł danych bez poleceń, można użyć `CTable` klasy. Zazwyczaj służy ono do proste zestawy wierszy, które nie określono żadnych parametrów, wymagają wielu wyników. Ta klasa prostych otwiera tabeli w źródle danych, za pomocą nazwy tabeli, który określisz.  
  
-   W przypadku źródeł danych, które obsługują polecenia, można użyć `CCommand` klasy zamiast tego. Aby wykonanie polecenia, należy wywołać [Otwórz](../../data/oledb/ccommand-open.md) od tej klasy. Alternatywnie, można wywołać `Prepare` przygotować polecenie, które chcesz wykonać więcej niż jeden raz.  
  
     `CCommand` ma trzy argumenty szablonu: typu dostępu, typ zestawu wierszy i typ wyniku (`CNoMultipleResults`, domyślnie lub `CMultipleResults`). Jeśli określisz `CMultipleResults`, `CCommand` klasy obsługuje `IMultipleResults` interfejs i obsługuje wiele zestawów wierszy. [DBVIEWER](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832) przykład pokazuje, jak obsługiwać wiele wyników.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)