---
title: "Kompilatora (poziom 4) ostrzeżenie C4512 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4512
dev_langs: C++
helpviewer_keywords: C4512
ms.assetid: afb68995-684a-4be5-a73a-38d7a16dc030
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3cf776d5908b747d63d17134e80a7da750852043
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4512"></a>Kompilator C4512 ostrzegawcze (poziom 4)
"class": nie można wygenerować operatora przypisania  
  
 Kompilator nie może wygenerować operatora przypisania dla danej klasy. Żaden operator przypisania został utworzony.  
  
 Operator przypisania dla klasy podstawowej, która nie jest dostępna w klasie pochodnej może spowodować to ostrzeżenie.  
  
 Aby uniknąć tego ostrzeżenia, określ operator przypisania zdefiniowane przez użytkownika dla tej klasy.  
  
 Kompilator wygeneruje również funkcji operatora przypisania dla klasy, które nie definiuje jedną. Ten operator przypisania jest kopią memberwise elementy członkowskie danych obiektu. Ponieważ `const` elementy danych nie można zmodyfikować po zainicjowaniu, jeśli klasa zawiera `const` elementu domyślnego operatora przypisania nie będzie działać. Inną przyczyną ostrzeżenie C4512 jest deklaracją elementu członkowskiego danych niestatycznych typu referencyjnego. Jeśli celem użycia jej do utworzenia-copyable typu, możesz również zapobiega tworzeniu domyślnego konstruktora kopiowania.  
  
 Aby usunąć ostrzeżenie C4512 dla kodu w jednym z trzech sposobów:  
  
-   Jawnie definiować operator przypisania dla klasy.  
  
-   Usuń **const** lub operator odwołania z elementu danych w klasie.  
  
-   Użyj #pragma [ostrzeżenie](../../preprocessor/warning.md) instrukcji, aby pominąć to ostrzeżenie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4512.  
  
```  
// C4512.cpp  
// compile with: /EHsc /W4  
// processor: x86  
  
class Base {  
private:  
   const int a;  
  
public:  
   Base(int val = 0) : a(val) {}  
   int get_a() { return a; }  
};   // C4512 warning  
  
class Base2 {  
private:  
   const int a;  
  
public:  
   Base2(int val = 0) : a(val) {}  
   Base2 & operator=( const Base2 & ) { return *this; }  
   int get_a() { return a; }  
};  
  
// Type designer intends this to be non-copyable because it has a   
// reference member  
class Base3  
{  
private:  
   char& cr;  
  
public:  
   Base3(char& r) : cr(r) {}  
   // Uncomment the following line to explicitly disable copying:  
   // Base3(const Base3&) = delete;   
};   // C4512 warning  
  
int main() {  
   Base first;  
   Base second;  
  
   // OK  
   Base2 first2;  
   Base2 second2;  
  
   char c = 'x';  
   Base3 first3(c);  
   Base3 second3 = first3; // C2280 if no default copy ctor  
}  
```