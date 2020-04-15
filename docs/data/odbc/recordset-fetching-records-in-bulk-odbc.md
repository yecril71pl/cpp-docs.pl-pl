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
ms.openlocfilehash: ec4d83481f6335d4c40ffb8f004b617f2ee09c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367030"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Zestaw rekordów: zbiorcze pobieranie rekordów (ODBC)

Ten temat dotyczy klas MFC ODBC.

Klasa `CRecordset` zapewnia obsługę pobierania wiersza zbiorczego, co oznacza, że wiele rekordów można pobrać jednocześnie podczas pojedynczego pobierania, zamiast pobierać jeden rekord naraz ze źródła danych. Pobieranie wiersza zbiorczego można zaimplementować tylko w `CRecordset` klasie pochodnej. Proces przesyłania danych ze źródła danych do obiektu zestaw rekordów jest nazywany zbiorczą wymianą pól rekordów (Bulk RFX). Należy zauważyć, że jeśli nie używasz `CRecordset`zbiorczego pobierania wierszy w klasie pochodnej, dane są przesyłane za pośrednictwem wymiany pól rekordu (RFX). Aby uzyskać więcej informacji, zobacz [Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

W tym temacie wyjaśniono:

- [Jak CRecordset obsługuje pobieranie wierszy zbiorczych](#_core_how_crecordset_supports_bulk_row_fetching).

- [Niektóre szczególne uwagi podczas korzystania z pobierania wiersza luzem](#_core_special_considerations).

- [Jak zaimplementować zbiorczą wymianę pól rekordów](#_core_how_to_implement_bulk_record_field_exchange).

## <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Jak CRecordset obsługuje pobieranie wierszy zbiorczych

Przed otwarciem obiektu zestawu rekordów można zdefiniować `SetRowsetSize` rozmiar zestawu wierszy za pomocą funkcji elementu członkowskiego. Rozmiar zestawu wierszy określa, ile rekordów należy pobrać podczas pojedynczego pobierania. Po zaimplementowaniu pobierania wiersza zbiorczego domyślny rozmiar zestawu wierszy wynosi 25. Jeśli pobieranie wiersza zbiorczego nie jest implementowane, rozmiar zestawu wierszy pozostaje stały na 1.

Po zainicjowaniu rozmiaru zestawu wierszy wywołaj funkcję [Otwórz](../../mfc/reference/crecordset-class.md#open) element członkowski. W tym miejscu `CRecordset::useMultiRowFetch` należy określić opcję *dwOptions* parametru do zaimplementowania pobierania wiersza zbiorczego. Można dodatkowo ustawić `CRecordset::userAllocMultiRowBuffers` tę opcję. Mechanizm zbiorczej wymiany pól rekordów używa tablic do przechowywania wielu wierszy danych pobranych podczas pobierania. Te bufory magazynu mogą być przydzielane automatycznie przez platformę lub można je przydzielić ręcznie. Określenie `CRecordset::userAllocMultiRowBuffers` opcji oznacza, że wykonasz alokację.

W poniższej tabeli wymieniono funkcje członkowskie udostępniane przez `CRecordset` do obsługi pobierania wiersza zbiorczego.

|Funkcja członkowce|Opis|
|---------------------|-----------------|
|[Sprawdź RachowanieError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Funkcja wirtualna, która obsługuje wszelkie błędy, które występują podczas pobierania.|
|[Dobulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementuje zbiorczą wymianę pól rekordów. Wywoływana automatycznie do przesyłania wielu wierszy danych ze źródła danych do obiektu zestaw rekordów.|
|[Rozmiar zestawu GetRowsetsize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Pobiera bieżące ustawienie rozmiaru zestawu wierszy.|
|[GetRowsFetched (GetRowsFetched)](../../mfc/reference/crecordset-class.md#getrowsfetched)|Informuje, ile wierszy zostało faktycznie pobranych po danym pobraniu. W większości przypadków jest to rozmiar zestawu wierszy, chyba że pobrano niekompletny zestaw wierszy.|
|[Stan GetRow](../../mfc/reference/crecordset-class.md#getrowstatus)|Zwraca stan pobierania dla określonego wiersza w zestawie wierszy.|
|[Zestaw RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Odświeża dane i stan określonego wiersza w zestawie wierszy.|
|[Pozycja SetRowsetCursor](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Przenosi kursor do określonego wiersza w obrębie zestawu wierszy.|
|[Rozmiar zestawu SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Funkcja wirtualna, która zmienia ustawienie rozmiaru zestawu wierszy na określoną wartość.|

## <a name="special-considerations"></a><a name="_core_special_considerations"></a>Uwagi specjalne

Chociaż pobieranie wiersza zbiorczego jest przyrost wydajności, niektóre funkcje działają inaczej. Przed podjęciem decyzji o zaimplementowaniu pobierania wiersza zbiorczego należy wziąć pod uwagę następujące kwestie:

- Struktura automatycznie wywołuje `DoBulkFieldExchange` funkcję elementu członkowskiego, aby przenieść dane ze źródła danych do obiektu zestaw rekordów. Jednak dane nie są przesyłane z zestawu rekordów z powrotem do źródła danych. Wywołanie `AddNew` `Edit`funkcji `Delete`, `Update` , lub elementu członkowskiego powoduje niepowodzenie potwierdzenia. Chociaż `CRecordset` obecnie nie zapewnia mechanizmu aktualizowania zbiorczych wierszy danych, można zapisywać własne `SQLSetPos`funkcje za pomocą funkcji INTERFEJSU API ODBC . Aby uzyskać `SQLSetPos`więcej informacji na temat programu , zobacz *odwołanie programisty SDK ODBC* w dokumentacji MSDN.

- Funkcje `IsDeleted`członkowskie `IsFieldDirty` `IsFieldNull`, `IsFieldNullable` `SetFieldDirty`, `SetFieldNull` , , i nie mogą być używane w grupach rekordów, które implementują pobieranie wiersza zbiorczego. `GetRowStatus` Można jednak dzwonić zamiast `IsDeleted`i `GetODBCFieldInfo` zamiast `IsFieldNullable`.

- Operacje `Move` zmienia położenie zestawu rekordów według zestawu wierszy. Załóżmy na przykład, że otwierasz zestaw rekordów, który ma 100 rekordów o początkowym rozmiarze zestawu wierszy 10. `Open`pobiera wiersze od 1 do 10, z bieżącym rekordem umieszczonym w wierszu 1. Wywołanie `MoveNext` pobierania następnego zestawu wierszy, a nie następnego wiersza. Ten zestaw wierszy składa się z wierszy od 11 do 20, z bieżącym rekordem umieszczonym w wierszu 11. Należy `MoveNext` zauważyć, że i `Move( 1 )` nie są równoważne, gdy zaimplementowano pobieranie wiersza zbiorczego. `Move( 1 )`pobiera zestaw wierszy, który rozpoczyna się od 1 wiersza od bieżącego rekordu. W tym przykładzie `Move( 1 )` `Open` wywołanie po wywołaniu pobiera zestaw wierszy składający się z wierszy od 2 do 11, z bieżącym rekordem umieszczonym w wierszu 2. Aby uzyskać więcej informacji, zobacz Move [element](../../mfc/reference/crecordset-class.md#move) członkowski funkcji.

- W przeciwieństwie do wymiany pól rekordów kreatorzy nie obsługują zbiorczej wymiany pól rekordów. Oznacza to, że należy ręcznie zadeklarować elementy członkowskie `DoBulkFieldExchange` danych pola i ręcznie zastąpić, zapisując wywołania do funkcji RFX luzem. Aby uzyskać więcej informacji, zobacz [Rejestrowanie funkcji wymiany pól](../../mfc/reference/record-field-exchange-functions.md) w *odwołaniu do biblioteki klas*.

## <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>Jak zaimplementować zbiorczą wymianę pól rekordów

Zbiorcza wymiana pól rekordów przenosi zestaw wierszy danych ze źródła danych do obiektu zestawu rekordów. Funkcje RFX zbiorcze używają tablic do przechowywania tych danych, a także tablic do przechowywania długości każdego elementu danych w zestawie wierszy. W definicji klasy należy zdefiniować elementy członkowskie danych pola jako wskaźniki, aby uzyskać dostęp do tablic danych. Ponadto należy zdefiniować zestaw wskaźników, aby uzyskać dostęp do tablic długości. Wszystkie elementy członkowskie danych parametrów nie powinny być zadeklarowane jako wskaźniki; deklarowanie elementów członkowskich danych parametrów podczas korzystania z zbiorczej wymiany pól rekordów jest takie samo jak deklarowanie ich podczas korzystania z wymiany pól rekordów. Poniższy kod przedstawia prosty przykład:

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

Można przydzielić te bufory magazynu ręcznie lub mają struktury do alokacji. Aby samodzielnie przydzielić bufory, `CRecordset::userAllocMultiRowBuffers` należy określić opcję parametru `Open` *dwOptions* w funkcji elementu członkowskiego. Należy ustawić rozmiary tablic co najmniej równe rozmiarze zestawu wierszy. Jeśli chcesz, aby struktura wykonać alokacji, należy zainicjować wskaźniki do null. Zazwyczaj odbywa się to w konstruktorze obiektu recordset:

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

Na koniec należy zastąpić funkcję `DoBulkFieldExchange` elementu członkowskiego. W przypadku elementów członkowskich danych pól wywołaj funkcje zbiorczego RFX; dla dowolnych elementów członkowskich danych parametrów, wywołaj funkcje RFX. Jeśli otworzysz zestawie rekordów, przekazując instrukcję SQL lub procedurę składowaną do `Open`, kolejność, w jakiej można wykonać zbiorcze wywołania RFX, musi odpowiadać kolejności kolumn w zestawie rekordów; podobnie kolejność wywołań RFX dla parametrów musi odpowiadać kolejności parametrów w instrukcji SQL lub procedurze składowanej.

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
> Należy wywołać `Close` funkcję elementu członkowskiego, zanim klasa pochodna `CRecordset` wykracza poza zakres. Gwarantuje to, że wszystkie pamięci przydzielone przez strukturę są zwalniane. Jest dobrą praktyką programowania zawsze `Close`jawnie wywołać, niezależnie od tego, czy zostały zaimplementowane pobieranie wiersza zbiorczego.

Aby uzyskać więcej informacji na temat wymiany pól rekordów (RFX), zobacz [Wymiana pól rekordów: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać więcej informacji na temat używania parametrów, zobacz [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) i [Recordset: Parametrizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
