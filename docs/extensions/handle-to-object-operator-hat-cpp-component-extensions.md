---
title: Operator uchwytu do obiektu (^)  (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
ms.openlocfilehash: f09fd5f112e3538fa2d7fb04c755031d413de9b8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225153"
---
# <a name="handle-to-object-operator---ccli-and-ccx"></a>Operator uchwytu do obiektu (^)  (C++/CLI i C++/CX)

*Dojście deklarator* ( `^` , wymawiane "Hat") modyfikuje [specyfikatora](../cpp/overview-of-declarators.md) typu, aby oznaczało, że zadeklarowany obiekt powinien zostać automatycznie usunięty, gdy system ustali, że obiekt nie jest już dostępny.

## <a name="accessing-the-declared-object"></a>Uzyskiwanie dostępu do zadeklarowanego obiektu

Zmienna zadeklarowana przy użyciu uchwytu deklarator zachowuje się jak wskaźnik do obiektu. Jednak zmienna wskazuje cały obiekt, nie może wskazywać elementu członkowskiego obiektu i nie obsługuje arytmetycznego wskaźnika. Użyj operatora pośredniego ( `*` ), aby uzyskać dostęp do obiektu, i operator dostępu do elementu członkowskiego ( `->` ), aby uzyskać dostęp do elementu członkowskiego obiektu.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Kompilator używa mechanizmu *zliczania odwołań* com, aby określić, czy obiekt nie jest już używany i czy można go usunąć. Jest to możliwe, ponieważ obiekt pochodzący z interfejsu środowisko wykonawcze systemu Windows jest w rzeczywistości obiektem COM. Licznik odwołań jest zwiększany, gdy obiekt jest tworzony lub kopiowany i zmniejszany, gdy obiekt jest ustawiony na wartość null lub wykracza poza zakres. Jeśli liczba odwołań spadnie do zera, obiekt jest automatycznie i natychmiast usuwany.

Zaletą obsługi deklarator jest to, że w modelu COM należy jawnie zarządzać liczbą odwołań dla obiektu, który jest żmudnym i podatnym na błędy proces. Oznacza to, że aby zwiększyć i zmniejszyć liczbę odwołań, należy wywołać metody AddRef () i Release () obiektu. Jednakże jeśli zadeklarujesz obiekt z deklarator dojścia, kompilator generuje kod, który automatycznie dostosowuje liczbę odwołań.

Aby uzyskać informacje na temat tworzenia wystąpienia obiektu, zobacz [ref new](ref-new-gcnew-cpp-component-extensions.md).

## <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

System używa mechanizmu *modułu zbierającego elementy bezużyteczne* środowiska CLR w celu ustalenia, czy obiekt nie jest już używany i można go usunąć. Środowisko uruchomieniowe języka wspólnego utrzymuje stertę, na której przydziela obiekty, i używa odwołań zarządzanych (zmiennych) w programie wskazuje lokalizację obiektów na stercie. Gdy obiekt nie jest już używany, zwolniona jest pamięć, która jest zajęta na stercie. Okresowo Moduł wyrzucania elementów bezużytecznych kompaktuje stertę, aby lepiej wykorzystać ilość pamięci. Kompaktowanie sterty może przenosić obiekty ze sterty, co unieważnia lokalizacje, do których odwołują się odwołania zarządzane. Jednak Moduł wyrzucania elementów bezużytecznych wie o lokalizacji wszystkich zarządzanych odwołań i automatycznie aktualizuje je, aby wskazać bieżącą lokalizację obiektów na stercie.

Ponieważ natywne wskaźniki C++ ( `*` ) i odwołania ( `&` ) nie są odwołaniami zarządzanymi, Moduł wyrzucania elementów bezużytecznych nie może automatycznie aktualizować adresów, do których wskazują. Aby rozwiązać ten problem, należy użyć deklarator dojścia do określenia zmiennej, której dotyczy Moduł wyrzucania elementów bezużytecznych i która może zostać zaktualizowana automatycznie.

Aby uzyskać więcej informacji, zobacz [instrukcje: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

### <a name="examples"></a>Przykłady

Ten przykład pokazuje, jak utworzyć wystąpienie typu odwołania na zarządzanym stosie.  Ten przykład pokazuje również, że możliwe jest zainicjowanie jednego dojścia do innego, co powoduje utworzenie dwóch odwołań do tego samego obiektu na zarządzanej stercie ze stertą. Należy zauważyć, że przypisanie [nullptr](nullptr-cpp-component-extensions.md) do jednego dojścia nie oznacza obiektu do wyrzucania elementów bezużytecznych.

```cpp
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

```Output
1
2
```

Poniższy przykład pokazuje, jak zadeklarować dojście do obiektu na zarządzanym stosie, gdzie typ obiektu jest opakowanym typem wartościowym. Przykład pokazuje również, jak uzyskać typ wartości z obiektu opakowanego.

```cpp
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

```Output
Not a boxed int
100
```

Ten przykład pokazuje, że typowe idiom języka C++ przy użyciu **`void*`** wskaźnika do wskazywania dowolnego obiektu jest zastępowane przez `Object^` , co może obsłużyć dojście do dowolnej klasy referencyjnej. Pokazuje również, że wszystkie typy, takie jak tablice i Delegaty, można przekonwertować na dojście do obiektu.

```cpp
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

```Output
Type is System.Collections.ArrayList

Type is System.Int32

Type is MyDel
```

Ten przykład pokazuje, że można odwoływać się do dojścia oraz uzyskać dostęp do elementu członkowskiego za pośrednictwem dojścia do odwołania.

```cpp
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

```Output
Array value: 7

Cannot access array element 11, size is 10
```

Ten przykład pokazuje, że odwołanie natywne ( `&` ) nie może być powiązane z **`int`** elementem członkowskim typu zarządzanego, ponieważ **`int`** mogą one być przechowywane na stercie, a odwołania natywne nie śledzą przenoszenia obiektów w zarządzanym stosie. Poprawka polega na użyciu zmiennej lokalnej lub do zmiany w `&` `%` , co sprawia, że jest to odwołanie śledzące.

```cpp
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

Opcja kompilatora:`/clr`

## <a name="see-also"></a>Zobacz także

[Rozszerzenia składników dla platform .NET i platformy UWP](component-extensions-for-runtime-platforms.md)<br/>
[Operator odwołania śledzenia](tracking-reference-operator-cpp-component-extensions.md)
