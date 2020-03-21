---
title: 'Zestaw rekordów: zbiorcze pobieranie rekordów (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
ms.openlocfilehash: cd9597da7ab4c405f90a145182d63945cef48c53
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079824"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Zestaw rekordów: zbiorcze pobieranie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

Klasa `CRecordset` zapewnia obsługę pobierania wierszy zbiorczych, co oznacza, że wiele rekordów można pobrać jednocześnie w ramach pojedynczego pobrania, zamiast pobierać jeden rekord jednocześnie ze źródła danych. Pobieranie wierszy zbiorczych można zaimplementować tylko w klasie pochodnej `CRecordset`. Proces przenoszenia danych ze źródła danych do obiektu zestawu rekordów jest nazywany zbiorczym polem rekordów wymiany (bulk RFX). Należy pamiętać, że jeśli nie używasz pobierania wierszy zbiorczych w klasie pochodnej `CRecordset`, dane są transferowane za pośrednictwem wymiany pól rekordów (RFX). Aby uzyskać więcej informacji, zobacz [rekord Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

W tym temacie objaśniono:

- [Jak CRecordset obsługuje pobieranie wierszy zbiorczych](#_core_how_crecordset_supports_bulk_row_fetching).

- [Niektóre specjalne zagadnienia dotyczące korzystania z pobierania wierszy zbiorczych](#_core_special_considerations).

- [Jak zaimplementować wymianę pól rekordów zbiorczych](#_core_how_to_implement_bulk_record_field_exchange).

##  <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Jak CRecordset obsługuje pobieranie wierszy zbiorczych

Przed otwarciem obiektu zestawu rekordów można zdefiniować rozmiar zestawu wierszy przy użyciu funkcji składowej `SetRowsetSize`. Rozmiar zestawu wierszy określa, ile rekordów ma być pobieranych podczas pojedynczego pobierania. Po zaimplementowaniu pobierania wierszy zbiorczych domyślny rozmiar zestawu wierszy wynosi 25. Jeśli pobieranie wierszy zbiorczych nie jest zaimplementowane, rozmiar zestawu wierszy pozostaje ustalony na 1.

Po zainicjowaniu rozmiaru zestawu wierszy wywołaj funkcję [Open](../../mfc/reference/crecordset-class.md#open) member. W tym miejscu należy określić opcję `CRecordset::useMultiRowFetch` parametru *dwOptions* w celu zaimplementowania pobierania wierszy zbiorczych. Ponadto możesz ustawić opcję `CRecordset::userAllocMultiRowBuffers`. Mechanizm wymiany pól rekordów zbiorczych używa tablic do przechowywania wielu wierszy danych pobranych podczas pobierania. Te bufory magazynów mogą być przydzielane automatycznie przez platformę lub można je przydzielić ręcznie. Określenie opcji `CRecordset::userAllocMultiRowBuffers` oznacza, że zostanie przydzielone.

Poniższa tabela zawiera listę funkcji Członkowskich udostępnianych przez `CRecordset` do obsługi pobierania wierszy zbiorczych.

|Funkcja członkowska|Opis|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Funkcja wirtualna, która obsługuje wszystkie błędy występujące podczas pobierania.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementuje wymianę pól rekordów zbiorczych. Wywoływana automatycznie do przesyłania wielu wierszy danych ze źródła danych do obiektu zestawu rekordów.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Pobiera bieżące ustawienie rozmiaru zestawu wierszy.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Informuje o liczbie wierszy, które zostały faktycznie pobrane po wykonaniu danego pobrania. W większości przypadków jest to rozmiar zestawu wierszy, chyba że pobrano niekompletny zestaw wierszy.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Zwraca stan pobierania dla określonego wiersza w zestawie wierszy.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Odświeża dane i stan określonego wiersza w zestawie wierszy.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Przenosi kursor do określonego wiersza w zestawie wierszy.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Funkcja wirtualna, która zmienia ustawienie rozmiaru zestawu wierszy na określoną wartość.|

##  <a name="special-considerations"></a><a name="_core_special_considerations"></a>Uwagi specjalne

Chociaż pobieranie wierszy zbiorczych jest wzrostem wydajności, niektóre funkcje działają inaczej. Przed podjęciem decyzji o zaimplementowaniu pobierania wierszy zbiorczych należy wziąć pod uwagę następujące kwestie:

- Struktura automatycznie wywołuje funkcję elementu członkowskiego `DoBulkFieldExchange`, aby przesłać dane ze źródła danych do obiektu zestawu rekordów. Jednak dane nie są przesyłane z zestawu rekordów z powrotem do źródła danych. Wywołanie funkcji elementów członkowskich `AddNew`, `Edit`, `Delete`lub `Update` powoduje niepowodzenie potwierdzenia. Chociaż `CRecordset` obecnie nie oferuje mechanizmu aktualizowania wierszy danych zbiorczych, można napisać własne funkcje przy użyciu funkcji ODBC API `SQLSetPos`. Aby uzyskać więcej informacji na temat `SQLSetPos`, zobacz *Kompendium zestawu ODBC SDK programisty* w dokumentacji MSDN.

- Funkcji Członkowskich `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`i `SetFieldNull` nie można używać w zestawach rekordów, które implementują pobieranie wierszy zbiorczych. Można jednak wywołać `GetRowStatus` zamiast `IsDeleted`i `GetODBCFieldInfo` zamiast `IsFieldNullable`.

- Operacje `Move` zmieniają położenie zestawu rekordów według zestawu wierszy. Załóżmy na przykład, że otworzysz zestaw rekordów, który ma 100 rekordów o początkowym rozmiarze zestawu wierszy 10. `Open` pobiera wiersze od 1 do 10 z bieżącym rekordem umieszczonym w wierszu 1. Wywołanie `MoveNext` pobiera następny zestaw wierszy, a nie następny wiersz. Ten zestaw wierszy składa się z wierszy od 11 do 20 z bieżącym rekordem umieszczonym w wierszu 11. Należy pamiętać, że `MoveNext` i `Move( 1 )` nie są równoważne, gdy zaimplementowano pobieranie wierszy zbiorczych. `Move( 1 )` Pobiera zestaw wierszy, który rozpoczyna 1 wiersz od bieżącego rekordu. W tym przykładzie wywoływanie `Move( 1 )` po wywołaniu `Open` Pobiera zestaw wierszy składający się z wierszy od 2 do 11, z bieżącym rekordem umieszczonym w wierszu 2. Aby uzyskać więcej informacji, zobacz Funkcja [przenoszenia](../../mfc/reference/crecordset-class.md#move) elementu członkowskiego.

- W przeciwieństwie do wymiany pól rekordów kreatorzy nie obsługują wymiany pól rekordów zbiorczych. Oznacza to, że należy ręcznie zadeklarować elementy członkowskie danych pola i ręcznie przesłonić `DoBulkFieldExchange` przez zapisanie wywołań do funkcji Bulk RFX. Aby uzyskać więcej informacji, zobacz [Rejestrowanie funkcji wymiany pól](../../mfc/reference/record-field-exchange-functions.md) w *dokumentacji biblioteki klas*.

##  <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>Jak zaimplementować wymianę pól rekordów zbiorczych

Wymiana pól rekordów zbiorczych przenosi zestaw wierszy danych ze źródła danych do obiektu recordset. Funkcje Bulk RFX używają tablic do przechowywania tych danych, a także tablic do przechowywania długości każdego elementu danych w zestawie wierszy. W definicji klasy należy zdefiniować elementy członkowskie danych pola jako wskaźniki umożliwiające dostęp do tablic danych. Ponadto należy zdefiniować zestaw wskaźników, aby uzyskać dostęp do tablic długości. Wszystkie elementy członkowskie danych parametrów nie powinny być deklarowane jako wskaźniki; Deklarowanie elementów członkowskich danych podczas korzystania z wymiany pól rekordów zbiorczych jest taka sama jak deklarująca je podczas korzystania z wymiany pól rekordów. Poniższy kod przedstawia prosty przykład:

```cpp
class MultiRowSet : public CRecordset
{
public:
   // Field/Param Data
      // field data members
      long* m_rgID;
      LPSTR m_rgName;

      // pointers for the lengths
      // of the field data
      long* m_rgIDLengths;
      long* m_rgNameLengths;

      // input parameter data member
      CString m_strNameParam;

   .
   .
   .
}
```

Te bufory magazynu można przydzielić ręcznie lub w ramach alokacji. Aby samodzielnie przydzielić bufory, należy określić opcję `CRecordset::userAllocMultiRowBuffers` parametru *dwOptions* w funkcji członkowskiej `Open`. Pamiętaj, aby ustawić rozmiary tablic co najmniej równe rozmiarowi zestawu wierszy. Jeśli chcesz, aby struktura wykonał alokację, należy zainicjować wskaźniki do wartości NULL. Zwykle jest to wykonywane w konstruktorze obiektu zestawu rekordów:

```cpp
MultiRowSet::MultiRowSet( CDatabase* pDB )
   : CRecordset( pDB )
{
   m_rgID = NULL;
   m_rgName = NULL;
   m_rgIDLengths = NULL;
   m_rgNameLengths = NULL;
   m_strNameParam = "";

   m_nFields = 2;
   m_nParams = 1;

   .
   .
   .
}
```

Na koniec należy zastąpić funkcję elementu członkowskiego `DoBulkFieldExchange`. Dla elementów członkowskich danych pola Wywołaj funkcje RFX zbiorczych; dla dowolnego elementu członkowskiego danych, wywołaj funkcje RFX. Jeśli zestaw rekordów został otwarty przez przekazanie instrukcji SQL lub procedury składowanej do `Open`, kolejność wykonywania wywołań zbiorczych RFX musi odpowiadać kolejności kolumn w zestawie rekordów; Podobnie porządek RFX wywołań parametrów musi odpowiadać kolejności parametrów w instrukcji SQL lub procedurze składowanej.

```cpp
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )
{
   // call the Bulk RFX functions
   // for field data members
   pFX->SetFieldType( CFieldExchange::outputColumn );
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),
                  &m_rgID, &m_rgIDLengths );
   RFX_Text_Bulk( pFX, _T( "[colName]" ),
                  &m_rgName, &m_rgNameLengths, 30 );

   // call the RFX functions for
   // for parameter data members
   pFX->SetFieldType( CFieldExchange::inputParam );
   RFX_Text( pFX, "NameParam", m_strNameParam );
}
```

> [!NOTE]
>  Musisz wywołać funkcję członkowską `Close`, zanim Klasa pochodna `CRecordset` wyjdzie poza zakres. Gwarantuje to, że wszystkie pamięci przydzielone przez platformę zostaną zwolnione. Dobrym sposobem programowania jest zawsze jawne wywołanie `Close`, niezależnie od tego, czy wdrożono pobieranie wierszy zbiorczych.

Aby uzyskać więcej informacji na temat wymiany pól rekordów (RFX), zobacz [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać więcej informacji na temat używania parametrów, zobacz [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) i [Recordset: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset:: m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
