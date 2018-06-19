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
ms.openlocfilehash: 1f834f9f52c8d01dbd7eb3ff54b794afc11630ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092037"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Wymiana pól rekordów: używanie funkcji RFX
W tym temacie opisano sposób korzystania z wywołania funkcji RFX wchodzące w skład treści Twojej `DoFieldExchange` zastąpienia.  
  
> [!NOTE]
>  Ten temat dotyczy klasy pochodzące od [crecordset —](../../mfc/reference/crecordset-class.md) w wiersz, który zbiorczego pobierania nie została zaimplementowana. Jeśli używasz zbiorcze pobieranie z wiersza zbiorcza wymiana pól rekordów (RFX zbiorczego) jest zaimplementowana. Zbiorcze RFX jest podobny do RFX. Aby poznać różnice, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Globalne funkcje RFX wymiany danych między kolumnami na źródłowym i pola danych elementów członkowskich danych w twoim zestawie rekordów. Pisania odwołuje się funkcja RFX w zestawie rekordów [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) funkcję elementu członkowskiego. Ten temat krótko opisano funkcje i zawiera typy danych, dla których RFX funkcje są dostępne. [43 Uwaga techniczna](../../mfc/tn043-rfx-routines.md) opisano, jak zapisać funkcji RFX dodatkowe typy danych.  
  
##  <a name="_core_rfx_function_syntax"></a> Składnia funkcji RFX  
 Każdej funkcji RFX przyjmuje trzy parametry (i podjęcia niektórych opcjonalny parametr czterech lub pięciu):  
  
-   Wskaźnik do [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) obiektu. Po prostu przekazują `pFX` wskaźnik przekazany do `DoFieldExchange`.  
  
-   Nazwa kolumny jest wyświetlana w źródle danych.  
  
-   Nazwa elementu członkowskiego danych odpowiednie pola lub elementu członkowskiego danych parametru w klasie zestaw rekordów.  
  
-   (Opcjonalnie) W niektórych funkcji, maksymalna długość ciąg lub tablica przesyłane. Wartością domyślną 255 bajtów, ale można go zmienić. Maksymalny rozmiar opiera się na maksymalny rozmiar `CString` obiektu — **int_max —** bajtów (2 147 483 647) — ale prawdopodobnie wystąpią limity sterowników przed tym rozmiarze.  
  
-   (Opcjonalnie) W `RFX_Text` funkcji, czasami używasz piątego parametru do określania typu danych kolumny.  
  
 Aby uzyskać więcej informacji, zobacz funkcji RFX w obszarze [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *informacje dotyczące biblioteki klas*. Na przykład kiedy może uniemożliwić specjalnych parametrów, zobacz [zestaw rekordów: uzyskiwanie sum i innych wyników agregacji (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).  
  
##  <a name="_core_rfx_data_types"></a> Typy danych RFX  
 Biblioteka klas udostępnia funkcje RFX transferowania wiele różnych typów danych między źródłem danych i zestawach rekordów. Poniższa lista zawiera podsumowanie funkcji RFX według typu danych. W przypadkach, w którym należy napisać własny wywołania funkcji RFX wybierz funkcje te według typu danych.  
  
|Funkcja|Typ danych|  
|--------------|---------------|  
|`RFX_Bool`|**BOOL**|  
|`RFX_Byte`|**BAJTÓW**|  
|`RFX_Binary`|`CByteArray`|  
|`RFX_Double`|**double**|  
|`RFX_Single`|**float**|  
|`RFX_Int`|`int`|  
|`RFX_Long`|**long**|  
|`RFX_LongBinary`|`CLongBinary`|  
|`RFX_Text`|`CString`|  
|`RFX_Date`|`CTime`|  
  

 Aby uzyskać więcej informacji, zobacz dokumentację funkcji RFX w obszarze [makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md) w *informacje dotyczące biblioteki klas*. Aby uzyskać informacji na temat sposobu typy danych języka C++ mapowania typów danych SQL, zobacz tabeli ANSI SQL danych typy mapowane na typy danych języka C++ w [SQL: SQL i typy danych języka C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wymiana pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Wymiana pól rekordów: Jak działa RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [Zestaw rekordów: Parametryzacja zestawu rekordów (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [Zestaw rekordów: Dynamiczne wiązanie kolumn danych (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [Crecordset — klasa](../../mfc/reference/crecordset-class.md)   
 [Klasa CFieldExchange](../../mfc/reference/cfieldexchange-class.md)