---
title: "przestarzałe (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: deprecated_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb0dd0bd25f1e4f8d0fd3bc0f1bee19f34497fb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="deprecated-c"></a>przestarzałe (C++)
Ten temat dotyczy specyficzne dla firmy Microsoft przestarzała deklaracja declspec. Informacje o C ++ 14 `[[deprecated]]` atrybutu i wskazówki na użycie tego atrybutu, a declspec specyficzne dla firmy Microsoft lub pragma, zobacz [atrybuty Standard C++](attributes2.md).

 Z wyjątkiem wymienionych poniżej **przestarzałe** deklaracji oferuje te same funkcje co [przestarzałe](../preprocessor/deprecated-c-cpp.md) pragma:  
  
-   **Przestarzałe** deklaracji pozwala określić formy określonego przeciążenia funkcji jako przestarzałe, formularz pragma ma zastosowanie do wszystkich formularzy przeciążone nazwy funkcji.  
  
-   **Przestarzałe** deklaracji pozwala określić wiadomość, która będzie wyświetlana w czasie kompilacji. Tekst komunikatu może być przy pomocy makra.  
  
-   Makra tylko może być oznaczony jako przestarzały z **przestarzałe** pragma.  
  
 Jeśli kompilator napotka użycia przestarzały identyfikator lub standardowego [ `[[deprecated]]` ](attributes2.md) atrybutu, [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) generowany jest ostrzeżenie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zostać oznaczone jako przestarzałe funkcje oraz sposobu określania komunikat, który będzie wyświetlany w czasie kompilacji, gdy jest używany przestarzały funkcji.  
  
```  
// deprecated.cpp  
// compile with: /W3  
#define MY_TEXT "function is deprecated"  
void func1(void) {}  
__declspec(deprecated) void func1(int) {}  
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}  
__declspec(deprecated(MY_TEXT)) void func3(int) {}  
  
int main() {  
   func1();  
   func1(1);   // C4996  
   func2(1);   // C4996  
   func3(1);   // C4996  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób klasy zostać oznaczone jako przestarzałe oraz sposobu określania komunikat, który będzie wyświetlany w czasie kompilacji, gdy jest używany przestarzały klasy.  
  
```  
// deprecate_class.cpp  
// compile with: /W3  
struct __declspec(deprecated) X {  
   void f(){}  
};  
  
struct __declspec(deprecated("** X2 is deprecated **")) X2 {  
   void f(){}  
};  
  
int main() {  
   X x;   // C4996  
   X2 x2;   // C4996  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)