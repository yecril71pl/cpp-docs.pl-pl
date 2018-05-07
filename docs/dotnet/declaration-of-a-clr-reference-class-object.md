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
ms.openlocfilehash: 12cead3a142c69da56390ca6f5bf32cecc3b0075
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="declaration-of-a-clr-reference-class-object"></a>Deklaracja obiektu klasy odwołania CLR
Składnia służąca do deklarowanie i utworzenia wystąpienia obiektu typu klasy odwołania zmienił się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 W zarządzanych rozszerzeń obiektu typu klasy odwołania jest zadeklarowana przy użyciu składni wskaźnika ISO C++, z opcjonalnym użyciem `__gc` — słowo kluczowe z lewej strony gwiazdy (`*`). Na przykład poniżej przedstawiono różne odwołania deklaracji obiektu typu klasy w ramach składni zarządzanych rozszerzeń:  
  
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
  
 W obszarze nowej składni deklaracji obiektu typu klasy odwołania przy użyciu nowego tokenu deklaratywne (`^`) nazywane formalnie *śledzenie uchwytu* i bardziej nieformalnego jako *hat*. (Przymiotnik śledzenia oznacza, że typ referencyjny znajduje się w stercie CLR i można w związku z tym niezauważalnie przenosić lokalizacje podczas kompaktowania sterty w pamięci kolekcji. Śledzenie dojścia niewidocznie jest aktualizowana w czasie wykonywania. Są dwa podobne pojęcia *odwołanie śledzące* (`%`) i *wskaźnik wewnętrzny* (`interior_ptr<>`), który omówiono w [semantyka typów wartości](../dotnet/value-type-semantics.md).  
  
 Głównych powodów, aby przenieść składni deklaratywnej w kierunku od ponownemu składni wskaźnika ISO C++ są następujące:  
  
-   Użycie składni wskaźnika nie pozwalały przeciążone operatory stosowane bezpośrednio do obiektu odwołania. Zamiast jeden musiał wywołać operatora przy użyciu nazwy wewnętrznych, takich jak `rV1->op_Addition(rV2)` zamiast bardziej intuicyjne `rV1+rV2`.  
  
-   Liczba operacji wskaźnika, takich jak rzutowanie i wskaźnik arytmetyczny, nie jest dozwolone dla obiektów przechowywanych w pamięci zebranych stosu. Pojęcia lepsze dojścia śledzenia stanowi uchwycenie natury typu odwołania CLR.  
  
 `__gc` Modyfikator w dojściu do śledzenia nie jest konieczne i nie jest obsługiwany. Użyj samego obiektu nie ulega zmianie; nadal uzyskuje dostęp do elementów członkowskich za pomocą operatora wyboru elementu członkowskiego wskaźnika (`->`). Na przykład w tym miejscu jest powyższego przykładu kodu rozszerzeń zarządzanych przetłumaczyć nowej składni:  
  
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
 W zarządzanych rozszerzeń istnienie dwóch `new` wyrażenia, aby przydzielić między sterty natywnych i zarządzanych został przede wszystkim przezroczysty. Prawie wszystkie wystąpienia kompilator jest w stanie używać kontekstu w celu ustalenia, czy można przydzielić pamięci sterty natywnego lub zarządzanego. Na przykład  
  
```  
Button *button1 = new Button; // OK: managed heap  
int *pi1 = new int;           // OK: native heap  
Int32 *pi2 = new Int32;       // OK: managed heap  
```  
  
 Jeśli nie chcesz, aby alokacja sterty kontekstowe, może kierować kompilatora przy użyciu jednej `__gc` lub `__nogc` — słowo kluczowe. W nowej składni oddzielne rodzaj dwa nowe wyrażenia jest jawnie wraz z wprowadzeniem `gcnew` — słowo kluczowe. Na przykład poprzednie trzy deklaracje wyglądać w następujący sposób w nowej składni:  
  
```  
Button^ button1 = gcnew Button;        // OK: managed heap  
int * pi1 = new int;                   // OK: native heap  
Int32^ pi2 = gcnew Int32; // OK: managed heap  
```  
  
 Oto inicjowanie rozszerzeń zarządzanych `Form1` zadeklarowane elementy członkowskie w poprzedniej sekcji:  
  
```  
void InitializeComponent() {  
   components = new System::ComponentModel::Container();  
   button1 = new System::Windows::Forms::Button();  
   myDataGrid = new DataGrid();  
  
   button1->Click +=   
      new System::EventHandler(this, &Form1::button1_Click);  
}  
```  
  
 W tym miejscu jest tej samej inicjacji zmienione do nowej składni. Należy pamiętać, że hat nie jest wymagany dla typu odwołania, gdy nie jest elementem docelowym `gcnew` wyrażenia.  
  
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
 W nowej składni `0` już reprezentuje adres null, ale jest traktowana jako liczba całkowita, taka sama jak `1`, `10`, lub `100`. Nowy token specjalne reprezentuje wartość null dla odwołania do śledzenia. Na przykład w zarządzanych rozszerzeń, możemy zainicjować typem referencyjnym, aby rozwiązać żadnego obiektu w następujący sposób:  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 W nowej składni inicjowania ani przypisanie wartości typ `Object` powoduje, że niejawnej konwersji boxing tego typu wartości. W nowej składni zarówno `obj` i `obj2` są inicjowane zająć opakowanego obiektów Int32 zawierający wartości 0 i 1, odpowiednio. Na przykład:  
  
```  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
```  
  
 W związku z tym w celu wykonywania Jawne inicjowanie, przypisywania i porównanie śledzenie dojścia do wartości null, należy użyć nowego słowa kluczowego `nullptr`.  Poprawne wersji oryginalnego przykładu wygląda następująco:  
  
```  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to a Int32^  
Object ^ obj2 = 1;  
```  
  
 Stwarza to nieco przenoszenia istniejącego kodu do nowej składni. Rozważmy na przykład deklaracji klasy następujące wartości:  
  
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
  
 W tym miejscu zarówno `args` i `env` są typy referencyjne CLR. Inicjowanie tych dwóch elementów członkowskich do `0` w konstruktorze nie ulegają zmianie w przejścia do nowej składni. Zamiast musi zostać zmieniona na `nullptr`:  
  
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
  
 Podobnie, testuje względem tych członków, ich porównanie `0` musi również zostać zmieniony do porównania elementy członkowskie, które `nullptr`. Oto składni zarządzanych rozszerzeń:  
  
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
  
 Oto poprawki, zastępując każdego `0` wystąpienia z `nullptr`. Narzędzie Translacja pomaga w tej transformacji automatyzując wiele, jeśli nie wszystkie wystąpienia, w tym użycie `NULL` makra.  
  
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
  
 `nullptr` Jest konwertowany na wskaźnik lub śledzenia typem uchwytu, ale nie jest podwyższany do typu całkowitego. Na przykład w następujący zestaw inicjalizacji `nullptr` jest prawidłowe tylko jako początkowej wartości do dwóch pierwszych.  
  
```  
// OK: we set obj and pstr to refer to no object  
Object^ obj = nullptr;  
char*   pstr = nullptr; // 0 would also work here  
  
// Error: no conversion of nullptr to 0  
int ival = nullptr;  
```  
  
 Podobnie podany zestaw przeciążonej metody, takie jak następujące:  
  
```  
void f( Object^ ); // (1)  
void f( char* );   // (2)  
void f( int );     // (3)  
```  
  
 Wywołania z `nullptr` literału, takie jak wymienione poniżej  
  
```  
// Error: ambiguous: matches (1) and (2)  
f(  nullptr );  
```  
  
 jest niejednoznaczny, ponieważ `nullptr` zgodny zarówno dojścia śledzenia i wskaźnik i nie ma żadnych preferencją jeden typ przez innych. (Ta sytuacja wymaga jawnego rzutowania w celu odróżnienia).  
  
 Wywołania z `0` dokładnie zgodny wystąpienia (3):  
  
```  
// OK: matches (3)  
f( 0 );  
```  
  
 Ponieważ `0` jest typu integer. Zostały `f(int)` nie istnieje, wywołanie jednoznacznie dopasuje `f(char*)` za pomocą konwersji standardowej. Regułami dopasowywania nadać priorytet dokładnego dopasowania za pośrednictwem standardowych konwersji. W przypadku braku dokładnego dopasowania konwersja standardowa mają pierwszeństwo nad niejawna konwersja boxing typów wartości. Właśnie dlatego niejednoznaczności nie nie istnieje.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Operator uchwytu do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)   
 [nullptr](../windows/nullptr-cpp-component-extensions.md)