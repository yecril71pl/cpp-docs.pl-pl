---
title: delegat (C++/CLI i C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 388ccb28c9311b4727199e6b7324771c24c2906d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172441"
---
# <a name="delegate--ccli-and-ccx"></a>delegat (C++/CLI i C++/CX)

Deklaruje typ, który reprezentuje wskaźnik funkcji.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Zarówno Delegaty środowisko wykonawcze systemu Windows, jak i środowisko uruchomieniowe języka wspólnego.

### <a name="remarks"></a>Uwagi

**Delegat** jest kontekstowym słowem kluczowym. Aby uzyskać więcej informacji, zobacz [kontekstowe słowa kluczowe](context-sensitive-keywords-cpp-component-extensions.md).

Aby wykryć w czasie kompilacji, jeśli typ jest delegatem, użyj cechy typu `__is_delegate()`. Aby uzyskać więcej informacji, zobacz [Obsługa kompilatora dla cech typu](compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

C++/CX obsługuje delegatów z następującą składnią.

### <a name="syntax"></a>Składnia

```cpp
access
delegate
return-type
delegate-type-identifier
(
[ parameters ]
)
```

### <a name="parameters"></a>Parametry

*niego*<br/>
obowiązkowe Dostępność delegata, która może być **publiczna** (wartość domyślna) lub **prywatna**. Prototyp funkcji może być również kwalifikowana za pomocą słowa kluczowego **const** lub **volatile** .

*Typ zwracany*<br/>
Zwracany typ prototypu funkcji.

*delegat-Type-Identifier*<br/>
Nazwa zadeklarowanego typu delegata.

*parameters*<br/>
Obowiązkowe Typy i identyfikatory prototypu funkcji.

### <a name="remarks"></a>Uwagi

Użyj *identyfikatora delegata-Type* , aby zadeklarować zdarzenie z tym samym prototypem co delegat. Aby uzyskać więcej informacji, zobacz [delegats (C++/CX)](../cppcx/delegates-c-cx.md).

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Środowisko uruchomieniowe języka wspólnego obsługuje delegatów z poniższą składnią.

### <a name="syntax"></a>Składnia

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>Parametry

*niego*<br/>
obowiązkowe Dostępność delegata poza zestawem może być publiczna lub prywatna.  Wartość domyślna to Private.  W obrębie klasy delegat może mieć dowolny ułatwienia dostępu.

*function_declaration*<br/>
Sygnatura funkcji, która może być powiązana z delegatem. Typem zwracanym delegata może być dowolny typ zarządzany. Ze względu na współdziałanie zaleca się, aby zwracany typ delegata był typem CLS.

Aby zdefiniować niepowiązanego delegata, pierwszy parametr w *function_declaration* powinien być typem wskaźnika **tego** obiektu.

### <a name="remarks"></a>Uwagi

Delegaty są multiemisją: "wskaźnik funkcji" może być powiązany z jedną lub wieloma metodami w klasie zarządzanej. Słowo kluczowe **Delegate** definiuje typ delegata multiemisji z określonym podpisem metody.

Delegat można także powiązać z metodą klasy wartości, taką jak metoda statyczna.

Delegat ma następującą charakterystykę:

- Dziedziczy po `System::MulticastDelegate`.

- Ma konstruktora, który przyjmuje dwa argumenty: wskaźnik do zarządzanej klasy lub wartość NULL (w przypadku powiązania z metodą statyczną) oraz w pełni kwalifikowaną metodę określonego typu.

- Ma metodę o nazwie `Invoke`, której podpis pasuje do zadeklarowanej sygnatury delegata.

Gdy obiekt delegowany jest wywoływany, jego funkcje są wywoływane w kolejności, w jakiej zostały dołączone.

Zwracana wartość delegata jest wartością zwracaną z ostatniej dołączonej funkcji członkowskiej.

Delegaty nie mogą być przeciążone.

Delegaty mogą być powiązane lub niepowiązane.

Podczas tworzenia wystąpienia powiązanego delegata pierwszy argument musi być odwołaniem do obiektu. Drugi argument tworzenia wystąpienia delegata musi być adresem metody obiektu klasy zarządzanej lub wskaźnikiem do metody typu wartości. Drugi argument tworzenia wystąpienia delegata musi mieć nazwę metody z pełną składnią zakresu klasy i zastosować operator address-of.

Podczas tworzenia wystąpienia niepowiązanego delegata pierwszy argument musi być adresem metody obiektu klasy zarządzanej lub wskaźnikiem do metody typu wartości. Argument musi mieć nazwę metody z pełną składnią zakresu klasy i zastosować operator address-of.

Podczas tworzenia delegata do funkcji statycznej lub globalnej jest wymagany tylko jeden parametr: Funkcja (opcjonalnie adres funkcji).

Aby uzyskać więcej informacji na temat delegatów, zobacz

- [Instrukcje: definiowanie obiektów delegowanych (C++/CLI) oraz korzystanie z nich](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [Delegaty ogólne (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>Wymagania

Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład pokazuje, jak zadeklarować, zainicjować i wywołać delegatów.

```cpp
// mcppv2_delegate.cpp
// compile with: /clr
using namespace System;

// declare a delegate
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      Console::WriteLine("in func1 {0}", i);
   }

   void func2(int i) {
      Console::WriteLine("in func2 {0}", i);
   }

   static void func3(int i) {
      Console::WriteLine("in static func3 {0}", i);
   }
};

int main () {
   A ^ a = gcnew A;

   // declare a delegate instance
   MyDel^ DelInst;

   // test if delegate is initialized
   if (DelInst)
      DelInst(7);

   // assigning to delegate
   DelInst = gcnew MyDel(a, &A::func1);

   // invoke delegate
   if (DelInst)
      DelInst(8);

   // add a function
   DelInst += gcnew MyDel(a, &A::func2);

   DelInst(9);

   // remove a function
   DelInst -= gcnew MyDel(a, &A::func1);

   // invoke delegate with Invoke
   DelInst->Invoke(10);

   // make delegate to static function
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);
   StaticDelInst(11);
}
```

```Output
in func1 8

in func1 9

in func2 9

in func2 10

in static func3 11
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)
