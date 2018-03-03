---
title: "Liczbowe, Boolean i literały wskaźnika (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 91f79a2703dee8a162b971a78eba7e13a9849b43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="numeric-boolean-and-pointer-literals--c"></a>Liczbowe, Boolean i literały wskaźnika (C++)
Literał jest element program, który bezpośrednio reprezentuje wartość. W tym artykule omówiono literałów typu Integer liczb zmiennoprzecinkowych, boolean i wskaźnika. Informacje o literały ciągów i znakowe znajdują się w temacie [ciągu i literały znaków (C++)](../cpp/string-and-character-literals-cpp.md). Istnieje również możliwość definiowania własnych literały według dowolnej z tych kategorii; Aby uzyskać więcej informacji, zobacz [zdefiniowane przez użytkownika literałów (C++)](../cpp/user-defined-literals-cpp.md)  
  
 . Literały w wielu sytuacjach, ale większość często zainicjować zmienne nazwanego i służy do przekazania argumentów do funkcji:  
  
```  
const int answer = 42; // integer literal  
double d = sin(108.87);     //floating point literal passed to sin function  
bool b = true;              // boolean literal  
MyClass* mc = nullptr;      // pointer literal  
  
```  
  
 Czasami jest ważne nakazuje kompilatorowi interpretowanie literału lub jakie określonego typu, aby przekazać do niego. W tym celu dołączanie prefiksy lub sufiksy literału. Na przykład prefiks 0 x informuje kompilator, aby zinterpretować numer następującym jako wartość szesnastkowa, na przykład 0x35. Sufiks EŁNA informuje kompilator, aby wartość jest traktowana `unsigned long long` typu, jak 5894345ULL. Zobacz następujące sekcje, aby uzyskać pełną listę prefiksów i sufiksów dla każdego typu literału.  
  
## <a name="syntax"></a>Składnia  
  
## <a name="integer-literals"></a>Literały całkowite  
 Literały całkowite rozpoczyna się od cyfry i nie ułamkowych części ani wykładniki. Literały całkowite można określić w postaci dziesiętnej, ósemkowe lub szesnastkową. Mogą one określać typy oznaczone lub nieoznaczone oraz typy long lub short.  
  
 Jeśli występuje nie prefiksu lub sufiksu kompilator zapewni typu całkowitego wartość literału `int` (32-bitowy), jeśli wartość zmieści się, w przeciwnym razie zapewnia on typ `long long` (64-bitowy).  
  
 Aby określić dziesiętną literał całkowity, Rozpocznij specyfikacji z różną od zera cyfrę. Na przykład:  
  
```  
int i = 157;   // Decimal literal  
int j = 0198;       // Not a decimal number; erroneous octal literal  
int k = 0365;       // Leading zero specifies octal literal, not decimal  
int m = 36'000'000  // digit separators make large values more readable  
int   
```  
  
 Aby określić ósemkowe literał całkowity, Rozpocznij Specyfikacja o 0, następuje sekwencję cyfr w zakresie od 0 do 7. 8 do 9 cyfr są błędy określania ósemkowe literal. Na przykład:  
  
```  
int i = 0377;   // Octal literal  
int j = 0397;        // Error: 9 is not an octal digit  
```  
  
 Aby określić szesnastkowe literał całkowity, Rozpocznij specyfikacji z `0x` lub `0X` (wielkość liter "x" nie ma znaczenia), następuje sekwencję cyfr w zakresie `0` za pośrednictwem `9` i `a` (lub `A`) za pomocą `f` (lub `F`). Cyfry szesnastkowe od `a` (lub `A`) do `f` (lub `F`) reprezentują wartości z zakresu od 10 do 15. Na przykład:  
  
```  
int i = 0x3fff;   // Hexadecimal literal  
int j = 0X3FFF;        // Equal to i  
```  
  
 Aby określić typ bez znaku, użyj **u** lub **U** sufiks. Aby określić typu long, użyj **l** lub **L** sufiks. Aby określić 64-bitowego typu całkowitego, użyj LL lub ll sufiks. Sufiks komputerach 64 nadal jest obsługiwany, ale należy unikać, ponieważ specyficzne dla firmy Microsoft i nie jest przenośnej. Na przykład:  
  
