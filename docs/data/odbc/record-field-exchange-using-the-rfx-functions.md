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
ms.openlocfilehash: f1afded360cfeff564f1f3d8bb9b294aa33cb733
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367128"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Wymiana pól rekordów: używanie funkcji RFX

W tym temacie wyjaśniono, jak używać wywołań funkcji `DoFieldExchange` RFX, które tworzą treść zastąpienia.

> [!NOTE]
> Ten temat dotyczy klas pochodzących z [CRecordset,](../../mfc/reference/crecordset-class.md) w którym pobieranie wiersza zbiorczego nie zostało zaimplementowane. W przypadku pobierania wierszy zbiorczych zaimplementowana jest zbiorcza wymiana pól rekordów (Bulk RFX). Zbiorczy RFX jest podobny do RFX. Aby zrozumieć różnice, zobacz [Recordset: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Globalne funkcje RFX wymieniają dane między kolumnami na źródle danych i elementach członkowskich danych pola w zbiorze rekordów. Wpisujesz wywołania funkcji RFX w funkcji elementu członkowskiego [DoFieldExchange.](../../mfc/reference/crecordset-class.md#dofieldexchange) W tym temacie opisano funkcje krótko i pokazano typy danych, dla których dostępne są funkcje RFX. [W obiekcie Technical Note 43](../../mfc/tn043-rfx-routines.md) opisano sposób pisania własnych funkcji RFX dla dodatkowych typów danych.

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>Składnia funkcji RFX

Każda funkcja RFX przyjmuje trzy parametry (a niektóre przyjmują opcjonalny parametr czwarty lub piąty):

- Wskaźnik do [obiektu CFieldExchange.](../../mfc/reference/cfieldexchange-class.md) Wystarczy przekazać wzdłuż `pFX` wskaźnika `DoFieldExchange`przekazanego do .

- Nazwa kolumny wyświetlana w źródle danych.

- Nazwa odpowiedniego elementu członkowskiego danych pola lub elementu członkowskiego danych parametru w klasie zestaw rekordów.

- (Opcjonalnie) W niektórych funkcjach maksymalna długość ciągu lub tablicy są przesyłane. Wartość domyślna to 255 bajtów, ale można ją zmienić. Maksymalny rozmiar zależy od maksymalnego `CString` rozmiaru obiektu — **INT_MAX** (2 147 483 647) bajtów — ale prawdopodobnie napotkasz limity sterowników przed tym rozmiarem.

- (Opcjonalnie) W `RFX_Text` funkcji czasami używasz piątego parametru, aby określić typ danych kolumny.

Aby uzyskać więcej informacji, zobacz funkcje RFX w obszarze [Makra i Globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołaniu do biblioteki klas*. Na przykład, kiedy można w szczególności korzystać z parametrów, zobacz [Recordset: Uzyskiwanie SUMs i inne wyniki zagregowane (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>Typy danych RFX

Biblioteka klas dostarcza funkcje RFX do przesyłania wielu różnych typów danych między źródłem danych a zestawami rekordów. Poniższa lista podsumowuje funkcje RFX według typu danych. W przypadkach, gdy należy napisać własne wywołania funkcji RFX, wybierz z tych funkcji według typu danych.

|Funkcja|Typ danych|
|--------------|---------------|
|`RFX_Bool`|**Bool**|
|`RFX_Byte`|**Bajtów**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Aby uzyskać więcej informacji, zobacz dokumentację funkcji RFX w obszarze [Makra i globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołaniu do biblioteki klas*. Aby uzyskać informacje o mapowanie typów danych języka C++ na typy danych SQL, zobacz tabelę TYPY DANYCH SQL ANSI mapowane na typy danych języka C++ w [języku SQL: SQL i C++ Typy danych (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Zobacz też

[Wymiana pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)
