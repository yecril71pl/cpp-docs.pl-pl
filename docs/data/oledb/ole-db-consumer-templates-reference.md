---
title: Szablony konsumentów OLE DB — kompendium
ms.date: 11/04/2016
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: fb0b24798b3f2682bbbec7624df34b40a2a9f4cc
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032274"
---
# <a name="ole-db-consumer-templates-reference"></a>Szablony konsumentów OLE DB — kompendium

Szablony OLE DB klienta zawierają następujące klasy. Materiały referencyjne zawiera również tematy na [makra dla OLE DB szablonów konsumentów](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="session-classes"></a>Klasy sesji

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
Zarządza połączenia ze źródłem danych. Jest to przydatne klasa do tworzenia klientów, ponieważ hermetyzuje niezbędnych obiektów (źródła danych i sesji), a niektóre czynności, które należy wykonać podczas nawiązywania połączenia ze źródłem danych.

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
Odnosi się do obiektu źródła danych OLE DB, reprezentujący za pośrednictwem dostawcy połączenia ze źródłem danych. Co najmniej jednej bazy danych sesji, każdy jest reprezentowany przez `CSession` obiektu; może się odbywać na pojedyncze połączenie.

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
Odpowiada to obiekt modułu wyliczającego OLE DB, który pobiera informacje o zestawie wierszy o dostępnych źródłach danych.

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
Używane przez `CEnumerator` dostępu do danych z zestawu wierszy modułu wyliczającego. Ten zestaw wierszy składa się z źródła danych i moduły wyliczające widoczne z bieżącej modułu wyliczającego.

[CSession](../../data/oledb/csession-class.md)<br/>
Reprezentuje sesję dostępu do pojedynczej bazy danych. Co najmniej jednej sesji można skojarzyć z poszczególnymi `CDataSource` obiektu.

## <a name="accessor-classes"></a>Metoda dostępu do klasy

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
Używane dla rekordów, które są statycznie powiązane ze źródłem danych. Klasa metody dostępu jest używana, gdy wiesz struktury źródła danych.

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
Klasa bazowa dla wszystkich klas dostępu.

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
Metoda dostępu, które mogą być tworzone w czasie wykonywania, na podstawie informacji kolumny zestawu wierszy. Klasa jest używana do pobierania danych, jeśli nie znasz struktury źródła danych.

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
Metoda dostępu, który może służyć w przypadku typów poleceń nieznany. Uzyskuje informacje o parametrach, wywołując `ICommandWithParameters` interfejsu, jeśli dostawca obsługuje ten interfejs.

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
Umożliwia dostęp do źródła danych, gdy nie znać struktury bazy danych.

[CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
Podobnie jak `CDynamicStringAccessor` różnicą, że ta klasa żądania danych dostępnych z magazynu danych jako dane ciągu ANSI.

[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
Podobnie jak `CDynamicStringAccessor` z tą różnicą, że ta klasa żądania danych dostępnych z magazynu danych jako dane ciągu UNICODE.

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
Metoda dostępu za pomocą metod do obsługi zarówno kolumny, jak i parametry polecenia. Za pomocą tej klasy można użyć wszystkie typy danych, tak długo, jak dostawca można przekonwertować typu.

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
Może służyć jako argument szablonu, gdy nie chcesz, aby klasy, która ma obsługiwać parametry lub kolumny wyjściowe.

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
Podobnie jak `CDynamicStringAccessor` z tą różnicą, że ta klasa konwertuje wszystkie dane używane z magazynu danych jako danych (oznakowany) w formacie XML.

## <a name="rowset-classes"></a>Klasy zestawów wierszy

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
Hermetyzuje zestawu wierszy i skojarzone metody dostępu.

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
Umożliwia dostęp do elementów zestawu wierszy za pomocą składni tablicy.

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
Używane do pobierania i manipulowanie wierszami w trybie zbiorczym pobierając wielu dojść do wierszy za pomocą jednego wywołania.

[Cnorowset —](../../data/oledb/cnorowset-class.md)<br/>
Może służyć jako argument szablonu, jeśli polecenie nie zwraca zestawu wierszy.

[cRestrictions](../../data/oledb/crestrictions-class.md)<br/>
Można określić ograniczenia dla zestawów wierszy schematu.

[CRowset](../../data/oledb/crowset-class.md)<br/>
Używane do manipulowania, ustawiania i pobierania zestawu wierszy danych.

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
Zwraca `ISequentialStream` obiektu zamiast zestawu wierszy; następnie użyć `Read` metodę, aby pobrać dane w formacie XML. (SQL Server 2000 jest formatowanie; należy pamiętać, że ta funkcja działa z programem SQL Server 2000 tylko).

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
Dostarcza implementację zastępczy dla `IRowsetNotify`, za pomocą funkcji puste dla `IRowsetNotify` metody `OnFieldChange`, `OnRowChange`, i `OnRowsetChange`.

[Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

Szablony OLE DB udostępnia zestaw klas, które odpowiadają zestawów wierszy schematu OLE DB.

## <a name="command-classes"></a>Klasy poleceń

[CCommand](../../data/oledb/ccommand-class.md)<br/>
Używany do ustawiania i wykonywania na podstawie parametru polecenia OLE DB. Aby otworzyć tylko prosty zestaw wierszy, należy użyć `CTable` zamiast tego.

[Cmultipleresults —](../../data/oledb/cmultipleresults-class.md)<br/>
Używane jako argument szablonu dla `CCommand` szablonu, jeśli chcesz, aby polecenia do obsługi wielu zestawów wyników.

[CNoAccessor](../../data/oledb/cnoaccessor-class.md)<br/>
Używane jako argument szablonu dla klasy szablonów, taką jak `CCommand` i `CTable`, które trwają argument klasy dostępu. Użyj `CNoAccessor` Jeśli nie chcesz, aby klasy, która ma obsługiwać parametry lub kolumny wyjściowe.

[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)<br/>
Używane jako argument szablonu dla `CCommand` szablonu, jeśli chcesz, aby polecenia do obsługi pojedynczego zestawu wierszy. `CNoMultipleResults` jest wartością domyślną dla argumentu szablonu.

[Cnorowset —](../../data/oledb/cnorowset-class.md)<br/>
Używane jako argument szablonu dla `CCommand` lub `CTable` Jeśli polecenie lub tabeli nie zwraca zestawu wierszy.

[CTable](../../data/oledb/ctable-class.md)<br/>
Umożliwia dostęp do prostego zestawu wierszy bez parametrów.

## <a name="property-classes"></a>Właściwości klasy

[Cdbpropidset —](../../data/oledb/cdbpropidset-class.md)<br/>
Używany do przekazania tablicę identyfikatorów właściwości, dla których użytkownik chce, aby informacje o właściwościach. Właściwości należą do zestawu jednej właściwości.

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
Używany do ustawiania właściwości w dostawcy.

## <a name="bookmark-class"></a>Klasa zakładki

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
Używane jako indeks do uzyskiwania dostępu do danych w zestawie wierszy.

## <a name="error-class"></a>Klasa błędów

[Cdberrorinfo —](../../data/oledb/cdberrorinfo-class.md)<br/>
Używany do pobierania informacji o błędzie OLE DB.

## <a name="see-also"></a>Zobacz także

[Szablony dostawców OLE DB — kompendium](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Szablony OLE DB](../../data/oledb/ole-db-templates.md)