---
title: 'Wymiana pól rekordów: Używanie funkcji RFX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4669796b44c362f90feef6ba879411a849299c52
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061237"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Wymiana pól rekordów: używanie funkcji RFX

W tym temacie wyjaśniono, jak używać wywołania funkcji RFX, które tworzą treści swoje `DoFieldExchange` zastąpienia.  
  
> [!NOTE]
>  Ten temat dotyczy klasy pochodne [CRecordset](../../mfc/reference/crecordset-class.md) w wierszu zbiorczego, które podczas pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza zbiorcza wymiana pól rekordów (zbiorcze RFX) jest zaimplementowana. Zbiorcze RFX przypomina RFX. Aby poznać różnice, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
Funkcje globalne RFX wymianę danych między kolumnami na źródłowym i pola danych elementów członkowskich danych w twoim zestawie rekordów. Pisania funkcji RFX wywołuje w twoim zestawie rekordów [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcja elementu członkowskiego. Ten temat krótko opisano funkcje i zawiera typy danych, dla których RFX funkcje są dostępne. [Techniczne 43 Uwaga](../../mfc/tn043-rfx-routines.md) w tym artykule opisano jak napisać własne funkcje RFX dla dodatkowe typy danych.  
  
##  <a name="_core_rfx_function_syntax"></a> Składnia funkcji RFX  

Każda funkcja RFX przyjmuje trzy parametry (natomiast niektóre czwartym lub piątym parametr opcjonalny):  
  
- Wskaźnik do [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiektu. Po prostu przekazują `pFX` wskaźnik przekazywany do `DoFieldExchange`.  
  
- Nazwa kolumny w postaci, w jakiej pojawia się w źródle danych.  
  
- Nazwa pola odpowiedni element członkowski danych lub element członkowski danych parametru w klasie zestawu rekordów.  
  
- (Opcjonalnie) W niektórych funkcji, maksymalna długość ciągu lub tablicy przesyłane. Domyślnie jest to 255 bajtów, ale możesz chcieć ją zmienić. Maksymalny rozmiar opiera się na maksymalny rozmiar `CString` obiektu — **INT_MAX** bajtów (2 147 483 647) —, ale prawdopodobnie będą napotykać limity sterowników przed tym rozmiarze.  
  
- (Opcjonalnie) W `RFX_Text` funkcji, czasami piątego parametru do określenia używasz typu danych kolumny.  
  
Aby uzyskać więcej informacji, zapoznaj się z funkcjami RFX w obszarze [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołanie do biblioteki klas*. Na przykład gdy można wprowadzać specjalne użycia parametrów, zobacz artykuł [zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).  
  
##  <a name="_core_rfx_data_types"></a> Typy danych RFX  

Biblioteka klas dostarcza funkcje RFX transferu wielu różnych typów danych między źródłem danych i zestawach rekordów. Na poniższej liście podsumowano funkcje RFX przez typ danych. W przypadkach, w którym należy napisać własne wywołania funkcji RFX wybierz z tych funkcji przez typ danych.  
  
|Funkcja|Typ danych|  
|--------------|---------------|  
|`RFX_Bool`|**BOOL**|  
|`RFX_Byte`|**BAJTÓW**|  
|`RFX_Binary`|`CByteArray`|  
|`RFX_Double`|**double**|  
|`RFX_Single`|**float**|  
|`RFX_Int`|**int**|  
|`RFX_Long`|**long**|  
|`RFX_LongBinary`|`CLongBinary`|  
|`RFX_Text`|`CString`|  
|`RFX_Date`|`CTime`|  
  

Aby uzyskać więcej informacji, zobacz dokumentację funkcji RFX w obszarze [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *odwołanie do biblioteki klas*. Aby uzyskać informacji na temat sposobu mapowania typów danych języka C++ na typy danych SQL, zobacz tabeli ANSI SQL danych typy mapowane na typy danych języka C++ w [SQL: SQL i typów danych języka C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  

[Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Wymiana pól rekordów: jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Zestaw rekordów: parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Zestaw rekordów: dynamiczne powiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)