---
title: 'Wymiana pól rekordów: używanie funkcji RFX'
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
ms.openlocfilehash: d281f801349527a065f4975b7cc3d88888f88367
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213034"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Wymiana pól rekordów: używanie funkcji RFX

W tym temacie wyjaśniono, jak używać wywołań funkcji RFX, które tworzą treść przesłonięcia `DoFieldExchange`.

> [!NOTE]
>  Ten temat dotyczy klas pochodnych [CRecordset](../../mfc/reference/crecordset-class.md) , w których nie zaimplementowano pobierania wierszy zbiorczych. W przypadku korzystania z pobierania wierszy zbiorczych zaimplementowano wymianę zbiorczych pól rekordów (bulk RFX). RFX Bulk jest podobna do RFX. Aby zrozumieć różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Funkcje globalne RFX wymieniają dane między kolumnami w elementach członkowskich danych źródła danych i pól w zestawie rekordów. Należy napisać wywołania funkcji RFX w funkcji członkowskiej [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) zestawu rekordów. W tym temacie opisano krótko funkcje i przedstawiono typy danych, dla których dostępne są funkcje RFX. [Uwaga techniczna 43](../../mfc/tn043-rfx-routines.md) opisuje sposób pisania własnych funkcji RFX dla dodatkowych typów danych.

##  <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>Składnia funkcji RFX

Każda funkcja RFX przyjmuje trzy parametry (a kilka z nich przyjmuje opcjonalny, czwarty lub piąty parametr):

- Wskaźnik do obiektu [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . Po prostu przekazujesz wskaźnik `pFX` przekazany do `DoFieldExchange`.

- Nazwa kolumny wyświetlanej w źródle danych.

- Nazwa odpowiedniego elementu członkowskiego danych lub parametru elementu członkowskiego danych w klasie zestawu rekordów.

- Obowiązkowe W niektórych funkcjach Maksymalna długość transferowanego ciągu lub tablicy. Wartość domyślna to 255 bajtów, ale można ją zmienić. Maksymalny rozmiar jest określany na podstawie maksymalnego rozmiaru `CString` obiektu — **INT_MAX** (2 147 483 647) b — ale prawdopodobnie napotkasz limity sterowników przed tym rozmiarem.

- Obowiązkowe W funkcji `RFX_Text` czasami używasz piątego parametru, aby określić typ danych kolumny.

Aby uzyskać więcej informacji, zobacz funkcje RFX w obszarze [MACROS i Globals](../../mfc/reference/mfc-macros-and-globals.md) w *bibliotece klas Reference*. Aby zapoznać się z przykładem sytuacji, w której można zastosować specjalne parametry, zobacz [zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

##  <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>RFX — typy danych

Biblioteka klas udostępnia funkcje RFX do przesyłania wielu różnych typów danych między źródłem danych i zestawami rekordów. Poniższa lista zawiera podsumowanie funkcji RFX według typu danych. W przypadkach, w których należy napisać własne wywołania funkcji RFX, należy wybrać jedną z tych funkcji według typu danych.

|Funkcja|Typ danych|
|--------------|---------------|
|`RFX_Bool`|**LOGICZNA**|
|`RFX_Byte`|**BAJC**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Aby uzyskać więcej informacji, zobacz dokumentację funkcji RFX w obszarze [MACROS i Globals](../../mfc/reference/mfc-macros-and-globals.md) w *bibliotece klas Reference*. Aby uzyskać informacje na C++ temat sposobu mapowania typów danych na typy danych SQL, zobacz Typy danych SQL ANSI zamapowane C++ na typy danych w [języku SQL: C++ SQL i typy danych (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Zobacz też

[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)