```  
unsigned val_1 = 328u;             // Unsigned value  
long val_2 = 0x7FFFFFL;                 // Long value specified   
                                        //  as hex literal  
unsigned long val_3 = 0776745ul;        // Unsigned long value  
auto val_4 = 108LL;                           // signed long long  
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long   
```  
  
 **Separatory cyfr**: znak pojedynczego cudzysłowu (apostrof) można użyć wartości miejsce w większą liczbą ułatwi ich dla ludzi do odczytu. Separatory nie mają wpływu na kompilacji.  
  
```  
long long i = 24'847'458'121  
```  
  
## <a name="floating-point-literals"></a>Literały punkcie zmiennoprzecinkowych  
 Literały zmiennoprzecinkowe określić wartości, które muszą mieć część ułamkowa. Wartości te zawierają miejsc dziesiętnych (**.**) i może zawierać wykładniki.  
  
 Literały liczb zmiennoprzecinkowych zostały "mantysy,", która określa wartość numer, "wykładnik," który określa wielkość numer, i opcjonalnie sufiks, który określa typ literału. Mantysa jest określony jako sekwencję cyfr następuje okres, opcjonalne sekwencji cyfr reprezentujący ułamkową część liczby. Na przykład:  
  
```  
18.46  
38.  
```  
  
 Wykładnik, jeśli jest obecny, określa wielkość liczby jako potęgi 10, jak pokazano w poniższym przykładzie:  
  
```  
18.46e0      // 18.46  
18.46e1           // 184.6  
```  
  
 Wykładnik może być określona za pomocą **e** lub **E**, które mają takie samo znaczenie znakiem opcjonalne (+ lub -) i sekwencji cyfr.  Jeśli występuje wykładnik końcowej punktu dziesiętnego nie jest konieczne w liczbach takich jak `18E0`.  
  
 Literały zmiennoprzecinkowe domyślne na typ **podwójne**. Za pomocą sufiksy **f** lub **l** (lub **F** lub **L** — sufiks nie jest uwzględniana wielkość liter), można określić jako literał  **float** lub `long double`odpowiednio.  
  
 Mimo że `long double` i **podwójne** ma reprezentacji w tym samym, nie są tego samego typu. Na przykład możesz można mieć przeciążonej funkcji, takich jak  
  
```  
void func( double );  
```  
  
 and  
  
```  
void func( long double );  
```  
  
## <a name="boolean-literals"></a>Literałów wartości logicznych  
 Literałów wartości logicznych są `true` i `false`.  
  
## <a name="pointer-literal-c11"></a>Literał wskaźnika (C ++ 11)  
 Wprowadza C++ [nullptr](../cpp/nullptr.md) literału, aby określić wskaźnik zainicjowane przez zero. Kod przenośny `nullptr` powinna być używana zamiast funkcji całkowitym typu zero lub makra takie jak wartości NULL.  
  
## <a name="binary-literals-c14"></a>Literały binarnego (C ++ 14)  
 Literał binarny można określić za pomocą `0B` lub `0b` prefiksu, następuje sekwencji 1 i 0:  
  
```  
  
auto x = 0B001101 ; // int  
auto y = 0b000001 ; // int  
```  
  
## <a name="avoid-using-literals-as-magic-constants"></a>Unikaj używania literałów jako "stałe magic"  
 Chociaż nie zawsze jest dobrym rozwiązaniem programowania, można użyć literałów bezpośrednio w wyrażenia i instrukcje:  
  
```  
if (num < 100)  
    return "Success";  
  
```  
  
 W poprzednim przykładzie może być lepiej jest użyć nazwanej stałej, przekazujący wyczyść znaczenie, na przykład "MAXIMUM_ERROR_THRESHOLD". Jeśli wartość zwracana przez "Powodzenie" jest widoczny dla użytkowników końcowych, to może być lepiej jest użyć stałą ciągu o nazwie, które mogą być przechowywane w jednym miejscu w pliku, z którym może być lokalizowany na inne języki. Używanie o nazwie stałe pomaga w innym, a także aby zrozumieć celem kod.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje leksykalne](../cpp/lexical-conventions.md)   
 [Literały ciągu języka C++](../cpp/string-and-character-literals-cpp.md)   
 [Literały definiowane przez użytkownika C++](../cpp/user-defined-literals-cpp.md)