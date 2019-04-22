---
title: Semantyka stosu języka C++ dla typów odwołań
ms.date: 11/04/2016
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
ms.openlocfilehash: 69771de120dc413496a3b7b0613e51a13d208e22
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772608"
---
# <a name="c-stack-semantics-for-reference-types"></a>Semantyka stosu języka C++ dla typów odwołań

Przed Visual C++ 2005, wystąpienia typu referencyjnego można można tworzyć tylko za pomocą `new` operatora, który utworzył obiekt w pamięci zbierane sterty. Teraz można jednak utworzyć wystąpienia typu referencyjnego przy użyciu tej samej składni, którego używasz do utworzenia wystąpienia typu natywnego w stosie. Dlatego nie trzeba używać [ref new, gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) do utworzenia obiektu typu referencyjnego. A gdy obiekt wykracza poza zakres, kompilator wywołuje destruktor obiektu.

## <a name="remarks"></a>Uwagi

Podczas tworzenia wystąpienia typu referencyjnego, używając semantyki stosu, kompilator wewnętrznie tworzenia wystąpienia na stercie zebranych wyrzucania elementów (przy użyciu `gcnew`).

Kiedy podpisu lub zwracany typ funkcji obejmuje wystąpienia typu referencyjnego przez wartość, funkcja zostanie oznaczona w metadanych, które wymagają specjalnej obsługi (z modreq). To specjalnej obsługi jest obecnie świadczona wyłącznie przez klientów Visual C++. inne języki aktualnie nie obsługują konsumencki funkcji lub dane, których używa typów referencyjnych utworzonych za pomocą semantyka stosu.

Jednym z powodów używania `gcnew` (dynamiczna alokacja) zamiast stosu semantyki będzie, jeśli typ ma destruktor nie. Również typów odwołań utworzonych za pomocą semantyka stosu w sygnaturach funkcji nie jest możliwe, jeśli chcesz, aby funkcje do użycia przez języki inne niż Visual C++.

Kompilator nie wygeneruje konstruktora kopiującego dla typu referencyjnego. W związku z tym Jeśli zdefiniujesz funkcję, która używa typu odwołania przez wartość w podpisie, należy zdefiniować konstruktora kopiującego dla typu odwołania. Konstruktora kopiującego dla typu odwołania, ma podpis następującą postać: `R(R%){}`.

Kompilator nie wygeneruje operator przypisania domyślny dla typu odwołania. Operator przypisania pozwala utworzyć obiekt przy użyciu semantyka stosu i zainicjować go z istniejącym obiektem utworzone za pomocą semantyka stosu. Operator przypisania dla typu odwołania, ma podpis następującą postać: `void operator=( R% ){}`.

Jeśli używasz semantyka stosu dla typów odwołań danego typu destruktor zwalnia zasoby o znaczeniu krytycznym, nie trzeba jawnie wywołać destruktor (lub zadzwoń `delete`). Aby uzyskać więcej informacji dotyczących destruktorów w typach odwołań, zobacz [destruktory i finalizatory w sposób: Definiowanie oraz stosowanie klas i struktur (C++sposób niezamierzony)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

Operator przypisania generowane przez kompilator będzie śledzić zwykły standardowe reguły języka C++ z następującymi dodatkami:

- Wszelkie dane niestatycznych elementów członkowskich, którego typem jest dojścia do typu odwołania, będzie skrócona skopiowanych (traktowane jak element członkowski danych niestatyczna, którego typ jest wskaźnikiem typu).

- Wszelkie element członkowski danych niestatycznych którego typ jest typem wartości będzie płytka skopiowane.

- Wszelkie element członkowski danych niestatycznych którego typ jest wystąpieniem typu referencyjnego wywoła wywołanie konstruktora kopiującego typ odwołania.

Kompilator zapewnia również `%` operatora jednoargumentowego do konwertowania wystąpienia typu referencyjnego utworzone za pomocą semantyka stosu na jej typ podstawowy uchwyt.

Następujące typy odwołań nie są dostępne do użytku z programem semantyka stosu:

- [delegate (C++ Component Extensions)](../extensions/delegate-cpp-component-extensions.md)

- [Tablice](../extensions/arrays-cpp-component-extensions.md)

- <xref:System.String>

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład kodu pokazuje sposób deklarowania wystąpień typów referencyjnych z semantyką stosu, jak operator przypisania i działa Konstruktor kopiowania i jak zainicjować odwołanie śledzenia z typem referencyjnym, utworzony za pomocą semantyka stosu.

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
