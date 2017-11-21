---
title: Polecenia i tabele | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b5f849dc66746fe5740f47182a4fbacbc4d6c60d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="commands-and-tables"></a>Polecenia i tabele
Polecenia i tabele zezwalają na dostęp do zestawów wierszy; oznacza to otwórz zestawów wierszy, wykonywania poleceń i powiązać kolumny. [CCommand](../../data/oledb/ccommand-class.md) i [CTable](../../data/oledb/ctable-class.md) odpowiednio wystąpienia klasy obiekt polecenia i tabeli. Te klasy pochodzić od [caccessorrowset —](../../data/oledb/caccessorrowset-class.md) jak pokazano na poniższej ilustracji.  
  
 ![CCommand i CTable](../../data/oledb/media/vccommandstables.gif "vccommandstables")  
Polecenie i klasy tabeli  
  
 W poprzedniej tabeli `TAccessor` mogą być dowolnego typu metody dostępu na liście [typy metod dostępu](../../data/oledb/accessors-and-rowsets.md). *TRowset* mogą być dowolnego typu zestawu wierszy na liście [typów wierszy](../../data/oledb/accessors-and-rowsets.md). *TMultiple* Określa typ wyniku (jeden lub wiele zestawu wyników).  
  
 [OLE DB Kreator konsumenta ATL](../../atl/reference/atl-ole-db-consumer-wizard.md) pozwala określić, czy obiekt polecenia lub tabeli.  
  
-   W przypadku źródeł danych bez polecenia, można użyć `CTable` klasy. Na ogół służy on do proste zestawy wierszy, określ bez parametrów, który wymaga wielu nie zwróciło żadnych wyników. Ta klasa prostych otwiera tabeli w źródle danych, przy użyciu określonej nazwy tabeli.  
  
-   W przypadku źródeł danych, które obsługują polecenia, można użyć `CCommand` zamiast klasy. Do wykonania polecenia, należy wywołać [Otwórz](../../data/oledb/ccommand-open.md) od tej klasy. Alternatywnie, można wywołać `Prepare` przygotować polecenie, które chcesz wykonać więcej niż raz.  
  
     **CCommand** ma trzy argumenty szablonu: typu dostępu, typ zestawu wierszy i typ wyniku (`CNoMultipleResults`, domyślnie lub `CMultipleResults`). Jeśli określisz `CMultipleResults`, `CCommand` klasy obsługuje **interfejsu IMultipleResults** interfejsu i obsługuje wiele zestawów wierszy. [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) przykładowych pokazano, jak obsługiwać wiele wyników.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)