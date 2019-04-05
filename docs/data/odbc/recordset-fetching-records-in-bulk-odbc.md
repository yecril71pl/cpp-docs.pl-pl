---
title: 'Zestaw rekordów: Pobieranie rekordów zbiorcze (ODBC)'
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
ms.openlocfilehash: 2fdcbf18fcb0d97ba7b2a39aa9bbbd79e65a4112
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027769"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Zestaw rekordów: Pobieranie rekordów zbiorcze (ODBC)

Ten temat dotyczy klas MFC ODBC.

Klasa `CRecordset` zapewnia obsługę zbiorcze pobieranie z wiersza, co oznacza, że wiele rekordów można pobrać tylko raz podczas pobierania jednego, a nie podczas pobierania jednego rekordu w danym momencie ze źródła danych. Możesz zaimplementować zbiorcze pobieranie z wiersza tylko w pochodnej `CRecordset` klasy. Proces przesyłania danych ze źródła danych do obiektu zestawu rekordów jest nazywany zbiorcza wymiana pól rekordów (zbiorcze RFX). Należy pamiętać, że jeśli nie używasz zbiorcze pobieranie z wiersza w `CRecordset`-klasy pochodnej, dane są przesyłane za pośrednictwem wymiana pól rekordów (RFX). Aby uzyskać więcej informacji, zobacz [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

W tym temacie opisano:

- [Jak CRecordset obsługuje zbiorcze pobieranie z wiersza](#_core_how_crecordset_supports_bulk_row_fetching).

- [Pewne specjalne zagadnienia dotyczące korzystania z zbiorcze pobieranie z wiersza](#_core_special_considerations).

- [Jak zaimplementować zbiorcza wymiana pól rekordów](#_core_how_to_implement_bulk_record_field_exchange).

##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> Jak CRecordset obsługuje pobieranie z wiersza zbiorcze

Przed otwarciem obiekt zestawu rekordów, można zdefiniować rozmiar wierszy przy użyciu `SetRowsetSize` funkcja elementu członkowskiego. Rozmiar zestawu wierszy Określa, ile rekordy mają zostać pobrane podczas pobierania jednego. Po zaimplementowaniu zbiorcze pobieranie z wiersza domyślny rozmiar wierszy to 25. Jeśli nie jest zaimplementowana zbiorcze pobieranie z wiersza, rozmiar wierszy nie zmienia się na 1.

Po zainicjują rozmiar wierszy, wywołać [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcja elementu członkowskiego. W tym miejscu należy określić `CRecordset::useMultiRowFetch` opcji *dwOptions* parametru, aby zaimplementować zbiorcze pobieranie z wiersza. Ponadto można ustawić `CRecordset::userAllocMultiRowBuffers` opcji. Mechanizm wymiany pól rekordów zbiorcze używa tablic do przechowywania wielu wierszy pobranych podczas pobierania danych. Bufory magazynu można przydzielić automatycznie przez strukturę lub przydzielać je ręcznie. Określanie `CRecordset::userAllocMultiRowBuffers` opcji oznacza, że wykonasz alokacji.

W poniższej tabeli wymieniono funkcje elementów członkowskich, dostarczone przez `CRecordset` do obsługi zbiorcze pobieranie z wiersza.

|Funkcja elementu członkowskiego|Opis|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Funkcja wirtualna, która obsługuje wszystkie błędy, które występują podczas pobierania.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementuje zbiorczo wymiana pól rekordów. Wywołuje się automatycznie z transferami wiele wierszy danych ze źródła danych do obiektu zestawu rekordów.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Pobiera bieżące ustawienie rozmiaru wierszy.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Informuje o tym, ile wierszy rzeczywiście zostały pobrane po pobraniu danego. W większości przypadków jest to rozmiar zestawu wierszy, chyba że pobrano wierszy niekompletne.|
|[Getrowstatus —](../../mfc/reference/crecordset-class.md#getrowstatus)|Zwraca stan pobierania dla danego wiersza w zestawie wierszy.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Odświeża dane i stan określonego wiersza w zestawie wierszy.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Przenosi kursor do określonego wiersza w zestawie wierszy.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Funkcja wirtualna, która zmienia ustawienie rozmiaru wierszy z podaną wartością.|

##  <a name="_core_special_considerations"></a> Specjalne uwagi

Mimo że zbiorcze pobieranie z wiersza jest bardziej wydajne, niektóre funkcje działają inaczej. Przed podjęciem decyzji o implementacji zbiorcze pobieranie z wiersza, należy wziąć pod uwagę następujące informacje:

- Struktura automatycznie wywołuje `DoBulkFieldExchange` funkcja elementu członkowskiego na przesyłanie danych ze źródła danych do obiektu zestawu rekordów. Jednak dane nie są przesyłane z zestawu rekordów do źródła danych. Wywoływanie `AddNew`, `Edit`, `Delete`, lub `Update` wyniki funkcji elementu członkowskiego w potwierdzenie nie powiodło się. Mimo że `CRecordset` aktualnie nie zapewnia mechanizm aktualizacji zbiorczej wiersze danych, można napisać własne funkcje za pomocą funkcji interfejsu API ODBC `SQLSetPos`. Aby uzyskać więcej informacji na temat `SQLSetPos`, zobacz *ODBC SDK Podręcznik programisty* w dokumentacji MSDN.

- Funkcje elementów członkowskich `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`, i `SetFieldNull` nie można używać w zestawach rekordów, który implementuje zbiorcze pobieranie z wiersza. Jednak można wywoływać `GetRowStatus` zamiast `IsDeleted`, i `GetODBCFieldInfo` zamiast `IsFieldNullable`.

- `Move` Operacje powoduje przeniesienie rekordów w zestawie wierszy. Na przykład załóżmy, że możesz otworzyć zestaw rekordów, które ma 100 rekordów o rozmiarze 10 początkowego zestawu wierszy. `Open` Pobiera wiersze od 1 do 10 z bieżącym rekordem umieszczony w wierszu 1. Wywołanie `MoveNext` pobierze następny zestaw wierszy nie następnego wiersza. Ten zestaw wierszy składa się z wierszach od 11 do 20 z bieżącym rekordem umieszczony w wierszu 11. Należy pamiętać, że `MoveNext` i `Move( 1 )` nie są równoważne, gdy zbiorcze pobieranie z wiersza jest zaimplementowana. `Move( 1 )` Pobiera zestaw wierszy, który rozpoczyna się 1 wiersz z bieżącego rekordu. W tym przykładzie wywołanie `Move( 1 )` po wywołaniu `Open` pobiera wierszy składający się z wierszy od 2 do 11 z bieżącym rekordem umieszczony w wierszu 2. Aby uzyskać więcej informacji, zobacz [przenieść](../../mfc/reference/crecordset-class.md#move) funkcja elementu członkowskiego.

- W odróżnieniu od wymiana pól rekordów kreatorów nie obsługują zbiorcza wymiana pól rekordów. Oznacza to, należy ręcznie zadeklarować swoje elementy członkowskie danych pola i ręcznie przezwyciężyć `DoBulkFieldExchange` , pisząc wywołania funkcji zbiorcze RFX. Aby uzyskać więcej informacji, zobacz [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md) w *odwołanie do biblioteki klas*.

##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> Jak zaimplementować wymiana pól rekordów zbiorcze

Zbiorcza wymiana pól rekordów przesyła zestawu wierszy danych ze źródła danych do obiektu zestawu rekordów. Funkcje zbiorcze RFX używać tablic do przechowywania danych, a także tablic do przechowywania długość każdego elementu danych w zestawie wierszy. W definicji klasy należy zdefiniować swoje elementy członkowskie danych pola jako wskaźniki do tablic danych dostęp. Ponadto należy zdefiniować zestaw wskaźniki do tablic o długości dostępu. Wszystkie elementy członkowskie danych parametru nie powinien być deklarowany jako wskaźniki; deklarowanie elementy członkowskie danych parametru w przypadku korzystania z zbiorcza wymiana pól rekordów jest taka sama jak deklarowanie je, korzystając z wymiana pól rekordów. Poniższy kod pokazuje prosty przykład:

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

Możesz przydzielić bufory magazynu ręcznie lub mieć platformę, czy przydział. Aby przydzielić bufory samodzielnie, należy określić `CRecordset::userAllocMultiRowBuffers` opcji *dwOptions* parametru w `Open` funkcja elementu członkowskiego. Należy ustawić co najmniej równa rozmiarowi wierszy rozmiary tablic. Jeśli chcesz mieć platformę, czy przydział, należy zainicjować wskaźniki do wartości NULL. Zazwyczaj jest to wykonywane w Konstruktorze obiektu zestaw rekordów:

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

Ponadto konieczne jest przesłonięcie `DoBulkFieldExchange` funkcja elementu członkowskiego. Elementy członkowskie danych pola można wywołać w funkcji zbiorcze RFX; wszystkie elementy członkowskie danych parametru można wywołać w funkcji RFX. Jeśli zestaw rekordów został otwarty przez przekazanie instrukcji SQL lub procedurę przechowywaną, aby `Open`, kolejność, w którym możesz wykonywać wywołania zbiorcze RFX musi odpowiadać kolejności kolumn w zestawie rekordów; podobnie kolejność RFX wywołuje dla parametrów musi odpowiadać. polecenie parametry w instrukcji SQL lub procedury składowanej.

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
>  Należy wywołać `Close` funkcji składowej przed swoje pochodnej `CRecordset` klasy wykracza poza zakres. Daje to gwarancję, że wszystkie pamięci przydzielonej przez platformę są zwalniane. Jest dobrą praktyką, aby zawsze jawnie wywołać programowania `Close`, niezależnie od tego, czy udało Ci się wdrożyć zbiorcze pobieranie z wiersza.

Aby uzyskać więcej informacji na temat wymiana pól rekordów (RFX), zobacz [wymiana pól rekordów: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać więcej informacji o korzystaniu z parametrów, zobacz [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) i [zestaw rekordów: Parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Zobacz także

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

