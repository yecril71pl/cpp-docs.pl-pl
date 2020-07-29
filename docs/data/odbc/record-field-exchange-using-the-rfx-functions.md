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
ms.openlocfilehash: 4d621fbe2207114dd51845b819d309802a009690
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216534"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Wymiana pól rekordów: używanie funkcji RFX

W tym temacie wyjaśniono, jak używać wywołań funkcji RFX, które tworzą treść `DoFieldExchange` przesłonięcia.

> [!NOTE]
> Ten temat dotyczy klas pochodnych [CRecordset](../../mfc/reference/crecordset-class.md) , w których nie zaimplementowano pobierania wierszy zbiorczych. W przypadku korzystania z pobierania wierszy zbiorczych zaimplementowano wymianę zbiorczych pól rekordów (bulk RFX). RFX Bulk jest podobna do RFX. Aby zrozumieć różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Funkcje globalne RFX wymieniają dane między kolumnami w elementach członkowskich danych źródła danych i pól w zestawie rekordów. Należy napisać wywołania funkcji RFX w funkcji członkowskiej [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) zestawu rekordów. W tym temacie opisano krótko funkcje i przedstawiono typy danych, dla których dostępne są funkcje RFX. [Uwaga techniczna 43](../../mfc/tn043-rfx-routines.md) opisuje sposób pisania własnych funkcji RFX dla dodatkowych typów danych.

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>Składnia funkcji RFX

Każda funkcja RFX przyjmuje trzy parametry (a kilka z nich przyjmuje opcjonalny, czwarty lub piąty parametr):

- Wskaźnik do obiektu [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . Wystarczy przekazać `pFX` wskaźnik do `DoFieldExchange` .

- Nazwa kolumny wyświetlanej w źródle danych.

- Nazwa odpowiedniego elementu członkowskiego danych lub parametru elementu członkowskiego danych w klasie zestawu rekordów.

- Obowiązkowe W niektórych funkcjach Maksymalna długość transferowanego ciągu lub tablicy. Wartość domyślna to 255 bajtów, ale można ją zmienić. Maksymalny rozmiar jest określany na podstawie maksymalnego rozmiaru `CString` obiektu — **INT_MAX** (2 147 483 647), ale prawdopodobnie napotkasz limity sterowników przed tym rozmiarem.

- Obowiązkowe W `RFX_Text` funkcji należy czasami użyć piątego parametru, aby określić typ danych kolumny.

Aby uzyskać więcej informacji, zobacz funkcje RFX w obszarze [MACROS i Globals](../../mfc/reference/mfc-macros-and-globals.md) w *bibliotece klas Reference*. Aby zapoznać się z przykładem sytuacji, w której można zastosować specjalne parametry, zobacz [zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>RFX — typy danych

Biblioteka klas udostępnia funkcje RFX do przesyłania wielu różnych typów danych między źródłem danych i zestawami rekordów. Poniższa lista zawiera podsumowanie funkcji RFX według typu danych. W przypadkach, w których należy napisać własne wywołania funkcji RFX, należy wybrać jedną z tych funkcji według typu danych.

|Funkcja|Typ danych|
|--------------|---------------|
|`RFX_Bool`|**LOGICZNA**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**`double`**|
|`RFX_Single`|**`float`**|
|`RFX_Int`|**`int`**|
|`RFX_Long`|**`long`**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Aby uzyskać więcej informacji, zobacz dokumentację funkcji RFX w obszarze [MACROS i Globals](../../mfc/reference/mfc-macros-and-globals.md) w *bibliotece klas Reference*. Aby uzyskać informacje o tym, jak typy danych C++ są mapowane na typy danych SQL, zobacz Typy danych SQL ANSI zamapowane na typy danych języka C++ w [języku SQL: SQL i c++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Zobacz także

[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Zestaw rekordów: parametryzacja a zestaw rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Zestaw rekordów: dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)
