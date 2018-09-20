---
title: Operator uchwytu do obiektu (^) (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ^ handle to object [C++]
ms.assetid: 70c411e6-be57-4468-a944-6ea7be89f392
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fa72b6ec2983c0d7b9850578e743d03b7e3946e3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410861"
---
# <a name="handle-to-object-operator---c-component-extensions"></a>Operator uchwytu do obiektu (^) (C++ Component Extensions)

*Deklarator obsługi* (`^`, wymawiane "hat"), modyfikuje typ [specyfikator](../cpp/overview-of-declarators.md) oznacza, że deklarowany obiekt powinien zostać automatycznie usunięty gdy system określi, że obiekt jest nie będą już dostępne.

## <a name="accessing-the-declared-object"></a>Dostęp do deklarowanego obiektu

Zmienna, która jest zadeklarowana za pomocą deklaratora uchwytu, zachowuje się jak wskaźnik do obiektu. Jednak punkty zmienne do całego obiektu nie może odnosić się do elementu członkowskiego obiektu, a nie obsługuje arytmetyki wskaźnika. Użyj operatora pośredniego (`*`) dostęp do obiektu i operatora dostępu do elementu członkowskiego strzałka (`->`) do uzyskania dostępu do członka obiektu.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Kompilator używa COM *zliczanie odwołań* mechanizm do określenia, czy obiekt jest już używany i czy można je usunąć. Jest to możliwe, ponieważ obiekt, który jest tworzony na podstawie interfejs Windows Runtime jest w rzeczywistości obiektem COM. Licznik odwołań rośnie, gdy obiekt jest utworzony lub skopiowany i zmniejszony, kiedy obiekt jest ustawiony na wartość null lub poza zakresem. Jeśli licznik odwołań zbliża się do zera, obiekt jest automatycznie i bezzwłocznie usuwany.

Zaletą deklaratora uchwytu jest to, że w modelu COM musi jawnie zarządzać licznikiem odwołań do obiektu, który jest procesem żmudnym i podatne. Oznacza to aby zwiększyć i zmniejszyć liczbę odwołań należy wywołać metody AddRef() obiektu i Release() obiektu. Jednak jeśli obiekt został zadeklarowany za pomocą deklaratora uchwytu, kompilator języka Visual C++ generuje kod, który automatycznie dostosowuje licznika odwołań.

Aby uzyskać informacje na temat sposobu tworzenia wystąpienia obiektu, zobacz [ref nowe](../windows/ref-new-gcnew-cpp-component-extensions.md).

## <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

System używa środowiska CLR *modułu zbierającego elementy bezużyteczne* mechanizm do określenia, czy obiekt jest już używany i czy można je usunąć. Środowisko uruchomieniowe języka wspólnego utrzymuje stertę, do której przydziela obiekty i zastosowań zarządzanych odwołania (zmiennych) w programie wskazujących lokalizację obiektów na stosie. Gdy obiekt nie jest już używany, pamięć, którą zajmował na stercie jest zwalniana. Okresowo moduł odśmiecania pamięci kompaktuje stos w celu lepszego wykorzystania zwolnionej pamięci. Przy kompaktowaniu stosu obiekty można przenosić na stosie, co unieważnia lokalizacje przewidziane przez zarządzane odwołania. Jednak moduł odśmiecania pamięci zna lokalizację wszystkich zarządzanych odwołań i automatycznie aktualizuje je, aby wskazać bieżące położenie obiektów na stosie.

Ponieważ wskaźniki natywne C++ (`*`) i odwołania (`&`) nie są zarządzanymi odniesieniami, moduł odśmiecania pamięci nie może automatycznie zaktualizować adresów, które one wskazują. Aby rozwiązać ten problem, użyj deklaratora uchwytu, aby określić zmienną, która moduł odśmiecania pamięci zna i można będzie automatycznie aktualizować.

W Visual C++ 2002 i Visual C++ 2003 `__gc *` został użyty do deklarowania obiektów na stosie zarządzanym.  `^` Zastępuje `__gc *` w nowej składni.

Aby uzyskać więcej informacji, zobacz [porady: deklarowanie dojść w typach natywnych](../dotnet/how-to-declare-handles-in-native-types.md).

### <a name="examples"></a>Przykłady

W tym przykładzie przedstawiono sposób tworzenia wystąpienia typu odwołania na stosie zarządzanym.  Ten przykład pokazuje również, że można zainicjować dojście w innym, co spowoduje dwa odwołania do tego samego obiektu na stercie zarządzanej, zebranych elementów bezużytecznych. Należy zauważyć, że przypisanie [nullptr](../windows/nullptr-cpp-component-extensions.md) do określonego dojścia nie oznacza obiektu do wyrzucania elementów bezużytecznych.

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

Poniższy przykład pokazuje sposób deklarowania dojścia do obiektu w zarządzanym stosie, gdzie typ obiektu jest typem wartości spakowanej. Przykład pokazuje także sposób uzyskiwania typ wartości z obiektu w ramce.

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

Ten przykład pokazuje, że typowe idiom języka C++ użycia `void*` wskaźnik, aby wskazywał dowolny obiekt został zastąpiony `Object^`, który ma dojścia do każdej klasy odniesienia. Pokazuje również, że wszystkie typy, takie jak tablice i pełnomocnicy, mogą być konwertowane na uchwyt obiektu.

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

Niniejszy przykład pokazuje, że można usunąć uchwyt i czy członek jest dostępny za pośrednictwem usuniętego uchwytu odwołania.

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

Ten przykład pokazuje, że odwołania natywnego (`&`) nie można powiązać z **int** składowej typu zarządzanego jako **int** mogą być przechowywane w stosie zebranych w pamięci i odwołania natywne nie śledzą Przenoszenie obiektu w zarządzanym stosie. Poprawka jest używana do zmiennej lokalnej lub zmienić `&` do `%`, dzięki czemu odwołaniem śledzącym.

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

— Opcja kompilatora: `/clr`

## <a name="see-also"></a>Zobacz też

[Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)<br/>
[Operator odwołania śledzenia](../windows/tracking-reference-operator-cpp-component-extensions.md)