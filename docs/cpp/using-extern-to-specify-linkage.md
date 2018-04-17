---
title: Użycie zewnętrznie w celu określenia powiązania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/06/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 319ee69d30ad49ff745df05172db10503b3b42e0
ms.sourcegitcommit: 770f6c4a57200aaa9e8ac6e08a3631a4b4bdca05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="using-extern-to-specify-linkage"></a>Użycie zewnętrznie w celu określenia powiązania
## <a name="syntax"></a>Składnia  
  
```  
extern string-literal { declaration-list }  
extern string-literal declaration  
```  
  
## <a name="remarks"></a>Uwagi  
 `extern` — Słowo kluczowe deklaruje zmienną lub funkcję i określa, czy ma ona połączenie zewnętrzne (jego nazwa jest widoczna z plików innego niż ten, w którym jest zdefiniowana). Podczas modyfikowania zmiennej, `extern` Określa, że zmienna ma statyczny czas trwania (przydzielany podczas program rozpoczyna się i alokację podczas kończenia program). Zmienną lub funkcję, może być zdefiniowana w innym pliku źródłowego lub później w tym samym pliku. Deklaracje zmiennych i funkcji w zakresie pliku są zewnętrzne domyślnie.  
  
## <a name="example"></a>Przykład  
  
```  
// specifying_linkage1.cpp  
int i = 1;  
void other();  
  
int main() {  
   // Reference to i, defined above:  
   extern int i;  
}  
  
void other() {  
   // Address of global i assigned to pointer variable:  
   static int *external_i = &i;  
  
   // i will be redefined; global i no longer visible:  
   // int i = 16;  
}  
```  
  
 W języku C++, gdy jest używany z ciągu `extern` Określa, czy dla declarator(s) są używane konwencje powiązanie dla innego języka. Funkcje języka C i dane są dostępne tylko wtedy, gdy wcześniej zostały zgłoszone jako mających powiązanie C. Jednak muszą być zdefiniowane w jednostce tłumaczenia oddzielnie skompilowany.  
  
 Microsoft C++ obsługuje ciągi **"C"** i **"C++"** w *literał ciągu* pola. Wszystkie standardowe obejmują użycie plików `extern` składni "C", aby umożliwić funkcji biblioteki wykonawczej języka używanego w programach języka C++.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono alternatywne metody zadeklarować nazwy, które mają powiązanie C:  
  
```  
// specifying_linkage2.cpp  
// compile with: /c  
// Declare printf with C linkage.  
extern "C" int printf( const char *fmt, ... );  
  
//  Cause everything in the specified header files  
//   to have C linkage.  
extern "C" {  
   // add your #include statements here  
   #include <stdio.h>  
}  
  
//  Declare the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" {  
   char ShowChar( char ch );  
   char GetChar( void );  
}  
  
//  Define the two functions ShowChar and GetChar  
//   with C linkage.  
extern "C" char ShowChar( char ch ) {  
   putchar( ch );  
   return ch;  
}  
  
extern "C" char GetChar( void ) {  
   char ch;  
  
   ch = getchar();  
   return ch;  
}  
  
// Declare a global variable, errno, with C linkage.  
extern "C" int errno;  
```  
  
 Jeśli funkcja ma więcej niż jedną specyfikację powiązania, muszą być zgodne; błędem jest deklaracja funkcji jako posiadających powiązania C i C++. Ponadto, jeśli dwie deklaracje dla funkcji występują w programie — jedna ze specyfikacją powiązania i jedna bez niej — deklaracja ze specyfikacją powiązania musi być pierwsza. Wszystkim nadmiarowym deklaracjom funkcji, które mają już specyfikację, nadawane są specyfikacje powiązania określone w pierwszej deklaracji. Na przykład:  
  
```  
extern "C" int CFunc1();  
...  
int CFunc1();            // Redeclaration is benign; C linkage is  
                         //  retained.  
  
int CFunc2();  
...  
extern "C" int CFunc2(); // Error: not the first declaration of  
                         //  CFunc2;  cannot contain linkage  
                         //  specifier.  
```  
  
 Funkcje i obiekty jawnie deklarować jako **statycznych** w treści specyfikator złożone powiązanie (**{}**) są traktowane jako statyczne funkcje lub obiektów; specyfikator połączenie jest ignorowana. Inne funkcje i obiekty zachowują się tak, jakby były zadeklarowane za pomocą słowa kluczowego `extern`. (Zobacz [użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md) szczegółowe informacje o `extern` — słowo kluczowe.)  
  
## <a name="see-also"></a>Zobacz też  
 [Keywords](../cpp/keywords-cpp.md)   
 [extern Specyfikator klasy magazynu](../c-language/extern-storage-class-specifier.md)   
 [Identyfikatory zachowania](../c-language/behavior-of-identifiers.md)   
 [Połączenie](../c-language/linkage.md)