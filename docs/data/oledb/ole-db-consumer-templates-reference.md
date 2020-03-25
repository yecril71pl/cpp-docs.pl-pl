---
title: Szablony konsumentów OLE DB — kompendium
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
ms.openlocfilehash: 13805ab1dc2c2b4792fd05c9140006c610b42f75
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210109"
---
# <a name="ole-db-consumer-templates-reference"></a>Szablony konsumentów OLE DB — kompendium

Szablony konsumentów OLE DB zawierają następujące klasy. Materiał referencyjny zawiera również tematy dotyczące [makr dla OLE DB szablonów konsumentów](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="session-classes"></a>Klasy sesji

[CDataConnection](../../data/oledb/cdataconnection-class.md)<br/>
Zarządza połączeniem ze źródłem danych. Jest to użyteczna Klasa do tworzenia klientów, ponieważ hermetyzuje niezbędne obiekty (Źródło danych i sesja) oraz niektóre zadania, które należy wykonać podczas nawiązywania połączenia ze źródłem danych.

[CDataSource](../../data/oledb/cdatasource-class.md)<br/>
Odnosi się do obiektu źródła danych OLE DB, reprezentującego połączenie przez dostawcę ze źródłem danych. Co najmniej jedna sesja bazy danych reprezentowana przez obiekt `CSession` może odbywać się przy użyciu jednego połączenia.

[CEnumerator](../../data/oledb/cenumerator-class.md)<br/>
Odnosi się do obiektu modułu wyliczającego OLE DB, który pobiera informacje o zestawie wierszy dla dostępnych źródeł danych.

[CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)<br/>
Używane przez `CEnumerator` do uzyskiwania dostępu do danych z zestawu wierszy modułu wyliczającego. Ten zestaw wierszy składa się ze źródeł danych i modułów wyliczających widocznych z bieżącego modułu wyliczającego.

[CSession](../../data/oledb/csession-class.md)<br/>
Reprezentuje sesję dostępu pojedynczej bazy danych. Co najmniej jedna sesja może być skojarzona z każdym obiektem `CDataSource`.

## <a name="accessor-classes"></a>Klasy akcesora

[CAccessor](../../data/oledb/caccessor-class.md)<br/>
Używany dla rekordów, które są statycznie powiązane ze źródłem danych. Użyj tej klasy akcesora, gdy znasz strukturę źródła danych.

[CAccessorBase](../../data/oledb/caccessorbase-class.md)<br/>
Klasa bazowa dla wszystkich klas metod dostępu.

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)<br/>
Metoda dostępu, którą można utworzyć w czasie wykonywania, na podstawie informacji o kolumnie zestawu wierszy. Użyj tej klasy, aby pobrać dane, jeśli nie znasz struktury źródła danych.

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
Metoda dostępu, która może być używana w przypadku nieznanych typów poleceń. Uzyskuje informacje o parametrach, wywołując interfejs `ICommandWithParameters`, jeśli dostawca obsługuje interfejs.

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
Pozwala uzyskać dostęp do źródła danych, gdy nie ma żadnej znajomości podstawowej struktury bazy danych.

