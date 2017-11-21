---
title: "Zestaw rekordów: Zbiorcze pobieranie rekordów (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c0eff5528d2b612fbeab4511f64341975791f3e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Zestaw rekordów: zbiorcze pobieranie rekordów (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 Klasa `CRecordset` zapewnia obsługę zbiorcze pobieranie z wiersza, co oznacza, że wiele rekordów można pobrać jednocześnie podczas pobierania pojedynczego zamiast pobierania jeden rekord jednocześnie ze źródła danych. Zbiorcze pobieranie z wiersza tylko w pochodnej można zaimplementować `CRecordset` klasy. Proces transferowania danych ze źródła danych do obiektu zestawu rekordów jest nazywany zbiorcza wymiana pól rekordów (RFX zbiorczego). Należy pamiętać, że jeśli nie używasz zbiorcze pobieranie z wiersza w `CRecordset`-klasy pochodnej, dane są przesyłane za pośrednictwem wymiana pól rekordów (RFX). Aby uzyskać więcej informacji, zobacz [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
 W tym temacie opisano:  
  
-   [Jak crecordset — obsługuje zbiorcze pobieranie z wiersza](#_core_how_crecordset_supports_bulk_row_fetching).  
  
-   [Niektóre szczególne zagadnienia dotyczące używania zbiorcze pobieranie z wiersza](#_core_special_considerations).  
  
-   [Jak zaimplementować zbiorcza wymiana pól rekordów](#_core_how_to_implement_bulk_record_field_exchange).  
  
##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Jak crecordset — obsługuje pobieranie z wiersza zbiorczego  
 Przed otwarciem obiektu zestawu rekordów, można zdefiniować rozmiar wierszy z `SetRowsetSize` funkcję elementu członkowskiego. Rozmiar zestawu wierszy określa liczbę rekordów powinny zostać pobrane podczas jednego pobierania. Po zaimplementowaniu zbiorcze pobieranie z wiersza domyślny rozmiar wierszy wynosi 25. Jeśli zbiorcze pobieranie z wiersza nie jest zaimplementowana, rozmiar zestawu wierszy nie zmienia się na 1.  
  
 Po już zainicjować rozmiar zestawu wierszy, wywołać [Otwórz](../../mfc/reference/crecordset-class.md#open) funkcję elementu członkowskiego. W tym miejscu należy określić `CRecordset::useMultiRowFetch` opcji **dwOptions** parametru do zaimplementowania zbiorcze pobieranie z wiersza. Ponadto można ustawić **CRecordset::userAllocMultiRowBuffers** opcji. Mechanizm wymiany pól rekordów zbiorczego przechowuje tablice wiele wierszy pobranych podczas pobierania danych. Bufory magazynu mogą być automatycznie przydzielone przez platformę, lub można je przydzielić ręcznie. Określanie **CRecordset::userAllocMultiRowBuffers** opcja oznacza wykona alokacji.  
  
 W poniższej tabeli wymieniono funkcje Członkowskie udostępniane przez `CRecordset` do obsługi zbiorcze pobieranie z wiersza.  
  
|Funkcja członkowska|Opis|  
|---------------------|-----------------|  
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Funkcja wirtualna obsługi błędów występujących podczas pobierania.|  
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementuje zbiorcze wymiana pól rekordów. Wywoływana automatycznie do transferów wiele wierszy danych ze źródła danych do obiektu zestawu rekordów.|  
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Pobiera bieżące ustawienie rozmiaru zestawu wierszy.|  
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Informuje, ile wierszy rzeczywiście zostały pobrane po pobraniu danego. W większości przypadków jest to rozmiar zestawu wierszy, chyba że pobrano niekompletne zestawu wierszy.|  
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Zwraca stan pobierania dla danego wiersza w zestawie wierszy.|  
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Odświeża dane i stan określonego wiersza w zestawie wierszy.|  
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Przesuwa kursor do określonego wiersza w zestawie wierszy.|  
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Funkcja wirtualna zmienia ustawienie rozmiaru wierszy z podaną wartością.|  
  
##  <a name="_core_special_considerations"></a>Uwagi  
 Zbiorcze pobieranie z wiersza jest bardziej wydajne, niektóre funkcje działają inaczej. Przed podjęciem decyzji o implementacji zbiorcze pobieranie z wiersza, należy rozważyć następujące kwestie:  
  
-   Struktura automatycznie wywołuje `DoBulkFieldExchange` funkcji członkowskiej na przesyłanie danych ze źródła danych do obiektu zestawu rekordów. Jednak dane nie są przesyłane w zestawie do źródła danych. Wywoływanie `AddNew`, **Edytuj**, **usunąć**, lub **aktualizacji** powoduje funkcje Członkowskie potwierdzenia nie powiodło się. Mimo że `CRecordset` aktualnie nie zapewnia mechanizm aktualizacji zbiorczej wiersze danych, można zapisać własnych funkcji przy użyciu funkcji interfejsu API ODBC **SQLSetPos**. Aby uzyskać więcej informacji na temat **SQLSetPos**, zobacz *ODBC SDK Podręcznik programisty* w dokumentacji MSDN.  
  
-   Funkcje Członkowskie `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`, i `SetFieldNull` nie można używać dla zestawów rekordów, który implementuje zbiorcze pobieranie z wiersza. Jednak możesz wywołać `GetRowStatus` zamiast `IsDeleted`, i `GetODBCFieldInfo` zamiast `IsFieldNullable`.  
  
-   **Przenieś** operacji zmiana zestawu rekordów w zestawie wierszy. Na przykład załóżmy, że Otwórz zestaw rekordów, który ma 100 rekordów o rozmiarze 10 początkowego zestawu wierszy. **Otwórz** pobiera wiersze od 1 do 10, z bieżącym rekordem znajduje się w wierszu 1. Wywołanie `MoveNext` pobiera dalej zestawu wierszy nie następnego wiersza. Ten zestaw wierszy składa się z wierszy 11 do 20 z bieżącym rekordem znajduje się w wierszu 11. Należy pamiętać, że `MoveNext` i **przenieść (1)** nie są równoważne po zaimplementowaniu zbiorcze pobieranie z wiersza. **Przenieś (1)** pobiera zestawu wierszy, który rozpoczyna się 1 wiersz z bieżącego rekordu. W tym przykładzie wywołanie **przenieść (1)** po wywołaniu **Otwórz** pobiera wierszy składający się z wierszy od 2 do 11, z bieżącym rekordem znajduje się w wierszu 2. Aby uzyskać więcej informacji, zobacz [Przenieś](../../mfc/reference/crecordset-class.md#move) funkcję elementu członkowskiego.  
  
-   W odróżnieniu od wymiana pól rekordów kreatorów nie obsługują zbiorcza wymiana pól rekordów. Oznacza to, należy ręcznie zadeklarować użytkownika elementy członkowskie danych pola i ręczne zastąpienie `DoBulkFieldExchange` pisząc wywołania funkcji RFX zbiorczego. Aby uzyskać więcej informacji, zobacz [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md) w *informacje dotyczące biblioteki klas*.  
  
##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a>Jak zaimplementować zbiorcza wymiana pól rekordów  
 Zbiorcza wymiana pól rekordów przesyła zestawu wierszy danych ze źródła danych do obiektu zestawu rekordów. Funkcje zbiorczej wymiany RFX używają tablic do przechowywania tych danych, a także tablic do przechowywania długość każdego elementu danych w zestawie wierszy. W definicji klasy należy zdefiniować jako wskaźniki do tablic danych użytkownika elementy członkowskie danych pola. Ponadto należy zdefiniować zestaw wskaźniki do tablic o długości. Wszystkie elementy członkowskie danych parametru nie powinien być zadeklarowany jako wskaźników; deklarowanie elementy członkowskie danych parametru w przypadku korzystania z zbiorcza wymiana pól rekordów jest taka sama jak deklarowanie je, korzystając z wymiana pól rekordów. Poniższy kod przedstawia prosty przykład:  
  
```  
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
  
 Można ręcznie przydzielić bufory magazynu lub mieć framework czy alokacji. Aby przydzielić buforów samodzielnie, należy określić **CRecordset::userAllocMultiRowBuffers** opcji **dwOptions** parametru w **Otwórz** funkcji członkowskiej. Należy ustawić co najmniej równa rozmiarowi wierszy rozmiary tablic. Jeśli chcesz mieć framework, czy przydział, należy zainicjować wskaźniki do **wartości NULL.** Jest to zazwyczaj wykonywane w Konstruktorze obiektu zestaw rekordów:  
  
```  
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
  
 Na koniec należy zastąpić `DoBulkFieldExchange` funkcję elementu członkowskiego. Elementy członkowskie danych pola można wywołać w funkcje zbiorczej wymiany RFX; dla żadnych elementów członkowskich danych parametru wywołania funkcji RFX. Jeśli zestaw rekordów jest otwarty przez przekazanie instrukcję SQL lub procedurę składowaną do **Otwórz**, kolejność, w którym można wykonywać wywołania RFX zbiorczego musi odpowiadać kolejności kolumn w zestawie rekordów; podobnie wymaga kolejność RFX Parametry muszą odpowiadać kolejności parametrów w instrukcji SQL lub procedurę składowaną.  
  
```  
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
>  Należy wywołać **Zamknij** funkcji członkowskiej przed Twojej pochodnej `CRecordset` klasy wykracza poza zakres. Dzięki temu, że są zwalniane wszystkie pamięci przydzielonej przez platformę. Jest dobrą praktyką jest zawsze jawnie wywołać programowania **Zamknij**, niezależnie od tego, czy zostały zaimplementowane zbiorcze pobieranie z wiersza.  
  
 Aby uzyskać więcej informacji na temat wymiana pól rekordów (RFX), zobacz [wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Aby uzyskać więcej informacji na temat użycia parametrów, zobacz [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) i [zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)   
 [CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

