---
title: 'Wymiana pól rekordów: Używanie funkcji RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: dc717336a5279e7eda1b7c39b19a7c76f9055cd3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035987"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Wymiana pól rekordów: Używanie funkcji RFX

W tym temacie wyjaśniono, jak używać wywołania funkcji RFX, które tworzą treści swoje `DoFieldExchange` zastąpienia.

> [!NOTE]
>  Ten temat dotyczy klasy pochodne [CRecordset](../../mfc/reference/crecordset-class.md) w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza zbiorcza wymiana pól rekordów (zbiorcze RFX) jest zaimplementowana. Zbiorcze RFX przypomina RFX. Aby poznać różnice, zobacz [zestaw rekordów: Pobieranie rekordów (ODBC) zbiorcze](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Funkcje globalne RFX wymianę danych między kolumnami na źródłowym i pola danych elementów członkowskich danych w twoim zestawie rekordów. Pisania funkcji RFX wywołuje w twoim zestawie rekordów [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcja elementu członkowskiego. Ten temat krótko opisano funkcje i zawiera typy danych, dla których RFX funkcje są dostępne. [Techniczne 43 Uwaga](../../mfc/tn043-rfx-routines.md) w tym artykule opisano jak napisać własne funkcje RFX dla dodatkowe typy danych.

##  <a name="_core_rfx_function_syntax"></a> Składnia funkcji RFX

Każda funkcja RFX przyjmuje trzy parametry (natomiast niektóre czwartym lub piątym parametr opcjonalny):

- Wskaźnik do [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiektu. Po prostu przekazują `pFX` wskaźnik przekazywany do `DoFieldExchange`.

- Nazwa kolumny w postaci, w jakiej pojawia się w źródle danych.

- Nazwa pola odpowiedni element członkowski danych lub element członkowski danych parametru w klasie zestawu rekordów.

- (Opcjonalnie) W niektórych funkcji, maksymalna długość ciągu lub tablicy przesyłane. Domyślnie jest to 255 bajtów, ale możesz chcieć ją zmienić. Maksymalny rozmiar opiera się na maksymalny rozmiar `CString` obiektu — **INT_MAX** bajtów (2 147 483 647) —, ale prawdopodobnie będą napotykać limity sterowników przed tym rozmiarze.

- (Opcjonalnie) W `RFX_Text` funkcji, czasami piątego parametru do określenia używasz typu danych kolumny.

Aby uzyskać więcej informacji, zapoznaj się z funkcjami RFX w obszarze [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołanie do biblioteki klas*. Na przykład gdy można wprowadzać specjalne użycia parametrów, zobacz artykuł [zestaw rekordów: Uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

##  <a name="_core_rfx_data_types"></a> Typy danych RFX

Biblioteka klas dostarcza funkcje RFX transferu wielu różnych typów danych między źródłem danych i zestawach rekordów. Na poniższej liście podsumowano funkcje RFX przez typ danych. W przypadkach, w którym należy napisać własne wywołania funkcji RFX wybierz z tych funkcji przez typ danych.

|Funkcja|Typ danych|
|--------------|---------------|
|`RFX_Bool`|**WARTOŚĆ LOGICZNA**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|


Aby uzyskać więcej informacji, zobacz dokumentację funkcji RFX w obszarze [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołanie do biblioteki klas*. Aby uzyskać informacji na temat sposobu mapowania typów danych języka C++ na typy danych SQL, zobacz tabeli ANSI SQL danych typy mapowane na typy danych języka C++ w [SQL: Program SQL oraz typów danych języka C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Zobacz także

[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Wymiana pól rekordów: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Zestaw rekordów: Parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Zestaw rekordów: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)