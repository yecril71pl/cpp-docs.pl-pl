---
title: Operator uchwytu do obiektu (^)  (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
ms.openlocfilehash: 3d08b2294da1599282feeb1739331c31d64a9e59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358327"
---
# <a name="handle-to-object-operator---ccli-and-ccx"></a>Operator uchwytu do obiektu (^)  (C++/CLI i C++/CX)

*Deklarator dojścia* (`^`, wymawiane "kapelusz"), modyfikuje [specyfikator](../cpp/overview-of-declarators.md) typu oznacza, że zadeklarowany obiekt powinien zostać automatycznie usunięty, gdy system stwierdzi, że obiekt nie jest już dostępny.

## <a name="accessing-the-declared-object"></a>Uzyskiwanie dostępu do zadeklarowany obiekt

Zmienna, która jest zadeklarowana z deklaratorem dojścia zachowuje się jak wskaźnik do obiektu. Jednak zmienna wskazuje na cały obiekt, nie może wskazywać na element członkowski obiektu i nie obsługuje arytmetyki wskaźnika. Użyj operatora pośredniego`*`( ), aby uzyskać dostęp do obiektu, a operator dostępu do elementów członkowskich strzałki (`->`), aby uzyskać dostęp do elementu członkowskiego obiektu.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Kompilator używa mechanizmu *zliczania odwołań* COM, aby określić, czy obiekt nie jest już używany i można go usunąć. Jest to możliwe, ponieważ obiekt, który pochodzi z interfejsu środowiska wykonawczego systemu Windows jest faktycznie obiekt COM. Liczba odwołań jest zwiększana, gdy obiekt jest tworzony lub kopiowany, i zmniejszana, gdy obiekt jest ustawiony na wartość null lub wykracza poza zakres. Jeśli liczba odwołań zostanie równa zeru, obiekt zostanie automatycznie usunięty.

Zaletą deklaratora dojścia jest to, że w com należy jawnie zarządzać liczbą odwołań dla obiektu, co jest żmudnym i podatnym na błędy procesem. Oznacza to, że aby zwiększyć i zdeklizować liczbę odwołań, należy wywołać metody AddRef() i Release() obiektu. Jednak jeśli deklarujesz obiekt z deklaratorem dojścia, kompilator generuje kod, który automatycznie dostosowuje liczbę odwołań.

Aby uzyskać informacje na temat tworzenia wystąpienia obiektu, zobacz [ref new](ref-new-gcnew-cpp-component-extensions.md).

## <a name="requirements"></a>Wymagania

Opcja kompilatora:`/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

System używa mechanizmu *modułu zbierającego elementy bezużyteczne* CLR, aby określić, czy obiekt nie jest już używany i można go usunąć. Środowisko wykonawcze języka wspólnego utrzymuje stertę, na której przydziela obiekty i używa odwołań zarządzanych (zmiennych) w programie wskazują lokalizację obiektów na stercie. Gdy obiekt nie jest już używany, pamięć, która zajmuje na stercie jest zwalniany. Okresowo moduł zbierający elementy bezużyteczne kompaktywuje sterty, aby lepiej używać zwolnionej pamięci. Kompaktowanie sterty można przenieść obiekty na stercie, co unieważnia lokalizacje, o których mowa w odwołaniach zarządzanych. Jednak moduł zbierający elementy bezużyteczne jest świadomy lokalizacji wszystkich odwołań zarządzanych i automatycznie aktualizuje je, aby wskazać bieżącą lokalizację obiektów na stercie.

Ponieważ natywne wskaźniki`*`C++`&`( ) i odwołania ( ) nie są odwołaniami zarządzanymi, moduł zbierający elementy bezużyteczne nie mogą automatycznie aktualizować adresów, na które wskazują. Aby rozwiązać ten problem, należy użyć deklaratora dojścia, aby określić zmienną, o której moduł zbierający elementy bezużyteczne jest świadomy i może być aktualizowana automatycznie.

Aby uzyskać więcej informacji, zobacz [Jak: Deklarowanie uchwytów w typach macierzystych](../dotnet/how-to-declare-handles-in-native-types.md).

### <a name="examples"></a>Przykłady

W tym przykładzie pokazano, jak utworzyć wystąpienie typu odwołania na zarządzanym stosie.  Ten przykład pokazuje również, że można zainicjować jeden dojście z innym, co powoduje dwa odwołania do tego samego obiektu na zarządzanym stercie zebranej przez śmieci. Należy zauważyć, że przypisanie [nullptr](nullptr-cpp-component-extensions.md) do jednego dojścia nie oznacza obiektu do wyrzucania elementów bezużytecznych.

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

W poniższym przykładzie pokazano, jak zadeklarować dojście do obiektu na zarządzanym stosie, gdzie typ obiektu jest typem wartości pudełkowej. Przykład pokazuje również, jak uzyskać typ wartości z obiektu pudełkowego.

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

W tym przykładzie pokazano, że wspólny idiom C++ za pomocą `void*` `Object^`wskaźnika, aby wskazać dowolny obiekt jest zastępowany przez , który może pomieścić dojście do dowolnej klasy odwołania. Pokazuje również, że wszystkie typy, takie jak tablice i delegatów, mogą być konwertowane do dojścia obiektu.

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

W tym przykładzie pokazano, że dojście może być wyłuskiwane i że element członkowski można uzyskać za pośrednictwem dojścia wyłuskane.

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

W tym przykładzie pokazano, że odwołanie natywne (`&`) nie może powiązać z elementem członkowskim **int** typu zarządzanego, ponieważ **int** może być przechowywany w stercie zebranych śmieci, a odwołania macierzyste nie śledzą ruchu obiektów w zarządzanym stosie. Poprawka polega na użyciu zmiennej lokalnej `&` `%`lub na zmianę na , co czyni ją odwołaniem do śledzenia.

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

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)<br/>
[Operator odwołania śledzenia](tracking-reference-operator-cpp-component-extensions.md)
