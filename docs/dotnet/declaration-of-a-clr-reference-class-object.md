---
title: Deklaracja obiektu klasy odwołania CLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- types [C++], reference types
- reference types, CLR
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f3e8ec6407e12d0c26331d45dc1659277feed016
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444583"
---
# <a name="declaration-of-a-clr-reference-class-object"></a>Deklaracja obiektu klasy odwołania CLR

Składnia do deklarowania i tworzenia wystąpienia obiektu typu klasy odwołania został zmieniony z zarządzanych rozszerzeń języka C++ do Visual C++.

W zarządzanych rozszerzeń odwołanie do obiektu typu klasy jest zadeklarowana za pomocą składni wskaźnika ISO C++ z opcjonalnym użyciem `__gc` — słowo kluczowe z lewej strony gwiazdka (`*`). Na przykład Oto różnych odwołania deklaracje obiektów typu klasy, w obszarze składni zarządzanych rozszerzeń:

```
public __gc class Form1 : public System::Windows::Forms::Form {
private:
   System::ComponentModel::Container __gc *components;
   Button __gc *button1;
   DataGrid __gc *myDataGrid;
   DataSet __gc *myDataSet;

   void PrintValues( Array* myArr ) {
      System::Collections::IEnumerator* myEnumerator =
         myArr->GetEnumerator();

      Array *localArray;
      myArr->Copy(myArr, localArray, myArr->Length);
   }
};
```

