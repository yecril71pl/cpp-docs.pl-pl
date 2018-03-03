---
title: Typy podstawowe (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
dev_langs:
- C++
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++], C++ data types
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb52d6a987289ed77d7b63a5497323ddad2b467
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fundamental-types--c"></a>Typy podstawowe (C++)
Typy podstawowe w języku C++ są podzielone na trzy kategorie: całkowitych, zmiennoprzecinkowych, a typ void. Typy całkowite są w stanie obsługiwać liczb całkowitych. Zmiennoprzecinkowych typów są w stanie określania wartości, które mogą mieć ułamkowych części.  
  
 [Void](../cpp/void-cpp.md) typu opisuje pustego zestawu wartości. Nie zmiennej typu `void` można określić — jest używany głównie w celu zadeklarowania funkcji zwracających wartości lub aby zadeklarować ogólnego wskaźniki bez typu lub arbitralnie wpisane danych. Dowolne wyrażenie może być jawnie przekonwertować lub rzutowany na typ `void`. Jednak takie wyrażenia są ograniczone do następujące zastosowania:  
  
-   Instrukcja wyrażenia. (Zobacz [wyrażenia](../cpp/expressions-cpp.md), aby uzyskać więcej informacji.)  
  
-   Lewy argument operacji operatora przecinka. (Zobacz [Operator przecinkowy](../cpp/comma-operator.md) Aby uzyskać więcej informacji.)  
  
-   Drugi i trzeci argument operacji operatora warunkowego (`? :`). (Zobacz [wyrażenia z Operator warunkowy](../cpp/conditional-operator-q.md) Aby uzyskać więcej informacji.)  
  
 W poniższej tabeli opisano ograniczenia rozmiarów typu. Ograniczenia te są niezależne od firmy Microsoft.  
  
### <a name="fundamental-types-of-the-c-language"></a>Typy podstawowe języka C++  
  
|Kategoria|Typ|Spis treści|  
|--------------|----------|--------------|  
|Typy całkowite|`char`|Typ `char` jest typem całkowitym, zawierający zestaw znaków wykonania podstawowych elementów członkowskich — domyślnie jest to ASCII języka Microsoft C++.<br /><br /> Kompilator języka C++ traktuje zmiennych typu `char`, `signed` `char`, i `unsigned` `char` jako mający różnych typów. Zmienne typu `char` awansowane na `int` tak, jakby są typu `signed` `char` domyślnie, chyba że używana jest opcją / kompilacji. W tym przypadku są traktowane jako typ `unsigned` `char` i awansowane na `int` bez rozszerzenia logowania.|  
||`bool`|Typ `bool` jest typem całkowitym, który może mieć jedną z dwóch wartości `true` lub `false`. Jego rozmiar jest nieokreślony.|  
||`short`|Typ `short` `int` (lub po prostu `short`) jest typem całkowitym, która jest większa niż lub równe rozmiarowi typu `char`i krótszy niż lub równe rozmiarowi typu `int`.<br /><br /> Obiekty typu `short` mogą być deklarowane jako `signed` `short` lub `unsigned short`. `Signed short`jest synonimem `short`.|  
||`int`|Typ `int` jest typem całkowitym, która jest większa niż lub równe rozmiarowi typu `short` `int`i krótszy niż lub równe rozmiarowi typu `long`.<br /><br /> Obiekty typu `int` mogą być deklarowane jako `signed` `int` lub `unsigned` `int`. `Signed``int` jest synonimem `int`.|  
||`__int8`, `__int16`, `__int32`, `__int64`|Całkowite o określonym rozmiarze `__int n`, gdzie `n` w bitach zmienna całkowitoliczbowa rozmiar. `__int8`, `__int16`, `__int32` i `__int64` są słowa kluczowe specyficzne dla firmy Microsoft. Nie wszystkie typy są dostępne na wszystkich architektury. `(__int128`nie jest obsługiwany.)|  
||`long`|Typ `long` (lub `long` `int`) jest typem całkowitym, która jest większa niż lub równe rozmiarowi typu `int`.<br /><br /> Obiekty typu `long` mogą być deklarowane jako `signed` `long` lub `unsigned` `long`. `Signed``long` jest synonimem `long`.|  
||`long``long`|Większe niż niepodpisany `long`.<br /><br /> Obiekty typu `long long` mogą być deklarowane jako `signed` `long long` lub `unsigned` `long long`. `signed``long long` jest synonimem `long long`.|  
||`wchar_t`, `__wchar_t`|Zmienna typu `wchar_t` wyznacza typ znaków dwubajtowych lub wielobajtowych znaków. Domyślnie `wchar_t` jest typem natywnym, ale może użyć [/Zc:wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) aby `wchar_t` element typedef dla `unsigned short`. `__wchar_t` Typu jest specyficzne dla firmy Microsoft synonimem natywnego `wchar_t` typu.<br /><br /> Użyj prefiksu L przed znakiem lub literału ciągu do wyznaczenia typu znaków dwubajtowych.|  
|Liczba zmiennoprzecinkowa|`float`|Typ `float` jest wartość zmiennoprzecinkowa najmniejsza typu punktu.|  
||`double`|Typ `double` jest przestawne typ punktu, który jest większy niż lub równy wpisz `float`, ale krótszy niż lub równe rozmiarowi typu `long` `double`.<br /><br /> Dotyczące firmy Microsoft: reprezentacja `long double` i `double` są identyczne. Jednak `long double` i `double` są osobne typy.|  
||`long double`|Typ `long` `double` jest przestawne typ punktu, który jest większy niż lub równy wpisz `double`.|  
  
 **Dotyczące firmy Microsoft**  
  
 W poniższej tabeli wymieniono ilości miejsca wymaganego dla podstawowych typów języka Microsoft C++.  
  
### <a name="sizes-of-fundamental-types"></a>Rozmiary typów podstawowych  
  
|Typ|Rozmiar|  
|----------|----------|  
|`bool`, `char`, `unsigned char`, `signed char`, `__int8`|1 bajt|  
|`__int16`, `short`, `unsigned short`, `wchar_t`, `__wchar_t`|2 bajty|  
|`float`, `__int32`, `int`, `unsigned int`, `long`, `unsigned long`|4 bajty|  
|`double`, `__int64`, `long double`, `long long`|8 bajtów|  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
 Zobacz [zakresy typu danych](../cpp/data-type-ranges.md) podsumowanie zakres wartości każdego typu.  
  
 Aby uzyskać więcej informacji na temat konwersji typu, zobacz [konwersje standardowe](../cpp/standard-conversions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zakresy typu danych](../cpp/data-type-ranges.md)