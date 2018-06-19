---
title: Dokumentacja szablonów konsumentów OLE DB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc-attr.db_param
- vc-attr.db_column
- vc-attr.db_accessor
- vc-attr.db_command
- vc-attr.db_table
- vc.templates.ole
- vc-attr.db_source
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, classes
ms.assetid: cfc7f698-1a0e-4a09-a4d3-ccb99e6654fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5b599a1c7a1b256cc9c56d772a15621beda286f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112059"
---
# <a name="ole-db-consumer-templates-reference"></a>Szablony konsumentów OLE DB — kompendium
Szablony OLE DB konsumenta zawiera następujące klasy. Materiałów referencyjnych zawiera także tematy na [makra dla OLE DB szablonów konsumentów](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).  
  
## <a name="session-classes"></a>Klasy sesji  
 [CDataConnection](../../data/oledb/cdataconnection-class.md)  
 Zarządza połączenia ze źródłem danych. Jest to przydatne klasa do tworzenia klientów, ponieważ hermetyzuje niezbędnych obiektów (źródła danych i sesji), a niektóre czynności, które należy wykonać podczas nawiązywania połączenia ze źródłem danych.  
  
 [CDataSource](../../data/oledb/cdatasource-class.md)  
 Odnosi się do obiektu źródła danych OLE DB, reprezentujący połączenia za pośrednictwem dostawcy ze źródłem danych. Co najmniej jednej bazy danych sesji, każdy jest reprezentowany przez `CSession` obiektu; może się odbywać w ramach pojedynczego połączenia.  
  
 [CEnumerator](../../data/oledb/cenumerator-class.md)  
 Odpowiada obiekt modułu wyliczającego OLE DB, który pobiera wierszy informacje o dostępnych źródeł danych.  
  
 [CEnumeratorAccessor](../../data/oledb/cenumeratoraccessor-class.md)  
 Używane przez `CEnumerator` dostępu do danych z zestawu wierszy modułu wyliczającego. Ten zestaw wierszy składa się z źródła danych i moduły wyliczające widoczne z bieżącej modułu wyliczającego.  
  
 [CSession](../../data/oledb/csession-class.md)  
 Reprezentuje sesję dostępu pojedynczej bazy danych. Co najmniej jednej sesji może być skojarzony z poszczególnymi `CDataSource` obiektu.  
  
## <a name="accessor-classes"></a>Klasy dostępu  
 [CAccessor](../../data/oledb/caccessor-class.md)  
 Używane do rekordów statycznie powiązanych ze źródłem danych. Użyj tej klasy dostępu, gdy wiesz struktura źródła danych.  
  
 [Caccessorbase —](../../data/oledb/caccessorbase-class.md)  
 Klasa podstawowa dla wszystkich klas dostępu.  
  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)  
 Metoda dostępu, które można utworzyć w czasie wykonywania na podstawie informacji kolumny zestawu wierszy. Klasa używana do pobierania danych, jeśli nie znasz struktura źródła danych.  
  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)  
 Metoda dostępu, który można użyć w przypadku typów poleceń jest nieznany. Uzyskuje informacje o parametrach wywołując `ICommandWithParameters` interfejsu, jeśli dostawca obsługuje ten interfejs.  
  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)  
 Umożliwia dostęp do źródła danych, jeśli masz żadnych informacji na temat struktury bazy danych.  
  
 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)  
 Podobnie jak `CDynamicStringAccessor` z tą różnicą, że ta klasa żądania danych dostępnych z magazynu danych jako dane ciągu ANSI.  
  
 [CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)  
 Podobnie jak `CDynamicStringAccessor` z tą różnicą, że ta klasa żądania danych dostępnych z magazynu danych jako dane ciąg UNICODE.  
  
 [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)  
 Metoda dostępu za pomocą metod do obsługi zarówno kolumny, jak i parametry polecenia. Z tej klasy można użyć wszystkie typy danych, tak długo, jak dostawca można przekonwertować typu.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Może służyć jako argument szablonu nie można się z klasy do obsługi parametry lub kolumny wyjściowe.  
  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md)  
 Podobnie jak `CDynamicStringAccessor` z tą różnicą, że ta klasa konwertuje wszystkie dane uzyskiwane ze źródła danych jako dane (oznakowany) w formacie XML.  
  
