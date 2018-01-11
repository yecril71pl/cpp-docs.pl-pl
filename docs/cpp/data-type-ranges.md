---
title: Zakresy typu danych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: af0601299046276c135571be2bac615df1571140
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="data-type-ranges"></a>Zakresy typu danych
Visual C++ 32-bitowe i 64-bitowe kompilatory rozpoznaje typy w tabeli w dalszej części tego artykułu.  
  
-   `int` (`unsigned int`)  
  
-   `__int8` (`unsigned __int8`)  
  
-   `__int16` (`unsigned __int16`)  
  
-   `__int32` (`unsigned __int32`)  
  
-   `__int64` (`unsigned __int64`)  
  
-   `short` (`unsigned short`)  
  
-   `long` (`unsigned long`)  
  
-   `long` `long` (`unsigned long long`)  
  
 Jeśli jej nazwa rozpoczyna się od dwóch znaków podkreślenia (`__`), typ danych jest niestandardowy.  
  
 Zakresy, które podano w poniższej tabeli są wraz z wartościami granicznymi włącznie.  
  
|Nazwa typu|Bajty|Inne nazwy|Wartości zakresu|  
|---------------|-----------|-----------------|---------------------|  
|int|4|oznaczony|-2 147 483 2 147 483 648 do 647|  
|unsigned int|4|nieoznaczony|4 294 967 0 Aby 295|  
|__int8|1|char|-128 do 127 znaków.|  
|__int8 bez znaku|1|unsigned char|0 do 255.|  
|__int16|2|krótkie, krótki int, podpisany krótkich liczb całkowitych|-32768 do 32 767.|  
|__int16 bez znaku|2|niepodpisane krótkie, bez znaku krótkich liczb całkowitych|0 do 65 535.|  
|__int32|4|podpisana, podpisanego elementu int, int|-2 147 483 2 147 483 648 do 647|  
|__int32 bez znaku|4|bez znaku, unsigned int|4 294 967 0 Aby 295|  
|__int64|8|Long long podpisany long long|-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807|  
|__int64 bez znaku|8|unsigned long long|0 — 18,446,744,073,709,551,615|  
|bool|1|brak|wartość false lub wartość PRAWDA|  
|char|1|brak|-128 do 127 znaków domyślnie<br /><br /> od 0 do 255 podczas kompilacji za pomocą [/J](../build/reference/j-default-char-type-is-unsigned.md)|  
|char podpisem|1|brak|-128 do 127 znaków.|  
|unsigned char|1|brak|0 do 255.|  
|short|2|krótkich liczb całkowitych, podpisem krótkich liczb całkowitych|-32768 do 32 767.|  
|unsigned short|2|unsigned short int|0 do 65 535.|  
|long|4|długie int, podpisanego elementu int długa|-2 147 483 2 147 483 648 do 647|  
|unsigned long|4|unsigned long int|4 294 967 0 Aby 295|  
|long long|8|Brak (ale równoważne __int64)|-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807|  
|unsigned long long|8|Brak (ale odpowiednikiem niepodpisane __int64)|0 — 18,446,744,073,709,551,615|  
|enum|Zmienia się|brak| |  
|float|4|brak|3.4e +/-38 (7 cyfr)|  
|double|8|brak|1.7e +/-308 (15 cyfr)|  
|liczba typu double|Identyczny o podwójnej precyzji|brak|Identyczny o podwójnej precyzji|  
|wchar_t|2|__wchar_t|0 do 65 535.|  
  
 W zależności od sposobu ich wykorzystywania, zmienna `__wchar_t` typu znaków dwubajtowych lub znaków wielobajtowych typu. Użyj `L` prefiksu przed znakiem lub stała do wyznaczenia stała całej znaków typu string.  
  
 `signed`i `unsigned` są Modyfikatory korzystające z dowolnego typu całkowitego, z wyjątkiem `bool`. Należy pamiętać, że `char`, `signed char`, i `unsigned char` są trzy różne typy na potrzeby mechanizmów, takich jak przeciążenie i szablony.  
  
 `int` i `unsigned int` typy mają rozmiar czterech bajtów. Jednak kod przenośny powinien zależy od rozmiaru `int` ponieważ standard języka umożliwia to być konkretnej implementacji.  
  
 C/C++ w programie Visual Studio obsługuje również typy całkowite o określonym rozmiarze. Aby uzyskać więcej informacji, zobacz [__int8, \__int16, \__int32, \__int64](../cpp/int8-int16-int32-int64.md) i [limity liczb całkowitych](../cpp/integer-limits.md).  
  
 Aby uzyskać więcej informacji na temat ograniczeń rozmiary każdego typu zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).  
  
 Zakres typy wyliczane może być różna w zależności od kontekstu i określić flagi kompilatora. Aby uzyskać więcej informacji, zobacz [deklaracje wyliczenia C](../c-language/c-enumeration-declarations.md) i [wyliczenia](../cpp/enumerations-cpp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Typy podstawowe](../cpp/fundamental-types-cpp.md)