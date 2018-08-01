---
title: przestarzałe (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/28/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- deprecated_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3efc793e5030fa86c3bd1214ef4b8b408361a4ef
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408615"
---
# <a name="deprecated-c"></a>przestarzałe (C++)
Ten temat dotyczy specyficzne dla firmy Microsoft przestarzałe declspec deklaracji. Aby uzyskać informacje o C ++ 14 `[[deprecated]]` atrybutu i wskazówki dotyczące kiedy należy używać tego atrybutu, a declspec specyficzne dla firmy Microsoft lub pragma, zobacz [atrybuty Standard C++](attributes.md).

 Z wyjątkiem wymienionych poniżej **przestarzałe** deklaracji oferuje te same funkcje co [przestarzałe](../preprocessor/deprecated-c-cpp.md) pragmy:  
  
-   **Przestarzałe** deklaracji umożliwia określenie konkretnego rodzaje przeciążenia funkcji jako przestarzałe, formularz pragma ma zastosowanie do wszystkich formularzy przeciążona nazwy funkcji.  
  
-   **Przestarzałe** deklaracji pozwala określić komunikat, który będzie wyświetlana w czasie kompilacji. Tekst komunikatu można przy pomocy makra.  
  
-   Makra tylko może być oznaczony jako przestarzały z **przestarzałe** pragmy.  
  
 Gdy kompilator napotka użytkowania przestarzały identyfikator lub standardem [ `[[deprecated]]` ](attributes.md) atrybutu [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) ostrzeżenie jest zgłaszane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób oznaczania funkcji jako przestarzały i jak określić wiadomość, która będzie wyświetlana w czasie kompilacji, gdy jest używany przestarzały — funkcja.  
  
```cpp 
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
 Poniższy przykład pokazuje sposób oznaczania klasy jako przestarzały i jak określić wiadomość, która będzie wyświetlana w czasie kompilacji, gdy jest używany przestarzały klasy.  
  
```cpp 
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
  
## <a name="see-also"></a>Zobacz także  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)