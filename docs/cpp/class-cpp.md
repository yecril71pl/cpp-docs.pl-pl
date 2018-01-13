---
title: klasy (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: class_cpp
dev_langs: CPP
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed344d5c15e709b09b760dee74a986dde6383d22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="class-c"></a>klasa (C++)
`class` — Słowo kluczowe deklaruje typ klasy lub definiuje obiekt typu klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [template-spec]  
       class [ms-decl-spec] [tag [: base-list ]]  
{  
   member-list  
} [declarators];  
[ class ] tag declarators;  
```  
  
#### <a name="parameters"></a>Parametry  
 `template-spec`  
 Opcjonalne specyfikacje szablonu. Aby uzyskać więcej informacji, zapoznaj się [szablony](templates-cpp.md).  
  
 `class`  
 `class` — Słowo kluczowe.  
  
 `ms-decl-spec`  
 Opcjonalna specyfikacja klasy magazynowania. Aby uzyskać więcej informacji, zapoznaj się [__declspec](../cpp/declspec.md) — słowo kluczowe.  
  
 `tag`  
 Nazwa typu klasy. Tag staje się słowem zastrzeżonym, w zakresie klasy. Znacznik jest opcjonalny. Pominięcie anonimowe klasa jest zdefiniowana. Aby uzyskać więcej informacji, zobacz [anonimowe typy klas](../cpp/anonymous-class-types.md).  
  
 `base-list`  
 Opcjonalna lista klas lub struktur ta klasa pochodzi jej elementów członkowskich z. Zobacz [klasy podstawowej](../cpp/base-classes.md) Aby uzyskać więcej informacji. Każda podstawowa nazwa klasy lub struktury może być poprzedzone specyfikator dostępu ([publicznego](../cpp/public-cpp.md), [prywatnej](../cpp/private-cpp.md), [chronione](../cpp/protected-cpp.md)) i [wirtualnego](../cpp/virtual-cpp.md) słowo kluczowe. Znajdują się w tabeli dostęp do elementu członkowskiego [kontrolowanie dostępu do członków klasy](member-access-control-cpp.md) Aby uzyskać więcej informacji.  
  
 `member-list`  
 Lista elementów członkowskich klasy. Zapoznaj się [omówienie elementu członkowskiego klasy](../cpp/class-member-overview.md) Aby uzyskać więcej informacji.  
  
 `declarators`  
 Lista deklarator określenie nazwy co najmniej jedno wystąpienie typu klasy. Deklaratory może zawierać listy inicjatorów, jeśli są wszystkie elementy członkowskie danych klasy `public`. Jest to częściej stosowana w strukturach, których elementy członkowskie danych są `public` domyślnie niż w klasy. Zobacz [Przegląd Deklaratorów](../cpp/overview-of-declarators.md) Aby uzyskać więcej informacji.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat klas ogólnie rzecz biorąc, można znaleźć w następujących tematach:  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [Unii](../cpp/unions.md)  
  
-   [__multiple_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__single_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__virtual_inheritance](../cpp/inheritance-keywords.md)  
  
 Informacje dotyczące zarządzanych klas i struktur, zobacz [klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)  
  
## <a name="example"></a>Przykład  
  
```  
// class.cpp  
// compile with: /EHsc  
// Example of the class keyword  
// Exhibits polymorphism/virtual functions.  
  
#include <iostream>  
#include <string>  
#define TRUE = 1  
using namespace std;  
  
class dog  
{  
public:  
   dog()  
   {  
      _legs = 4;  
      _bark = true;  
   }  
  
   void setDogSize(string dogSize)  
   {  
      _dogSize = dogSize;  
   }  
   virtual void setEars(string type)      // virtual function  
   {  
      _earType = type;  
   }  
  
private:  
   string _dogSize, _earType;  
   int _legs;  
   bool _bark;  
  
};  
  
class breed : public dog  
{  
public:  
   breed( string color, string size)  
   {  
      _color = color;  
      setDogSize(size);  
   }  
  
   string getColor()  
   {  
      return _color;  
   }  
  
   // virtual function redefined  
   void setEars(string length, string type)  
   {  
      _earLength = length;  
      _earType = type;  
   }  
  
protected:  
   string _color, _earLength, _earType;  
};  
  
int main()  
{  
   dog mongrel;  
   breed labrador("yellow", "large");  
   mongrel.setEars("pointy");  
   labrador.setEars("long", "floppy");  
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Klasy i struktury](../cpp/classes-and-structs-cpp.md)