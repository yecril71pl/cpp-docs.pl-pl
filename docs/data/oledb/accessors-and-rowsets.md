---
title: Metody dostępu i zestawy wierszy
ms.date: 11/19/2018
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
ms.openlocfilehash: d29c409f2ed410d9f697419e9a98b675eee7a69d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175722"
---
# <a name="accessors-and-rowsets"></a>Metody dostępu i zestawy wierszy

Do ustawiania i pobierania danych, szablony OLE DB użyj metody dostępu i zestawu wierszy za pomocą [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) klasy. Ta klasa może obsłużyć wielu metod dostępu w różnych typów.

## <a name="accessor-types"></a>Typy metod dostępu

Wszystkie metody dostępu pochodzi od [caccessorbase —](../../data/oledb/caccessorbase-class.md). `CAccessorBase` udostępnia zarówno parametr, jak i powiązanie kolumny.

Na poniższej ilustracji przedstawiono typy metod dostępu.

![Typy metod dostępu](../../data/oledb/media/vcaccessortypes.gif "typy metod dostępu")<br/>
Metoda dostępu do klasy

- [CAccessor](../../data/oledb/caccessor-class.md) Użyj tej metody dostępu, gdy wiesz struktury źródłowej bazy danych w czasie projektowania. `CAccessor` statycznie wiąże rekordu bazy danych, który zawiera buforu, źródła danych.

- [Cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) Użyj tej metody dostępu, jeśli nie znasz struktury bazy danych w czasie projektowania. `CDynamicAccessor` wywołania `IColumnsInfo::GetColumnInfo` można pobrać informacji o kolumnie bazy danych. Tworzy i zarządza metody dostępu i buforu.

- [Cdynamicparameteraccessor —](../../data/oledb/cdynamicparameteraccessor-class.md) Użyj tej metody dostępu, aby obsłużyć nieznane polecenie typów. Podczas przygotowywania poleceń, `CDynamicParameterAccessor` można uzyskać informacje o parametrach z `ICommandWithParameters` interfejsu, jeśli dostawca obsługuje `ICommandWithParameters`.

- [Cdynamicstringaccessor —](../../data/oledb/cdynamicstringaccessor-class.md), [cdynamicstringaccessora —](../../data/oledb/cdynamicstringaccessora-class.md), i [cdynamicstringaccessorw —](../../data/oledb/cdynamicstringaccessorw-class.md) korzystając z tych klas, gdy masz nie znajomości schematu bazy danych. `CDynamicStringAccessorA` pobiera dane jako ciągów ANSI; `CDynamicStringAccessorW` pobiera dane jako ciąg Unicode.

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md) za pomocą tej klasy, można użyć dowolnych typów danych, jeśli dostawca można przekonwertować typu. Obsługuje on kolumny wyników i parametry polecenia.

Poniższa tabela zawiera podsumowanie obsługi w typy metod dostępu szablonów OLE DB.

|Typ metody dostępu|Dynamiczne|Obsługuje params|Bufor|Wielu metod dostępu|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|Nie|Tak|Użytkownik|Tak|
|`CDynamicAccessor`|Tak|Nie|Szablony OLE DB|Nie|
|`CDynamicParameterAccessor`|Tak|Tak|Szablony OLE DB|Nie|
|`CDynamicStringAccessor[A,W]`|Tak|Nie|Szablony OLE DB|Nie|
|`CManualAccessor`|Tak|Tak|Użytkownik|Tak|

## <a name="rowset-types"></a>Typy zestawów wierszy

Szablony OLE DB obsługuje trzy rodzaje zestawów wierszy (patrz rysunek poprzedniego): pojedyncze zestawy wierszy (implementowany przez [CRowset](../../data/oledb/crowset-class.md)), zbiorcze zestawy wierszy (implementowany przez [cbulkrowset —](../../data/oledb/cbulkrowset-class.md)) i zestawy wierszy (zaimplementowano tablicy przez [carrayrowset —](../../data/oledb/carrayrowset-class.md)). Pobieranie pojedyncze zestawy wierszy w pojedynczy wiersz obsługi, kiedy `MoveNext` jest wywoływana. Zbiorcze zestawy wierszy można pobrać dojścia do wielu wierszy. Zestawy wierszy tablicy są zestawy wierszy, który jest możliwy za pomocą składni tablicy.

Na poniższej ilustracji pokazano typy w zestawie wierszy.

![Grafika RowsetType](../../data/oledb/media/vcrowsettypes.gif "RowsetType — grafika")<br/>
Klasy zestawów wierszy

[Zestawy wierszy schematu](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) nie dostęp do danych w danych przechowywania ale zamiast tego uzyskać dostępu do informacji o magazynie danych o nazwie metadanych. Zestawy wierszy schematu są zwykle używane w sytuacjach, w których struktury bazy danych nie jest znany w czasie kompilacji i musi być uzyskana w czasie wykonywania.

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)