[CDynamicStringAccessorA —](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
Podobnie jak w przypadku `CDynamicStringAccessor`, z tą różnicą, że ta klasa żąda danych uzyskanych z magazynu danych jako dane typu ANSI.

[CDynamicStringAccessorW —](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
Podobnie jak w przypadku `CDynamicStringAccessor`, z tą różnicą, że ta klasa żąda danych uzyskanych z magazynu danych jako dane ciągu UNICODE.

[CManualAccessor](../../data/oledb/cmanualaccessor-class.md)<br/>
Metoda dostępu z metodami do obsługi zarówno kolumn, jak i parametrów poleceń. Za pomocą tej klasy można użyć dowolnego typu danych, o ile dostawcy mogą konwertować typ.

[CNoAccessor —](../../data/oledb/cnoaccessor-class.md)<br/>
Może służyć jako argument szablonu, gdy nie chcesz, aby Klasa obsługiwała parametry lub kolumny wyjściowe.

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)<br/>
Podobnie jak w przypadku `CDynamicStringAccessor`, z tą różnicą, że ta klasa konwertuje wszystkie dane, do których uzyskano dostęp z magazynu danych jako dane sformatowane w formacie XML.

## <a name="rowset-classes"></a>Klasy zestawu wierszy

[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)<br/>
Hermetyzuje zestaw wierszy i powiązane z nim metody dostępu.

[CArrayRowset](../../data/oledb/carrayrowset-class.md)<br/>
Używane do uzyskiwania dostępu do elementów zestawu wierszy przy użyciu składni tablicy.

[CBulkRowset](../../data/oledb/cbulkrowset-class.md)<br/>
Służy do pobierania i manipulowania wierszy luzem przez pobranie wielu dojść do wierszy przy użyciu jednego wywołania.

[CNoRowset —](../../data/oledb/cnorowset-class.md)<br/>
Może być używany jako argument szablonu, jeśli polecenie nie zwraca zestawu wierszy.

[CRestrictions](../../data/oledb/crestrictions-class.md)<br/>
Służy do określania ograniczeń dla zestawów wierszy schematu.

[CRowset](../../data/oledb/crowset-class.md)<br/>
Służy do manipulowania, ustawiania i pobierania danych zestawu wierszy.

[CStreamRowset](../../data/oledb/cstreamrowset-class.md)<br/>
Zwraca obiekt `ISequentialStream`, a nie zestaw wierszy; następnie użyj metody `Read`, aby pobrać dane w formacie XML. (SQL Server 2000 wykonuje formatowanie; należy zauważyć, że ta funkcja działa tylko z SQL Server 2000).

[IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md)<br/>
Zapewnia implementację fikcyjną dla `IRowsetNotify`, z pustymi funkcjami dla metod `IRowsetNotify` `OnFieldChange`, `OnRowChange`i `OnRowsetChange`.

[Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)

Szablony OLE DB udostępniają zestaw klas, które odpowiadają OLE DB zestawom wierszy schematu.

## <a name="command-classes"></a>Klasy poleceń

[CCommand](../../data/oledb/ccommand-class.md)<br/>
Służy do ustawiania i wykonywania polecenia OLE DB opartego na parametrach. Aby tylko otworzyć prosty zestaw wierszy, należy zamiast tego użyć `CTable`.

[CMultipleResults —](../../data/oledb/cmultipleresults-class.md)<br/>
Używany jako argument szablonu `CCommand`, gdy chcesz, aby polecenie obsługiwało wiele zestawów wyników.

[CNoAccessor —](../../data/oledb/cnoaccessor-class.md)<br/>
Używany jako argument szablonu dla klas szablonu, takich jak `CCommand` i `CTable`, który przyjmuje argument klasy metody dostępu. Użyj `CNoAccessor`, jeśli nie chcesz, aby Klasa obsługiwała parametry lub kolumny wyjściowe.

[CNoMultipleResults —](../../data/oledb/cnomultipleresults-class.md)<br/>
Używany jako argument szablonu `CCommand`, gdy polecenie ma obsługiwać pojedynczy zestaw wierszy. `CNoMultipleResults` jest wartością domyślną dla argumentu szablonu.

[CNoRowset —](../../data/oledb/cnorowset-class.md)<br/>
Używany jako argument szablonu dla `CCommand` lub `CTable`, jeśli polecenie lub tabela nie zwracają zestawu wierszy.

[CTable](../../data/oledb/ctable-class.md)<br/>
Służy do uzyskiwania dostępu do prostego zestawu wierszy bez parametrów.

## <a name="property-classes"></a>Klasy właściwości

[CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)<br/>
Służy do przekazywania tablicy identyfikatorów właściwości, dla których odbiorca chce uzyskać informacje o właściwościach. Właściwości należą do jednego zestawu właściwości.

[CDBPropSet](../../data/oledb/cdbpropset-class.md)<br/>
Służy do ustawiania właściwości dostawcy.

## <a name="bookmark-class"></a>Zakładka — Klasa

[CBookmark](../../data/oledb/cbookmark-class.md)<br/>
Używany jako indeks do uzyskiwania dostępu do danych w zestawie wierszy.

## <a name="error-class"></a>Error — Klasa

[CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)<br/>
Służy do pobierania OLE DB informacji o błędzie.

## <a name="see-also"></a>Zobacz też

[Szablony dostawców OLE DB — dokumentacja](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Szablony OLE DB](../../data/oledb/ole-db-templates.md)
