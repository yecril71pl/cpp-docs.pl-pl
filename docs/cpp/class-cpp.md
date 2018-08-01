---
title: Klasa (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- class_cpp
dev_langs:
- CPP
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3c3defdfb882db69f7789c97feba11d346e540
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405590"
---
# <a name="class-c"></a>klasa (C++)
**Klasy** — słowo kluczowe deklaruje typu klasy lub definiuje obiekt typu klasy.  
  
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
 *specyfikacje szablonu*  
 Opcjonalne specyfikacje szablonu. Aby uzyskać więcej informacji, zobacz [szablony](templates-cpp.md).  
  
 *class*  
 **Klasy** — słowo kluczowe.  
  
 *MS-decl-spec*  
 Opcjonalna specyfikacja klasy magazynowania. Aby uzyskać więcej informacji, zobacz [__declspec](../cpp/declspec.md) — słowo kluczowe.  
  
 *Tag*  
 Nazwa typu nadana tej klasy. Znacznik staje się słowem zastrzeżonym w zakresie klasy. Znacznik jest opcjonalny. W przypadku pominięcia jest zdefiniowana klasa anonimowa. Aby uzyskać więcej informacji, zobacz [anonimowe typy klas](../cpp/anonymous-class-types.md).  
  
 *Lista podstawowego*  
 Opcjonalna lista klas lub struktur tej klasy, z której pochodzą składowe. Zobacz [klasy podstawowej](../cpp/base-classes.md) Aby uzyskać więcej informacji. Każda podstawowa nazwy klasy lub struktury może być poprzedzona przez specyfikator dostępu ([publicznych](../cpp/public-cpp.md), [prywatnej](../cpp/private-cpp.md), [chronione](../cpp/protected-cpp.md)) i [wirtualnego](../cpp/virtual-cpp.md) słowo kluczowe. Zobacz tabelę dostępu do elementu członkowskiego w [kontrolowanie dostępu do składowych klasy](member-access-control-cpp.md) Aby uzyskać więcej informacji.  
  
 *Lista elementów członkowskich*  
 Lista składowych klasy. Zapoznaj się [omówienie składowej klasy](../cpp/class-member-overview.md) Aby uzyskać więcej informacji.  
  
 *deklaratory*  
 Lista deklaratora określająca nazwy co najmniej jedno wystąpienie typu klasy. Deklaratory mogą zawierać listy inicjatorów, jeśli wszystkie składowe danych klasy są **publicznych**. Jest to bardziej powszechne w strukturach, w których elementy członkowskie danych są **publicznych** domyślnie niż w klasach. Zobacz [Przegląd Deklaratorów](../cpp/overview-of-declarators.md) Aby uzyskać więcej informacji.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat klas ogólnie rzecz biorąc, można skorzystać z jednego z następujących tematów:  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [Unia](../cpp/unions.md)  
  
-   [__multiple_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__single_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__virtual_inheritance](../cpp/inheritance-keywords.md)  
  
 Aby uzyskać informacje dotyczące zarządzanych klas i struktur, zobacz [klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)  
  
## <a name="example"></a>Przykład  
  
```cpp 
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
  
## <a name="see-also"></a>Zobacz także  
 [Keywords](../cpp/keywords-cpp.md)   
 [Klasy i struktury](../cpp/classes-and-structs-cpp.md)