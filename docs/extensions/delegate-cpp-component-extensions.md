---
title: Delegowanie (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: eedaf81a52fc28de4a640de7345ff3486c5f4a3a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787390"
---
# <a name="delegate--ccli-and-ccx"></a>Delegowanie (C + +/ CLI i C + +/ CX)

Deklaruje typ, który reprezentuje wskaźnik funkcji.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Środowisko uruchomieniowe Windows i środowisko uruchomieniowe języka wspólnego obsługuje delegatów.

### <a name="remarks"></a>Uwagi

**Delegowanie** jest kontekstowej słowem kluczowym. Aby uzyskać więcej informacji, zobacz [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md).

Aby wykryć w czasie kompilacji, jeśli typ jest delegatem, należy użyć `__is_delegate()` cechy typu. Aby uzyskać więcej informacji, zobacz [Obsługa cech typu w kompilatorze](compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

C + +/ CX obsługuje delegatów przy użyciu następującej składni.

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

*access*<br/>
(opcjonalnie) Dostępność delegata, która może być **publicznych** (ustawienie domyślne) lub **prywatnej**. Prototyp funkcji również może być kwalifikowana za **const** lub **volatile** słów kluczowych.

*zwracany typ*<br/>
Zwracany typ prototypu funkcji.

*delegate-type-identifier*<br/>
Nazwa typu zadeklarowana delegata.

*parameters*<br/>
(Opcjonalnie) Typy i identyfikatory prototypu funkcji.

### <a name="remarks"></a>Uwagi

Użyj *identyfikatora w przypadku typu delegata* Aby zadeklarować zdarzenia o ten sam prototyp jako pełnomocnik. Aby uzyskać więcej informacji, zobacz [obiektów delegowanych (C + +/ CX)](../cppcx/delegates-c-cx.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

Środowisko uruchomieniowe języka wspólnego obsługuje delegatów przy użyciu następującej składni.

### <a name="syntax"></a>Składnia

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>Parametry

*access*<br/>
(opcjonalnie) Dostępność delegata spoza zestawu może być publicznym lub prywatnym.  Wartość domyślna jest prywatny.  Wewnątrz klasy delegata może mieć żadnych ułatwień dostępu.

*function_declaration*<br/>
Podpis funkcji, która może być powiązana z obiektu delegowanego. Zwracany typ delegata może być dowolnego typu zarządzanego. Ze względu na współdziałanie zalecane jest, że zwracany typ delegata być typem ze specyfikacją CLS.

Aby zdefiniować niezwiązanego delegata, pierwszy parametr w *function_declaration* powinien być typem **to** wskaźnik do obiektu.

### <a name="remarks"></a>Uwagi

Obiekty delegowane są multiemisji: "wskaźnik funkcji" może być powiązany z co najmniej jednej metody w klasie zarządzanej. **Delegować** — słowo kluczowe definiuje typ delegata multiemisji za pomocą podpisu określonej metody.

Delegat może być powiązana również metody klasy wartości, takich jak metody statycznej.

Obiekt delegowany ma następujące cechy:

- Dziedziczy `System::MulticastDelegate`.

- Ma on konstruktora, który przyjmuje dwa argumenty: wskaźnik do klasy zarządzanej lub o wartości NULL (w przypadku powiązania na metodę statyczną) i pełną metodą określonego typu.

- Ma metodę o nazwie `Invoke`, którego podpis pasuje zadeklarowane podpis delegata.

Gdy obiekt delegowany jest wywoływany, jego funkcji są wywoływane w kolejności, w której zostały dołączone.

Wartość zwracana przez obiekt delegowany jest wartość zwrotną z jej ostatniej funkcji członkowskiej dołączone.

Delegaci nie mogą być przeciążone.

Delegatów można powiązać lub niepowiązanych.

Podczas tworzenia wystąpienia delegata powiązanej pierwszy argument jest odwołanie do obiektu. Drugi argument wystąpienia delegata są albo być adresem metodę do obiektu klasy zarządzanej lub wskaźnikiem do metody typu wartości. Drugi argument wystąpienia delegata należy nazwę metody z klasy pełnej składni zakresu i zastosowania operatora address-of.

Podczas tworzenia wystąpienia niezwiązanego delegata pierwszy argument jest adres metodę do obiektu klasy zarządzanej lub wskaźnikiem do metody typu wartości. Argument musi nadaj nazwę metody z klasy pełnej składni zakresu i zastosowania operatora address-of.

Podczas tworzenia delegata funkcji statycznych lub globalnych, tylko jeden parametr jest wymagany: — funkcja (opcjonalnie, adres funkcji).

Aby uzyskać więcej informacji na temat obiektów delegowanych zobacz

- [Instrukcje: definiowanie obiektów delegowanych (C++/CLI) oraz korzystanie z nich](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [Delegaty ogólne (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład pokazuje sposób deklarowania, zainicjować i wywoływać delegatów.

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