---
title: nullptr (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33a276c383618531103a76b1f20c6ad478d57c10
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880712"
---
# <a name="nullptr--c-component-extensions"></a>nullptr (C++ Component Extensions)
`nullptr` Reprezentuje — słowo kluczowe *wartość wskaźnika null*. Wartość wskaźnika pustego umożliwia wskazanie, czy dojście obiektu, wskaźnik wewnętrzny lub typu wskaźnika natywnego nie wskazuje obiekt.  
  
 Użyj `nullptr` z kodem zarządzanym lub macierzystym. Kompilator emituje odpowiednie, ale inną instrukcje dotyczące wartości zarządzanego i natywnego wskaźnika o wartości null. Aby dowiedzieć się, jak za pomocą ISO standardową wersję C++ to słowo kluczowe, zobacz [nullptr](../cpp/nullptr.md).  
  
 `__nullptr` — Słowo kluczowe jest słowem kluczowym specyficzne dla firmy Microsoft, która ma takie samo znaczenie jak `nullptr`, ale dotyczy tylko kodu natywnego. Jeśli używasz `nullptr` z macierzystego C/C++ kod, a następnie skompiluj z [/CLR](../build/reference/clr-common-language-runtime-compilation.md) — opcja kompilatora, kompilator nie może określić, czy `nullptr` wskazuje wartość macierzysty lub zarządzany wskaźnika o wartości null. Aby wyczyścić kompilator masz zamiar, użyj `nullptr` określenie wartości zarządzanych lub `__nullptr` określić wartość native.  
  
 `nullptr` — Słowo kluczowe jest odpowiednikiem `Nothing` w języku Visual Basic i `null` w języku C#.  
  
## <a name="usage"></a>Użycie  
 `nullptr` — Słowo kluczowe może używane wszędzie, gdzie można uchwytu, wskaźnika natywnego lub argumentu funkcji.  
  
 `nullptr` — Słowo kluczowe nie jest typem i nie jest obsługiwane przez program:  
  
-   [sizeof](../cpp/sizeof-operator.md)  
  
-   [TypeID](../cpp/typeid-operator.md)  
  
-   `throw nullptr` (mimo że `throw (Object^)nullptr;` będzie działać)  
  
 `nullptr` — Słowo kluczowe może być używana w inicjowania następujących typów wskaźnika:  
  
-   Wskaźnik natywny  
  
-   Dojście do środowiska wykonawczego systemu Windows  
  
-   Dojście do zarządzanego  
  
-   Zarządzane wskaźnik wewnętrzny  
  
 `nullptr` — Słowo kluczowe może służyć do testowania, jeśli odwołanie do wskaźnika lub dojścia jest równa null, zanim będzie można użyć odwołania.  
  
 Wywołania funkcji spośród języków, które używają wartości null wskaźnika sprawdzania błędów powinny być rozumiane poprawnie.  
  
 Nie można zainicjować dojścia do zera; tylko `nullptr` mogą być używane. Przypisanie stałej 0 na dojścia obiektu tworzy opakowanego `Int32` i Rzutowanie na `Object^`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, że `nullptr` wszędzie tam, gdzie uchwytu, wskaźnika natywnego można używać słowa kluczowego lub argument funkcji można używać. I w przykładzie pokazano, że `nullptr` — słowo kluczowe może służyć do sprawdzania odwołania, przed jego użyciem.  
  
```  
// mcpp_nullptr.cpp  
// compile with: /clr  
value class V {};  
ref class G {};  
void f(System::Object ^) {}  
  
int main() {  
// Native pointer.  
   int *pN = nullptr;  
// Managed handle.  
   G ^pG = nullptr;  
   V ^pV1 = nullptr;  
// Managed interior pointer.  
   interior_ptr<V> pV2 = nullptr;  
// Reference checking before using a pointer.  
   if (pN == nullptr) {}  
   if (pG == nullptr) {}  
   if (pV1 == nullptr) {}  
   if (pV2 == nullptr) {}  
// nullptr can be used as a function argument.  
   f(nullptr);   // calls f(System::Object ^)  
}  
```  
  
## <a name="example"></a>Przykład  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że `nullptr` i zero mogą być używane zamiennie na wskaźników natywnych.  
  
```  
// mcpp_nullptr_1.cpp  
// compile with: /clr  
class MyClass {  
public:  
   int i;  
};  
  
int main() {  
   MyClass * pMyClass = nullptr;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
  
   pMyClass = 0;  
   if ( pMyClass == nullptr)  
      System::Console::WriteLine("pMyClass == nullptr");  
  
   if ( pMyClass == 0)  
      System::Console::WriteLine("pMyClass == 0");  
}  
```  
  
 **Output**  
  
```Output  
pMyClass == nullptr  
  
pMyClass == 0  
  
pMyClass == nullptr  
  
pMyClass == 0  
```  
  
## <a name="example"></a>Przykład  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że `nullptr` jest interpretowana jako dojścia do dowolnego typu lub wskaźnik natywny do dowolnego typu. W przypadku przeciążanie funkcji z dojścia do różnych typów, zostanie wygenerowany błąd niejednoznaczności. `nullptr` Musi być jawnie rzutować na typ.  
  
```  
// mcpp_nullptr_2.cpp  
// compile with: /clr /LD  
void f(int *){}  
void f(int ^){}  
  
void f_null() {  
   f(nullptr);   // C2668  
   // try one of the following lines instead  
   f((int *) nullptr);  
   f((int ^) nullptr);  
}  
```  
  
## <a name="example"></a>Przykład  
 **Przykład**  
  
 Poniższy przykład kodu pokazuje tego rzutowania `nullptr` jest dozwolone i zwraca wskaźnika lub dojścia do typu rzutowania, który zawiera `nullptr` wartość.  
  
```  
// mcpp_nullptr_3.cpp  
// compile with: /clr /LD  
using namespace System;  
template <typename T>   
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type  
  
int main() {  
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)  
  
   // Delete the following line to resolve.  
   f(nullptr);  
  
   f(0);   // T = int, call f(int)  
}  
```  
  
## <a name="example"></a>Przykład  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że `nullptr` można użyć jako parametru funkcji.  
  
```  
// mcpp_nullptr_4.cpp  
// compile with: /clr  
using namespace System;  
void f(Object ^ x) {  
   Console::WriteLine("test");  
}  
  
int main() {  
   f(nullptr);  
}  
```  
  
 **Output**  
  
```Output  
test  
```  
  
## <a name="example"></a>Przykład  
 **Przykład**  
  
 Poniższy przykład kodu pokazuje, że jeśli uchwyty są deklarowane i nie zostało zainicjowane, są one domyślnie zainicjowane, aby `nullptr`.  
  
```  
// mcpp_nullptr_5.cpp  
// compile with: /clr  
using namespace System;  
ref class MyClass {  
public:  
   void Test() {  
      MyClass ^pMyClass;   // gc type  
      if (pMyClass == nullptr)  
         Console::WriteLine("NULL");  
   }  
};  
  
int main() {  
   MyClass ^ x = gcnew MyClass();  
   x -> Test();  
}  
```  
  
 **Output**  
  
```Output  
NULL  
```  
  
## <a name="example"></a>Przykład  
 **Przykład**  
  
 W poniższym przykładzie pokazano, że `nullptr` można przypisać na wskaźnik natywny podczas kompilowania z **/CLR**.  
  
```  
// mcpp_nullptr_6.cpp  
// compile with: /clr  
int main() {  
   int * i = 0;  
   int * j = nullptr;  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: (nie jest wymagane; obsługiwane przez wszystkie opcje generowania kodu, w tym **/ZW** i **/CLR**)  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)   
 [nullptr](../cpp/nullptr.md)