## <a name="rowset-classes"></a>Klasy zestawów wierszy  
 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md)  
 Hermetyzuje zestawu wierszy i jego skojarzone metody dostępu.  
  
 [CArrayRowset](../../data/oledb/carrayrowset-class.md)  
 Umożliwia dostęp do elementów zestawu wierszy za pomocą składni tablicy.  
  
 [CBulkRowset](../../data/oledb/cbulkrowset-class.md)  
 Służy do pobierania i manipulowanie wierszami zbiorczo przez pobranie wielu dojść do wierszy przy użyciu jednego wywołania.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Może służyć jako argument szablonu Jeśli polecenie nie zwraca zestawu wierszy.  
  
 [CRestrictions](../../data/oledb/crestrictions-class.md)  
 Pozwala określić ograniczenia dotyczące zestawów wierszy schematu.  
  
 [CRowset](../../data/oledb/crowset-class.md)  
 Używane do manipulowania, ustawiania i pobierania zestawu wierszy danych.  
  
 [CStreamRowset](../../data/oledb/cstreamrowset-class.md)  
 Zwraca `ISequentialStream` obiektu zamiast zestawu wierszy; można następnie użyć **odczytu** metody do pobierania danych w formacie XML. (SQL Server 2000 jest formatowanie; należy pamiętać, że ta funkcja działa z programem SQL Server 2000 tylko).  
  
 [Irowsetnotifyimpl —](../../data/oledb/irowsetnotifyimpl-class.md)  
 Udostępnia implementację fikcyjny dla `IRowsetNotify`, pusty funkcje dla `IRowsetNotify` metody `OnFieldChange`, `OnRowChange`, i `OnRowsetChange`.  
  
 [Klasy zestawów wierszy schematu i klasy Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)  
  
 Szablony OLE DB zapewniają zestaw klas, które odpowiadają zestawów wierszy schematu OLE DB.  
  
## <a name="command-classes"></a>Klasy poleceń  
 [CCommand](../../data/oledb/ccommand-class.md)  
 Używany do ustawiania i wykonywania na podstawie parametru polecenia OLE DB. Aby otworzyć tylko prosty zestaw wierszy, użyj `CTable` zamiast tego.  
  
 [Cmultipleresults —](../../data/oledb/cmultipleresults-class.md)  
 Używane jako argument szablonu dla `CCommand` szablonu polecenia do obsługi wielu zestawów wyników.  
  
 [CNoAccessor](../../data/oledb/cnoaccessor-class.md)  
 Używane jako argument szablonu dla szablonu klasy, taką jak `CCommand` i `CTable`, które trwają argumentu klasy metody dostępu. Użyj `CNoAccessor` Jeśli nie chcesz klasy do obsługi parametry lub kolumny wyjściowe.  
  
 [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)  
 Używane jako argument szablonu dla `CCommand` szablonu polecenie, aby obsłużyć jednego zestawu wierszy. `CNoMultipleResults` jest to wartość domyślna argumentu szablonu.  
  
 [CNoRowset](../../data/oledb/cnorowset-class.md)  
 Używane jako argument szablonu dla `CCommand` lub `CTable` Jeśli polecenia lub tabeli nie zwraca zestawu wierszy.  
  
 [CTable](../../data/oledb/ctable-class.md)  
 Umożliwia dostęp do prostego zestawu wierszy bez parametrów.  
  
## <a name="property-classes"></a>Właściwość klasy  
 [CDBPropIDSet](../../data/oledb/cdbpropidset-class.md)  
 Służy do przekazywania tablicę identyfikatorów właściwości, dla których użytkownik chce informacje dotyczące właściwości. Właściwości należą do zestawu jedną właściwość.  
  
 [CDBPropSet](../../data/oledb/cdbpropset-class.md)  
 Używany do ustawiania właściwości przez dostawcę.  
  
## <a name="bookmark-class"></a>Klasa zakładki  
 [CBookmark](../../data/oledb/cbookmark-class.md)  
 Używana jako indeks, aby uzyskać dostęp do danych w zestawie wierszy.  
  
## <a name="error-class"></a>Błąd — klasa  
 [CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)  
 Używane do pobierania informacji o błędach OLE DB.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja szablonów OLE DB Provider](../../data/oledb/ole-db-provider-templates-reference.md)   
 [Szablony OLE DB](../../data/oledb/ole-db-templates.md)