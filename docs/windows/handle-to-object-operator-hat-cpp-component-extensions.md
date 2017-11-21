---
title: Operator uchwytu do obiektu (^) (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 85adbf7c14f0d610cea4085169b945b55d6b5ab9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="handle-to-object-operator---c-component-extensions"></a>Operator uchwytu do obiektu (^) (C++ Component Extensions)
*Obsługi deklarator* (`^`, Wymowa "hat"), modyfikuje typ [specyfikator](../cpp/overview-of-declarators.md) oznacza, że zadeklarowane obiektu powinien automatycznie usunięta, gdy system sprawdza, czy obiekt jest nie jest już dostępny.  
  
## <a name="accessing-the-declared-object"></a>Uzyskiwanie dostępu do obiektu zadeklarowana  
 Zmienna, która jest zadeklarowana z deklarator dojście zachowuje się jak wskaźnik do obiektu. Element członkowski obiektu nie może wskazywać zmiennej punktami całego obiektu i nie obsługuje arytmetyki wskaźnika. Użyj operator pośredni (`*`) dostęp do obiektu i operatora dostępu do elementu członkowskiego strzałkę (`->`) można uzyskać dostępu do członka obiektu.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Kompilator używa modelu COM *liczenie odwołań w* mechanizmu, aby ustalić, czy obiekt jest już używany i można go usunąć. Jest to możliwe, ponieważ obiekt, który jest pochodną interfejsu środowiska wykonawczego systemu Windows jest rzeczywiście obiektu COM. Liczba odwołań jest zwiększany, gdy obiekt został utworzony lub skopiowane i zmniejszana, gdy obiekt ma ustawioną wartość null lub jest umieszczane poza zakresem. Jeśli liczba odwołań do zera, ten obiekt jest automatycznie i natychmiast usunięty.  
  
 Zaletą deklarator dojście jest w modelu COM musi jawnie Zarządzanie liczba odwołań dla obiekt, który jest procesem podatne żmudnego i błędów. Oznacza to aby zwiększyć i zmniejszyć liczbę odwołań należy wywołać metody AddRef() obiektu i Release() obiektu. Jednak przy deklarowaniu obiektu z deklarator dojście kompilatora Visual C++ generuje kod, który automatycznie dostosowuje liczbę odwołań.  
  
 Aby uzyskać informacje na temat sposobu tworzenia wystąpienia obiektu, zobacz [ref nowe](../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
## <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 System używa CLR *modułu zbierającego elementy bezużyteczne* mechanizmu, aby ustalić, czy obiekt jest już używany i można go usunąć. Środowisko uruchomieniowe języka wspólnego przechowuje sterty przydzielania obiektów i używa zarządzane odniesienia (zmienne) w programie wskaż lokalizację obiektów na stercie. Gdy obiekt jest już używany, pamięci, która go zajęte na stercie zostanie zwolniona. Okresowo moduł zbierający elementy bezużyteczne kompaktuje sterty na lepsze wykorzystanie pamięci zwolnionych. Kompaktowanie sterty obiekty można przenosić na stercie, co spowoduje unieważnienie lokalizacji określonej przez zarządzanych odwołań. Jednak moduł garbage collector zna lokalizacji wszystkie odwołania zarządzane i automatycznie aktualizuje je, aby wskazać lokalizację bieżącego obiektów na stercie.  
  
 Ponieważ wskaźników natywnych języka C++ (`*`) i odwołania (`&`) nie są zarządzane odniesienia, moduł zbierający elementy bezużyteczne nie można automatycznie zaktualizować adresów, aby wskazywały. Aby rozwiązać ten problem, użyj deklarator uchwyt, aby określić zmienną moduł garbage collector zna i można automatycznie zaktualizować.  
  
 W programie Visual C++ 2002 i 2003 Visual C++ `__gc *` został użyty do deklarowania obiektów na stercie zarządzanej.  `^` Zastępuje `__gc *` w nowej składni.  
  
 Aby uzyskać więcej informacji, zobacz [porady: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).  
  
### <a name="examples"></a>Przykłady  
 **Przykład**  
  
 W tym przykładzie przedstawiono sposób tworzenia wystąpienia typu referencyjnego na stercie zarządzanej.  W tym przykładzie przedstawiono również, że można zainicjować określonego dojścia innym, co dwa odwołania do tego samego obiektu na stercie zarządzanej, zbierane w pamięci. Zwróć uwagę, że przypisywanie [nullptr](../windows/nullptr-cpp-component-extensions.md) do realizacji jednej nie oznacza obiekt do wyrzucanie elementów bezużytecznych.  
  
```  
// mcppv2_handle.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   MyClass() : i(){}  
   int i;  
   void Test() {  
      i++;  
      System::Console::WriteLine(i);  
   }  
};  
  
int main() {  
   MyClass ^ p_MyClass = gcnew MyClass;  
   p_MyClass->Test();  
  
   MyClass ^ p_MyClass2;  
   p_MyClass2 = p_MyClass;  
  
   p_MyClass = nullptr;  
   p_MyClass2->Test();     
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
1  
2  
```  
  
 **Przykład**  
  
 Poniższy przykład przedstawia sposób zadeklarować dojścia do obiektów na stercie zarządzanej, której typ obiektu jest opakowanym typem wartościowym. Próbka przedstawiono również sposób uzyskać typ wartości z obiektu ramce.  
  
```  
// mcppv2_handle_2.cpp  
// compile with: /clr  
using namespace System;  
  
void Test(Object^ o) {  
   Int32^ i = dynamic_cast<Int32^>(o);  
  
   if(i)  
      Console::WriteLine(i);  
   else  
      Console::WriteLine("Not a boxed int");  
}  
  
int main() {  
   String^ str = "test";  
   Test(str);  
  
   int n = 100;  
   Test(n);  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
Not a boxed int  
100  
```  
  
 **Przykład**  
  
 W tym przykładzie przedstawiono typowe idiom C++ do punktu do dowolnego obiektu za pomocą wskaźnika void * zastępuje obiekt ^, która zawiera dojścia do dowolnej klasy odwołania. Pokazuje też, że wszystkie typy, takie jak tablice i delegatów, można przekonwertować na dojścia obiektu.  
  
```  
// mcppv2_handle_3.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Collections;  
public delegate void MyDel();  
ref class MyClass {  
public:  
   void Test() {}  
};  
  
void Test(Object ^ x) {  
   Console::WriteLine("Type is {0}", x->GetType());  
}  
  
int main() {  
   // handle to Object can hold any ref type  
   Object ^ h_MyClass = gcnew MyClass;  
  
   ArrayList ^ arr = gcnew ArrayList();  
   arr->Add(gcnew MyClass);  
  
   h_MyClass = dynamic_cast<MyClass ^>(arr[0]);  
   Test(arr);  
  
   Int32 ^ bi = 1;  
   Test(bi);  
  
   MyClass ^ h_MyClass2 = gcnew MyClass;  
  
   MyDel^ DelInst = gcnew MyDel(h_MyClass2, &MyClass::Test);  
   Test(DelInst);  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
Type is System.Collections.ArrayList  
  
Type is System.Int32  
  
Type is MyDel  
```  
  
 **Przykład**  
  
 W tym przykładzie pokazano, że dojścia może wyłuskiwany i czy element członkowski jest dostępna za pośrednictwem wyłuskiwany dojścia.  
  
```  
// mcppv2_handle_4.cpp  
// compile with: /clr  
using namespace System;  
value struct DataCollection {  
private:  
   int Size;  
   array<String^>^ x;  
  
public:  
   DataCollection(int i) : Size(i) {  
      x = gcnew array<String^>(Size);  
      for (int i = 0 ; i < Size ; i++)  
         x[i] = i.ToString();  
   }  
  
   void f(int Item) {  
      if (Item >= Size)  
      {  
         System::Console::WriteLine("Cannot access array element {0}, size is {1}", Item, Size);  
         return;  
      }  
      else  
         System::Console::WriteLine("Array value: {0}", x[Item]);  
   }  
};  
  
void f(DataCollection y, int Item) {  
   y.f(Item);  
}  
  
int main() {  
   DataCollection ^ a = gcnew DataCollection(10);  
   f(*a, 7);   // dereference a handle, return handle's object  
   (*a).f(11);   // access member via dereferenced handle  
}  
```  
  
 **Dane wyjściowe**  
  
```Output  
Array value: 7  
  
Cannot access array element 11, size is 10  
```  
  
 **Przykład**  
  
 W tym przykładzie pokazano, że odwołanie do natywnego (`&`) nie można powiązać z `int` elementu członkowskiego typu zarządzanego jako `int` mogą być przechowywane w pamięci sterty zebranych i natywnego odwołania nie śledzą ruch obiektów na stercie zarządzanej. Poprawka jest, aby użyć zmiennej lokalnej lub zmienić `&` do `%`, dzięki czemu odwołaniem śledzącym.  
  
```  
// mcppv2_handle_5.cpp  
// compile with: /clr  
ref struct A {  
   void Test(unsigned int &){}  
   void Test2(unsigned int %){}  
   unsigned int i;  
};  
  
int main() {  
   A a;  
   a.i = 9;  
   a.Test(a.i);   // C2664  
   a.Test2(a.i);   // OK  
  
   unsigned int j = 0;  
   a.Test(j);   // OK  
}  
```  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)   
 [Operator odwołania śledzenia](../windows/tracking-reference-operator-cpp-component-extensions.md)