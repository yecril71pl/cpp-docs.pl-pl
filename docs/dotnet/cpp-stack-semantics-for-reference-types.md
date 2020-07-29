---
title: Semantyka stosu języka C++ dla typów odwołań
ms.date: 11/04/2016
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
ms.openlocfilehash: 886d0d16d8b81364078db5604ab10d8dcc3fa561
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197842"
---
# <a name="c-stack-semantics-for-reference-types"></a>Semantyka stosu języka C++ dla typów odwołań

W starszych wersjach programu Visual Studio 2005 wystąpienie typu referencyjnego można utworzyć tylko przy użyciu **`new`** operatora, który utworzył obiekt na stertie zebranych elementów bezużytecznych. Można jednak teraz utworzyć wystąpienie typu referencyjnego przy użyciu tej samej składni, która będzie używana do tworzenia wystąpienia typu natywnego na stosie. Dlatego nie trzeba używać [ref new, gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) do tworzenia obiektu typu referencyjnego. A gdy obiekt wykracza poza zakres, kompilator wywołuje destruktor obiektu.

## <a name="remarks"></a>Uwagi

Podczas tworzenia wystąpienia typu odwołania przy użyciu semantyki stosu kompilator wykonuje wewnętrznie Tworzenie wystąpienia na stosie odzyskiwanych elementów bezużytecznych (przy użyciu **`gcnew`** ).

Gdy sygnatura lub typ zwracany funkcji zawiera wystąpienie typu odwołania przez wartość, funkcja zostanie oznaczona w metadanych jako wymagającej specjalnej obsługi (z modreq). Ta specjalna obsługa jest obecnie świadczona tylko przez Visual C++ klientów; inne języki nie obsługują obecnie korzystania z funkcji ani danych, które używają typów referencyjnych utworzonych przy użyciu semantyki stosu.

Jedną z przyczyn użycia **`gcnew`** (Alokacja dynamiczna) zamiast semantyki stosu będzie, jeśli typ nie ma destruktora. Ponadto używanie typów odwołań utworzonych z semantyką stosu w sygnaturach funkcji nie będzie możliwe, jeśli chcesz, aby funkcje były używane przez języki inne niż Visual C++.

Kompilator nie będzie generował konstruktora kopiującego dla typu referencyjnego. W związku z tym, jeśli zdefiniujesz funkcję, która używa typu odwołania przez wartość w podpisie, musisz zdefiniować Konstruktor kopiujący dla typu referencyjnego. Konstruktor kopiujący dla typu referencyjnego ma podpis w następującej postaci: `R(R%){}` .

Kompilator nie będzie generował domyślnego operatora przypisania dla typu referencyjnego. Operator przypisania umożliwia utworzenie obiektu przy użyciu semantyki stosu i zainicjowanie go z istniejącym obiektem utworzonym przy użyciu semantyki stosu. Operator przypisania dla typu referencyjnego ma sygnaturę następującej formy: `void operator=( R% ){}` .

Jeśli destruktor typu zwalnia zasoby krytyczne i używasz semantyki stosu dla typów referencyjnych, nie musisz jawnie wywołać destruktora (lub wywołaniu **`delete`** ). Aby uzyskać więcej informacji na temat destruktorów w typach referencyjnych, zobacz [destruktory i finalizatory w instrukcje: Definiowanie i korzystanie z klas i struktur (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Generowany przez kompilator operator przypisania będzie przestrzegać zwykłych standardowych reguł języka C++ z następującymi dodatkami:

- Wszystkie niestatyczne składowe danych, których typ to dojście do typu referencyjnego, zostaną skopiowane na płytki (traktowane jak niestatyczny element członkowski danych, którego typem jest wskaźnik).

- Wszystkie niestatyczne składowe danych, których typem jest typ wartości, zostaną skopiowane na płytki.

- Każdy niestatyczny element członkowski danych, którego typem jest wystąpienie typu referencyjnego, wywoła wywołanie konstruktora kopiującego typu odwołania.

Kompilator udostępnia również `%` operator jednoargumentowy do konwersji wystąpienia typu odwołania utworzonego przy użyciu semantyki stosu do jego bazowego typu uchwytu.

Następujące typy referencyjne nie są dostępne do użycia z semantyką stosu:

- [delegate (C++ Component Extensions)](../extensions/delegate-cpp-component-extensions.md)

- [Macierze](../extensions/arrays-cpp-component-extensions.md)

- <xref:System.String>

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład kodu pokazuje, jak zadeklarować wystąpienia typów odwołań z semantyką stosu, jak działa operator przypisania i Konstruktor kopiujący oraz jak zainicjować odwołanie śledzenia z typem referencyjnym utworzonym przy użyciu semantyki stosu.

### <a name="code"></a>Kod

```cpp
// stack_semantics_for_reference_types.cpp
// compile with: /clr
ref class R {
public:
   int i;
   R(){}

   // assignment operator
   void operator=(R% r) {
      i = r.i;
   }

   // copy constructor
   R(R% r) : i(r.i) {}
};

void Test(R r) {}   // requires copy constructor

int main() {
   R r1;
   r1.i = 98;

   R r2(r1);   // requires copy constructor
   System::Console::WriteLine(r1.i);
   System::Console::WriteLine(r2.i);

   // use % unary operator to convert instance using stack semantics
   // to its underlying handle
   R ^ r3 = %r1;
   System::Console::WriteLine(r3->i);

   Test(r1);

   R r4;
   R r5;
   r5.i = 13;
   r4 = r5;   // requires a user-defined assignment operator
   System::Console::WriteLine(r4.i);

   // initialize tracking reference
   R % r6 = r4;
   System::Console::WriteLine(r6.i);
}
```

### <a name="output"></a>Dane wyjściowe

```Output
98
98
98
13
13
```

## <a name="see-also"></a>Zobacz także

[Klasy i struktury](../extensions/classes-and-structs-cpp-component-extensions.md)
