---
title: Metody dostępu i zestawy wierszy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 49f5415f6c75984f968b25fb709c20d80dde554f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="accessors-and-rowsets"></a>Metody dostępu i zestawy wierszy
Do ustawiania i pobierania danych, szablony OLE DB użyj metody dostępu i zestawu wierszy za pomocą [caccessorrowset —](../../data/oledb/caccessorrowset-class.md) klasy. Ta klasa może obsługiwać wiele metod dostępu do różnych typów.  
  
## <a name="accessor-types"></a>Typy metod dostępu  
 Wszystkie metody dostępu pochodzi od [caccessorbase —](../../data/oledb/caccessorbase-class.md). `CAccessorBase` zapewnia parametru i powiązanie kolumny.  
  
 Na poniższej ilustracji przedstawiono typy metod dostępu.  
  
 ![Typy metod dostępu](../../data/oledb/media/vcaccessortypes.gif "vcaccessortypes")  
Klasy dostępu  
  
-   [CAccessor](../../data/oledb/caccessor-class.md) Użyj tej metody dostępu, gdy wiesz struktury źródłowej bazy danych w czasie projektowania. `CAccessor` statycznie wiąże rekordu bazy danych, który zawiera buforu, źródła danych.  
  
-   [Cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) Użyj tej metody dostępu, jeśli nie znasz struktury bazy danych w czasie projektowania. `CDynamicAccessor` wywołania `IColumnsInfo::GetColumnInfo` można pobrać informacji o kolumnie bazy danych. Tworzy i zarządza metody dostępu i buforu.  
  
-   [Cdynamicparameteraccessor —](../../data/oledb/cdynamicparameteraccessor-class.md) używania tej metody dostępu na potrzeby obsługi typów nieznane polecenie. Podczas przygotowywania poleceń, `CDynamicParameterAccessor` można uzyskać informacji o parametru `ICommandWithParameters` interfejsu, jeśli dostawca obsługuje `ICommandWithParameters`.  
  
-   [Cdynamicstringaccessor —](../../data/oledb/cdynamicstringaccessor-class.md), [cdynamicstringaccessora —](../../data/oledb/cdynamicstringaccessora-class.md), i [cdynamicstringaccessorw —](../../data/oledb/cdynamicstringaccessorw-class.md) korzystając z tych klas, gdy użytkownik nie korzystają z nie schematu bazy danych. `CDynamicStringAccessorA` pobiera dane jako ciągów ANSI; `CDynamicStringAccessorW` pobiera dane jako ciąg Unicode.  
  
-   [Cmanualaccessor —](../../data/oledb/cmanualaccessor-class.md) z tej klasy można użyć niezależnie od typów danych, jeśli dostawca można przekonwertować typu. Obsługuje ona zarówno wynik i parametry polecenia.  
  
 W poniższej tabeli przedstawiono obsługę w typy metod dostępu szablonów OLE DB.  
  
|Typ metody dostępu|dynamiczne|Obsługuje params|Bufor|Wiele metod dostępu|  
|-------------------|-------------|--------------------|------------|------------------------|  
|`CAccessor`|Nie|Tak|Użytkownik|Tak|  
|`CDynamicAccessor`|Tak|Nie|Szablony OLE DB|Nie|  
|`CDynamicParameterAccessor`|Tak|Tak|Szablony OLE DB|Nie|  
|`CDynamicStringAccessor[A,W]`|Tak|Nie|Szablony OLE DB|Nie|  
|`CManualAccessor`|Tak|Tak|Użytkownik|Tak|  
  
## <a name="rowset-types"></a>Typy zestawu wierszy  
 Szablony OLE DB obsługuje trzy rodzaje zestawy wierszy (patrz rysunek poprzedniego): pojedyncze zestawy wierszy (implementowane przez [CRowset](../../data/oledb/crowset-class.md)), zbiorcze zestawy wierszy (implementowane przez [cbulkrowset —](../../data/oledb/cbulkrowset-class.md)) i zestawy wierszy (zaimplementowana tablicy przez [carrayrowset —](../../data/oledb/carrayrowset-class.md)). Pobieranie pojedyncze zestawy wierszy w pojedynczy wiersz obsługi, gdy `MoveNext` jest wywoływana. Zbiorcze zestawy wierszy można pobrać dojścia do wielu wierszy. Zestawy wierszy tablicy są zestawy wierszy, do którego mogą uzyskać dostęp za pomocą składni tablicy.  
  
 Na poniższej ilustracji przedstawiono typy zestawu wierszy.  
  
 ![Grafika RowsetType](../../data/oledb/media/vcrowsettypes.gif "vcrowsettypes")  
Klasy zestawów wierszy  
  
 [Zestawy wierszy schematu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) nie dostępu do danych przechowywania ale zamiast tego dostępu do informacji o magazynie danych o nazwie metadanych. Zestawy wierszy schematu są zazwyczaj używane w sytuacjach, w których struktury bazy danych nie jest znany w czasie kompilacji i musi być uzyskany w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)