W ramach nowej składni zadeklarować obiektu typu klasy odwołania przy użyciu nowego tokenu deklaratywne (`^`) nazywane formalnie *śledzenie uchwytu* oraz bardziej nieformalnie *hat*. (Przymiotnik śledzenia oznacza, że znajduje się w stosie CLR typu odwołania i można w związku z tym niezauważalnie przenosić lokalizacji podczas kompaktowania sterty kolekcji wyrzucania elementów. Śledzenie dojścia sposób niewidoczny dla użytkownika jest aktualizowana w czasie wykonywania. Dwoma pojęciami podobne są *odwołanie śledzenia* (`%`) i *wskaźnika wewnętrznego* (`interior_ptr<>`), który omówiono w [semantyka typów wartości](../dotnet/value-type-semantics.md).

Głównych powodów, aby przenieść składni deklaratywnej od ponownemu składni wskaźnika ISO C++ są następujące:

- Użycie składni wskaźnika nie pozwalały przeciążonych operatorów, aby być stosowane bezpośrednio do obiektu odwołania. Zamiast jednego było wywołać operator przy użyciu nazwy wewnętrzne, takie jak `rV1->op_Addition(rV2)` zamiast bardziej intuicyjne `rV1+rV2`.

- Liczba operacji wskaźnika, takich jak rzutowania i wskaźnik arytmetyczny, nie jest dozwolona dla obiektów przechowywanych w pamięci zbierane sterty. Śledzenie dojścia lepsze pojęcie stanowi uchwycenie natury typu referencyjnego CLR.

`__gc` Modyfikator w dojściu do śledzenia nie jest konieczne i nie jest obsługiwana. Użycie sam obiekt nie jest zmieniany; nadal uzyskuje dostęp do elementów członkowskich za pomocą operatora wyboru składowej wskaźnika (`->`). Na przykład Oto poprzedni przykład kodu zarządzanych rozszerzeń przetłumaczyć nowej składni:

```
public ref class Form1: public System::Windows::Forms::Form {
private:
   System::ComponentModel::Container^ components;
   Button^ button1;
   DataGrid^ myDataGrid;
   DataSet^ myDataSet;

   void PrintValues( Array^ myArr ) {
      System::Collections::IEnumerator^ myEnumerator =
         myArr->GetEnumerator();

      Array ^localArray;
      myArr->Copy(myArr, localArray, myArr->Length);   }
};
```

## <a name="dynamic-allocation-of-an-object-on-the-clr-heap"></a>Dynamiczna alokacja obiektów na stercie CLR

W zarządzanych rozszerzeń istnienie dwóch `new` wyrażenia, aby przydzielić między natywnego i zarządzanego stosu była w dużej mierze przejrzyste. W prawie wszystkich wystąpień kompilator będzie mógł używać kontekstu w celu ustalenia, czy można przydzielić pamięci sterty natywnej lub zarządzanych. Na przykład

```
Button *button1 = new Button; // OK: managed heap
int *pi1 = new int;           // OK: native heap
Int32 *pi2 = new Int32;       // OK: managed heap
```

Gdy nie mają Alokacja sterty kontekstowych, może kierować kompilatora z oboma `__gc` lub `__nogc` — słowo kluczowe. W nowej składni oddzielne charakter dwa nowe wyrażenia jest jawnie wraz z wprowadzeniem `gcnew` — słowo kluczowe. Na przykład poprzednie trzy deklaracje wyglądać następująco w nowej składni:

```
Button^ button1 = gcnew Button;        // OK: managed heap
int * pi1 = new int;                   // OK: native heap
Int32^ pi2 = gcnew Int32; // OK: managed heap
```

Oto inicjowanie zarządzanych rozszerzeń `Form1` elementów członkowskich zadeklarowanych w poprzedniej sekcji:

```
void InitializeComponent() {
   components = new System::ComponentModel::Container();
   button1 = new System::Windows::Forms::Button();
   myDataGrid = new DataGrid();

   button1->Click +=
      new System::EventHandler(this, &Form1::button1_Click);
}
```

Oto inicjowania tych samych zmienione do nowej składni. Należy pamiętać, że hat nie jest wymagany dla typu odwołania, gdy jest ona elementem docelowym `gcnew` wyrażenia.

```
void InitializeComponent() {
   components = gcnew System::ComponentModel::Container;
   button1 = gcnew System::Windows::Forms::Button;
   myDataGrid = gcnew DataGrid;

   button1->Click +=
      gcnew System::EventHandler( this, &Form1::button1_Click );
}
```

## <a name="a-tracking-reference-to-no-object"></a>Odwołanie śledzące do żadnego obiektu

W nowej składni `0` już reprezentuje adres o wartości null, ale jest traktowana jako liczba całkowita, taka sama jak `1`, `10`, lub `100`. Nowy token specjalne reprezentuje wartość null dla odwołania śledzenia. Na przykład w zarządzanych rozszerzeń możemy zainicjować typem referencyjnym, aby rozwiązać żaden obiekt w następujący sposób:

```
// OK: we set obj to refer to no object
Object * obj = 0;

// Error: no implicit boxing
Object * obj2 = 1;
```

W nowej składni inicjowania ani przypisania wartości wpisz, aby `Object` powoduje, że niejawnej konwersji boxing tego typu wartości. W nowej składni zarówno `obj` i `obj2` są inicjowane na rozwiązany spakowany obiektów Int32 zawierający wartości 0 i 1, odpowiednio. Na przykład:

```
// causes the implicit boxing of both 0 and 1
Object ^ obj = 0;
Object ^ obj2 = 1;
```

W związku z tym, aby można było wykonać Jawne inicjowanie, przypisywania i porównanie śledzenie dojścia do wartości null, użyj nowe słowo kluczowe `nullptr`.  Poprawna wersja oryginalnego przykładu wygląda następująco:

```
// OK: we set obj to refer to no object
Object ^ obj = nullptr;

// OK: we initialize obj2 to a Int32^
Object ^ obj2 = 1;
```

Komplikuje to nieco Przenoszenie istniejącego kodu do nowej składni. Na przykład rozważmy następującą deklarację klasy wartości:

```
__value struct Holder {
   Holder( Continuation* c, Sexpr* v ) {
      cont = c;
      value = v;
      args = 0;
      env = 0;
   }

private:
   Continuation* cont;
   Sexpr * value;
   Environment* env;
   Sexpr * args __gc [];
};
```

W tym miejscu zarówno `args` i `env` są typami odwołań CLR. Inicjowanie te dwa elementy członkowskie do `0` w konstruktorze nie uległy zmianie w okresie przejściowym do nowej składni. Przeciwnie, musi zostać zmieniona na `nullptr`:

```
value struct Holder {
   Holder( Continuation^ c, Sexpr^ v )
   {
      cont = c;
      value = v;
      args = nullptr;
      env = nullptr;
   }

private:
   Continuation^ cont;
   Sexpr^ value;
   Environment^ env;
   array<Sexpr^>^ args;
};
```

Podobnie, testy względem tych członków, porównywanie ich `0` musi również zostać zmieniony do porównywania elementów członkowskich do `nullptr`. Oto składni zarządzanych rozszerzeń:

```
Sexpr * Loop (Sexpr* input) {
   value = 0;
   Holder holder = Interpret(this, input, env);

   while (holder.cont != 0) {
      if (holder.env != 0) {
         holder=Interpret(holder.cont,holder.value,holder.env);
      }
      else if (holder.args != 0) {
         holder =
         holder.value->closure()->
         apply(holder.cont,holder.args);
      }
   }

   return value;
}
```

Poniżej przedstawiono przegląd, zastępując każdego `0` wystąpienia z `nullptr`. Narzędzie do tłumaczenia ułatwia to przekształcenie, automatyzując wiele, jeśli nie używać wszystkich wystąpień, w tym `NULL` makra.

```
Sexpr ^ Loop (Sexpr^ input) {
   value = nullptr;
   Holder holder = Interpret(this, input, env);

   while ( holder.cont != nullptr ) {
      if ( holder.env != nullptr ) {
         holder=Interpret(holder.cont,holder.value,holder.env);
      }
      else if (holder.args != nullptr ) {
         holder =
         holder.value->closure()->
         apply(holder.cont,holder.args);
      }
   }

   return value;
}
```

`nullptr` Jest konwertowana na dowolny typ wskaźnika lub śledzenia dojście, ale nie jest promowany do typu całkowitego. Na przykład, w następujący zestaw inicjalizacje `nullptr` jest prawidłowy tylko jako wartością początkową potrzeba do dwóch pierwszych.

```
// OK: we set obj and pstr to refer to no object
Object^ obj = nullptr;
char*   pstr = nullptr; // 0 would also work here

// Error: no conversion of nullptr to 0
int ival = nullptr;
```

Podobnie biorąc pod uwagę przeciążona zestaw metod, takie jak następujące:

```
void f( Object^ ); // (1)
void f( char* );   // (2)
void f( int );     // (3)
```

Wywołania z `nullptr` literału, podobny do następującego

```
// Error: ambiguous: matches (1) and (2)
f(  nullptr );
```

jest niejednoznaczny, ponieważ `nullptr` odpowiada śledzenie dojścia i wskaźnik, a nie preferencją dla jednego typu na drugi. (Ta sytuacja wymaga jawnego rzutowania w celu odróżnienia).

Wywołania z `0` dokładnie zgodne wystąpienie (3):

```
// OK: matches (3)
f( 0 );
```

Ponieważ `0` jest typu Integer. Zostały `f(int)` nieobecna, wywołanie jednoznacznie dopasuje `f(char*)` za pomocą konwersji standardowej. Reguł dopasowania nadać priorytet dokładne dopasowanie za pośrednictwem standardowych konwersji. W przypadku braku dokładne dopasowanie konwersja standardowa jest pierwszeństwo przed niejawnej konwersji boxing typu wartości. Właśnie dlatego nie ma żadnych niejednoznaczności.

## <a name="see-also"></a>Zobacz też

[Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[Operator uchwytu do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)<br/>
[nullptr](../windows/nullptr-cpp-component-extensions.md)