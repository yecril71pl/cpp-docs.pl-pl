---
title: System typów języka C++ (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 553c0ed6-77c4-43e9-87b1-c903eec53e80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82c017b7048c8b62f58068d22b8efefd72f31d4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="c-type-system-modern-c"></a>System typów języka C++ (Modern C++)
Pojęcie *typu* jest bardzo ważna w języku C++. Zwracana wartość każdej zmiennej, argumentu funkcji oraz funkcji musi mieć typ, aby mogła zostać skompilowana. Ponadto, kompilator niejawnie nadaje typ każdemu wyrażeniu (w tym wartości literału), zanim zostanie on oceniony. Oto przykłady typów `int` do przechowywania wartości całkowite `double` do przechowywania wartości zmiennoprzecinkowych (znanej także jako *skalarne* typów danych), lub klasy biblioteki standardowej [std::basic_string](../standard-library/basic-string-class.md) do przechowywania tekstu. Można utworzyć własny typ, definiując `class` lub `struct`. Typ określa wielkość pamięci, która zostanie zaalokowana dla zmiennej (lub wyniku wyrażenia), rodzaje wartości, które mogą być przechowywane w tej zmiennej, sposób interpretacji tych wartości (jako wzorców bajtów) oraz operacje, jakie mogą zostać na nich wykonane. Ten artykuł zawiera nieformalny przegląd głównych funkcji systemu typów C++.  
  
## <a name="terminology"></a>Terminologia  
 **Zmienna**: łącze symboliczne nazwa ilości danych, aby nazwa służy do uzyskiwania dostępu do danych odwołuje się do przez cały zakres kodu, w którym jest zdefiniowana. W języku C++ *zmiennej* zazwyczaj służy do odwoływania się do wystąpień typów skalarnych danych, natomiast wystąpień inne typy są zwykle nazywane *obiektów*.  
  
 **Obiekt**: dla uproszczenia i spójności, w tym artykule używany jest termin *obiektu* do odwoływania się do dowolnego wystąpienia klasy lub struktury i gdy jest używany w tym sensie, ogólne obejmuje wszystkie typy, nawet zmienne skalarne.  
  
 **Typ POD** (zwykły starych danych): Ta kategoria nieformalne typów danych w języku C++ odwołuje się do typów, które są skalarne (patrz sekcja typów podstawowych) lub *klasy POD*. Klasa POD nie ma żadnych statycznych składowych danych, które nie są również POD, i nie ma zdefiniowanych przez użytkownika konstruktorów, zdefiniowanych przez użytkownika destruktorów ani zdefiniowanych przez użytkownika operatorów przypisania. Klasa POD nie ma też żadnych funkcji wirtualnych, nie ma klasy podstawowej ani żadnych prywatnych lub chronionych niestatycznych składowych danych. Typy POD są często używane do wymiany danych zewnętrznych, na przykład przy użyciu modułu napisanego w języku C (który ma tylko typy POD).  
  
## <a name="specifying-variable-and-function-types"></a>Określanie typów zmiennych i funkcji  
 C++ jest *silnie typizowane* języka i stanowi również *statycznie wpisany*; każdy obiekt ma typ i który typu nigdy nie zmiany (nie należy mylić z obiektami dane statyczne).   
**Gdy zadeklarować zmiennej** w kodzie, należy jawnie określić jego typ, lub użyj `auto` — słowo kluczowe nakazać kompilatora do ustalenia typu z inicjatora.   
**Gdy zadeklarowania funkcji** w kodzie, należy określić typ każdego argumentu i jego wartość zwracaną, lub `void` Jeśli wartość nie zostanie zwrócony przez funkcję. Wyjątek występuje podczas korzystania z szablonów funkcji, które pozwalają na argumenty dowolnego typu.  
  
 Po pierwszym zdeklarowaniu zmiennej nie można później zmienić jej typu. Możesz jednak skopiować wartość zmiennej lub wartość zwracaną przez funkcję do innej zmiennej innego typu. Takie operacje są nazywane *konwersje typów*, które są czasami konieczne, ale są również potencjalne źródła danych, utratę lub niepoprawności.  
  
 Kiedy deklarujesz zmienną typu POD, stanowczo zalecamy jej inicjalizację, co oznacza nadanie jej początkowej wartości. Dopóki zmienna nie zostanie zainicjalizowana, ma ona wartość „śmieciową”, składającą się z bitów, które poprzednio znajdowały się w tej lokalizacji pamięci. Jest to ważny aspekt C++ warty zapamiętania, szczególnie jeżeli praca odbywała się wcześniej w innym języku, który automatycznie obsługuje inicjalizację. Gdy deklarujesz zmienną typu innego niż klasa POD, konstruktor obsługuje inicjalizację.  
  
 Poniższy przykład pokazuje kilka prostych deklaracji zmiennych z opisami każdej z nich. W przykładzie pokazano również, jak kompilator używa informacji o typie, aby umożliwiać lub uniemożliwiać pewne kolejne operacje na zmiennej.  
  
```cpp  
  
int result = 0;              // Declare and initialize an integer.  
double coefficient = 10.8;   // Declare and initialize a floating   
                             // point value.  
auto name = "Lady G.";       // Declare a variable and let compiler   
                             // deduce the type.  
auto address;                // error. Compiler cannot deduce a type   
                             // without an intializing value.  
age = 12;                    // error. Variable declaration must  
                             // specify a type or use auto!  
result = "Kenny G.";         // error. Can’t assign text to an int.  
string result = "zero";      // error. Can’t redefine a variable with  
                             // new type.  
int maxValue;                // Not recommended! maxValue contains   
                             // garbage bits until it is initialized.  
  
```  
  
## <a name="fundamental-built-in-types"></a>Podstawowe (wbudowane) typy  
 W odróżnieniu do innych języków, C++ nie ma uniwersalnego typu bazowego, z którego wywodzą się wszystkie inne typy. Implementacja języka Visual C++ zawiera wiele *typy podstawowe*, znanej także jako *wbudowanych typów*. Obejmuje to typy liczbowe takich jak `int`, `double`, `long`, `bool`, wraz z `char` i `wchar_t` typy znaki ASCII i UNICODE, odpowiednio. Większość podstawowych typów (z wyjątkiem `bool`, `double`, `wchar_t` i powiązanych typów) ma wszystkie niepodpisane wersje, które modyfikować zakres wartości, które mogą być przechowywane w zmiennej. Na przykład `int`, który przechowuje całkowita 32-bitowe, można reprezentują wartości od -2,147,483,648 do 2 147 483 647. `unsigned int`, Który także jest przechowywany jako 32-bitowej, można przechowywać wartość z zakresu od 0 do 4 294 967 295. Całkowita liczba możliwych wartości w każdym przypadku jest taka sama, zmienia się tylko zakres.  
  
 Podstawowe typy są rozpoznawane przez kompilator, który posiada wbudowane reguły rządzące tym, jakie operacje można na nich wykonywać i jak mogą być konwertowane na inne typy podstawowe. Aby uzyskać pełną listę wbudowanych typów i ich rozmiar i limity liczbowego, zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).  
  
 Na poniższej ilustracji przedstawiono względne wielkości typów wbudowanych:  
  
 ![Wyrażony w bajtach rozmiar wbudowane&#45;w typach](../cpp/media/built-intypesizes.png "inTYpeSizes wbudowane")  
  
 Poniższa tabela wymienia najczęściej używane typy podstawowe:  
  
|Typ|Rozmiar|Komentarz|  
|----------|----------|-------------|  
|int|4 bajty|Wybór domyślny dla wartości całkowitych.|  
|double|8 bajtów|Wybór domyślny dla wartości zmiennopozycyjnych.|  
|bool|1 bajt|Przedstawia wartości, które mogą być prawdziwe lub fałszywe.|  
|char|1 bajt|Używaj dla znaków ASCII w starszych ciągach typu C lub obiektach std::string, które nigdy nie będą musiały zostać skonwertowane na UNICODE.|  
|wchar_t|2 bajty|Przedstawia wartości znaku „szerokiego”, które mogą być zakodowane w formacie UNICODE (UTF-16 w systemie Windows, inne systemy operacyjne mogą się różnić). Jest to typ znak, który jest używany w parametrach typu `std::wstring`.|  
|unsigned char|1 bajt|C++ nie ma wbudowanej `byte` typu.  Używaj unsigned char, aby reprezentować wartość bajtową.|  
|unsigned int|4 bajty|Wybór domyślny dla flag bitowych.|  
|long long|8 bajtów|Przedstawia bardzo duże wartości całkowitoliczbowe.|  
  
## <a name="the-void-type"></a>Typ void (pusty).  
 `void` Typ to specjalne; nie można zadeklarować zmiennej typu `void`, ale można zadeklarować zmiennej typu `void *` (wskaźnik do `void`), która czasami jest niezbędne podczas przydzielania pamięci (wyrażeniami bez typu). Jednak wskaźniki do `void` są nie bezpieczne i zwykle ich użycie jest zalecane w nowoczesnych wersji języka C++. W deklaracji funkcji `void` zwracana wartość oznacza, że funkcja nie zwraca wartości, co jest typowe i dopuszczalne korzystanie z `void`. Podczas funkcje wymagane języka C, które mają parametrów do deklarowania `void` na liście parametrów, na przykład `fou(void)`, takie rozwiązanie jest niezalecane w nowoczesnych wersji języka C++ i powinien być zadeklarowany jako `fou()`. Aby uzyskać więcej informacji, zobacz [konwersje i bezpieczeństwo typów](../cpp/type-conversions-and-type-safety-modern-cpp.md).  
  
## <a name="const-type-qualifier"></a>kwalifikator typu const  
 Dowolny wbudowany lub zdefiniowany przez użytkownika typ może być zakwalifikowany według słowa kluczowego const. Ponadto funkcje Członkowskie mogą być `const`-kwalifikowaną i nawet `const`-przeciążony. Wartość `const` typu nie można modyfikować po jego inicjowania.  
  
```cpp  
  
const double PI = 3.1415;  
PI = .75 //Error. Cannot modify const variable.  
  
```  
  
 `const` Kwalifikator jest bardzo często używane w deklaracjach funkcji i zmiennej i "const" jest jest ważne pojęcia języka C++; zasadniczo oznacza korzystanie z `const` w celu zagwarantowania, w czasie kompilacji, że wartości nie są modyfikowane przypadkowo . Aby uzyskać więcej informacji, zobacz [const](../cpp/const-cpp.md).  
  
 A `const` typu różni się od wersji z systemem innym niż stała; na przykład `const int` jest typem distinct z `int`. Można użyć języka C++ `const_cast` operatora w tych rzadkich przypadkach, gdy należy usunąć *stałość* zmiennych. Aby uzyskać więcej informacji, zobacz [konwersje i bezpieczeństwo typów](../cpp/type-conversions-and-type-safety-modern-cpp.md).  
  
## <a name="string-types"></a>Typy ciągu  
 Mówiąc ściślej języka C++ nie ma wbudowanej ciąg typu; `char` i `wchar_t` sklepu pojedynczy znaki — należy zadeklarować tablicę tych typów do przybliżonego określenia ciągu, dodawanie zakończenia wartości null (na przykład ASCII `'\0'`) do jednego elementu tablicy poza ostatni nieprawidłowy znak (nazywane również *Ciąg w stylu języka C*). Ciągi stylu C wymagały znacznie więcej kodu lub korzystania z funkcji zewnętrznej biblioteki obsługującej ciągi. Ale w nowoczesnych wersji języka C++, mamy typy standardowa biblioteka `std::string` (dla 8-bitowych `char`-wpisz ciągi znaków) lub `std::wstring` (do 16-bitowych `wchar_t`— wpisz ciągi znaków). Kontenery standardowa biblioteka C++ można traktować jako typów natywnych ciąg, ponieważ są one częścią standardowych bibliotek, które znajdują się w dowolnym zgodne środowisku kompilacji C++. Po prostu użyć `#include <string>` dyrektywy wprowadzać typy dostępnych w programie. (Jeśli używasz biblioteki ATL lub MFC, klasa CString jest również dostępna, ale nie jest częścią standardowego języka C++.) Używanie tablic zakończonych znakiem zerowym (wcześniej wspomniane ciągi stylu C) jest odradzane w nowoczesnym C++.  
  
## <a name="user-defined-types"></a>Typy definiowane przez użytkownika  
 Podczas definiowania `class`, `struct`, `union`, lub `enum`, tej konstrukcji jest używany w pozostałej części kodu, tak jakby był typem podstawowym. Zajmuje znany obszar w pamięci, a niektóre zasady sposobu, w jaki można go używać, dotyczą sprawdzania w czasie kompilacji i w trakcie uruchomienia, przez cały okres istnienia programu. Główne różnice między głównymi wbudowanymi typami a typami definiowanymi przez użytkownika są następujące:  
  
-   Kompilator nie ma wbudowanej wiedzy o typie zdefiniowanym przez użytkownika. Dowie się typu po pierwszym napotkaniu definicji podczas procesu kompilacji.  
  
-   Ty określasz, jakie operacje mogą zostać przeprowadzone na typie i jak może on zostać przekonwertowany do innych typów, definiując (przez przeciążenie) odpowiednie operatory, albo jako funkcje składowych, albo jako funkcje, które nie są składowymi. Aby uzyskać więcej informacji, zobacz [przeciążanie funkcji](function-overloading.md).  
  
-   Nie muszą zostać statycznie wpisane (zasada, że typ obiektu nigdy nie ulega zmianie). Za pomocą mechanizmów *dziedziczenia* i *polimorfizm*, zmienna zadeklarowany jako typ zdefiniowany przez użytkownika klasy (nazywane wystąpienia obiektu klasy) może mieć inny typ w czasie wykonywania niż w czas kompilacji. Aby uzyskać więcej informacji, zobacz [dziedziczenia](../cpp/inheritance-cpp.md).  
  
## <a name="pointer-types"></a>Typy wskaźnika  
 Sprzed wersje języka C, C++ w dalszym ciągu można zadeklarować zmiennej typu wskaźnika za pomocą specjalnych deklarator `*` (gwiazdkę). Typ wskaźnika przechowuje adres lokalizacji w pamięci, gdzie jest przechowywana rzeczywista wartość danych. W nowoczesnych wersji języka C++, te są określane jako *raw wskaźniki*i są dostępne w kodzie za pomocą specjalne operatory `*` (gwiazdkę) lub `->` (kreska z większą-niż). Ta metoda jest wywoływana *dereferencji*, i które z nich, którego używasz zależy od tego, czy usuwania odwołania wskaźnik do skalarnej lub wskaźnika do elementu członkowskiego w obiekcie. Praca z typami wskaźników od dawna jest jednym z najtrudniejszych i najbardziej dezorientujących aspektów tworzenia programów w C i C++. W tej sekcji opisano niektóre faktów i wskazówki ułatwiające użycie wskaźników raw, jeśli chcesz, aby, ale w nowoczesnych wersji języka C++ jego nie jest już wymagane (lub zalecana) do użycia wskaźników pierwotnych dla obiekt własności na wszystkich z powodu zmiany [wskaźnika inteligentnego](../cpp/smart-pointers-modern-cpp.md) () rejestru na końcu tej sekcji). Nadal jest użyteczne i bezpieczne używanie surowych wskaźników do obserwacji obiektów, ale jeśli musisz użyć ich do własności obiektu, należy to zrobić z ostrożnością i po bardzo starannym rozważeniu sposobu, w jaki obiekty przez nie posiadane są tworzone i niszczone.  
  
 Pierwszą rzeczą, którą należy wiedzieć przy deklarowaniu zmiennej surowego wskaźnika, jest to, że zmienna przydzieli tylko pamięć, która jest niezbędna do przechowania adresu lokalizacji pamięci, do którego odwoła się wskaźnik po wyłuskaniu. Alokacja pamięci dla wartości danych sam (nazywane również *magazynu zapasowego*) nie został jeszcze przydzielony. Innymi słowy, przez zadeklarowanie zmiennej surowego wskaźnika tworzysz zmienną adresu pamięci, a nie zmienną rzeczywistych danych. \Wyłuskanie zmiennej wskaźnika przed upewnieniem się, że zawiera ona prawidłowy adres magazynu zapasowego, spowoduje niezdefiniowane zachowanie (zwykle błąd krytyczny) w programie. Poniższy przykład przedstawia ten rodzaj błędu:  
  
```cpp  
  
int* pNumber;       // Declare a pointer-to-int variable.  
*pNumber = 10;      // error. Although this may compile, it is  
                    // a serious error. We are dereferencing an  
                    // uninitialized pointer variable with no  
                    // allocated memory to point to.  
  
```  
  
 Przykład wyłuskuje typ wskaźnika, bez przydzielania pamięci na przechowywanie rzeczywistych danych całkowitoliczbowych lub prawidłowego przypisanego adresu pamięci. Poniższy kod poprawia te błędy:  
  
```cpp  
  
    int number = 10;          // Declare and initialize a local integer  
                              // variable for data backing store.  
    int* pNumber = &number;   // Declare and initialize a local integer  
                              // pointer variable to a valid memory  
                              // address to that backing store.  
...  
    *pNumber = 41;            // Dereference and store a new value in   
                              // the memory pointed to by  
                              // pNumber, the integer variable called  
                              // "number". Note "number" was changed, not  
                              // "pNumber".  
  
```  
  
 Pamięci lokalnej stosu używa przykład poprawiony kod, aby utworzyć zapasowy magazyn `pNumber` wskazuje. Dla uproszczenia używamy podstawowego typu. W praktyce magazynu zapasowego dla wskaźników są większość typów często zdefiniowane przez użytkownika, które są dynamicznie przydzielane to obszar pamięci o nazwie *sterty* (lub *wolnego magazynu*) przy użyciu `new` — słowo kluczowe wyrażenia (w stylu języka C programowaniu starszej `malloc()` użyto funkcji biblioteki C runtime). Po przydzielone, tych zmiennych są zwykle nazywane obiektów, zwłaszcza, jeśli są one oparte na definicji klasy. Pamięci przydzielonej z `new` muszą zostać usunięte przez odpowiadający `delete` instrukcji (lub, jeśli używasz `malloc()` funkcji można przydzielić go funkcji środowiska wykonawczego języka C `free()`).  
  
 Jednak łatwiej Pamiętaj, aby usunąć dynamicznie przydzielane obiektu — szczególnie w przypadku złożonego kodu, co powoduje, że usterki zasobów o nazwie *przeciek pamięci*. Z tego powodu zdecydowanie odradza się stosowanie surowych wskaźników w nowoczesnym języku C++. Warto prawie zawsze Zawijaj raw wskaźnika w [wskaźnika inteligentnego](../cpp/smart-pointers-modern-cpp.md), który automatycznie spowoduje zwolnienie z pamięci po wywołaniu jego — destruktor (jeśli kod wykracza poza zakres wskaźnika inteligentnego); przy użyciu wskaźniki inteligentne można praktycznie Usuń całą klasy błędów w programach języka C++. W poniższym przykładzie założono `MyClass` jest zdefiniowane przez użytkownika typu, który ma publicznego — metoda `DoSomeWork();`  
  
```cpp  
  
void someFunction() {  
    unique_ptr<MyClass> pMc(new MyClass);  
    pMc->DoSomeWork();  
}  
  // No memory leak. Out-of-scope automatically calls the destructor  
  // for the unique_ptr, freeing the resource.  
  
```  
  
 Aby uzyskać więcej informacji na temat wskaźniki inteligentne, zobacz [wskaźniki inteligentne](../cpp/smart-pointers-modern-cpp.md).  
  
 Aby uzyskać więcej informacji na temat konwersje wskaźników, zobacz [konwersje i bezpieczeństwo typów](../cpp/type-conversions-and-type-safety-modern-cpp.md).  
  
 Aby uzyskać więcej informacji na temat wskaźniki ogólnie rzecz biorąc, zobacz [wskaźniki](../cpp/pointers-cpp.md).  
  
## <a name="windows-data-types"></a>Typy danych Windows  
 W klasycznym Win32 programowania w języku C i C++, większość funkcji używać definicje typów właściwe dla systemu Windows i #define makra (zdefiniowany w `windef.h`) można określić typy parametrów i wartości zwracane. Te typy danych systemu Windows są prawie tylko ze specjalnymi nazwy (aliasy) podane typy wbudowane C/C++. Aby uzyskać pełną listę te definicje typów i definicje preprocesora, zobacz [typów danych systemu Windows](http://msdn.microsoft.com/en-us/4553cafc-450e-4493-a4d4-cb6e2f274d46). Niektóre z tych definicji typów, takie jak HRESULT i LCID, są użyteczne i opisowe. Inne, takie jak INT, nie mają specjalnego znaczenia i są po prostu aliasami dla podstawowych typów C++. Inne typy danych systemu Windows mają nazwy pochodzące z czasów programowania w C i procesorów 16-bitowych. Nie mają one żadnego celu ani znaczenia w przypadku nowoczesnego sprzętu lub systemu operacyjnego. Istnieją również specjalne typy danych skojarzonych z biblioteką środowiska wykonawczego systemu Windows, na liście jako [środowiska wykonawczego systemu Windows podstawowe typy danych](http://msdn.microsoft.com/en-us/b5735851-ec07-48c1-92b4-ca9f768096f6). W nowoczesnym C++, ogólną wytyczną jest preferowanie typów podstawowych języka C++, chyba że typ Windows komunikuje jakieś dodatkowe znaczenie o sposobie interpretowania wartości.  
  
## <a name="more-information"></a>Więcej informacji  
 Aby uzyskać więcej informacji dotyczących typu systemu C++, zobacz następujące tematy.  
  
|||  
|-|-|  
|[Typy wartości](../cpp/value-types-modern-cpp.md)|W tym artykule opisano *typów wartości* oraz problemów dotyczących ich używania.|  
|[Konwersje i bezpieczeństwo typów](../cpp/type-conversions-and-type-safety-modern-cpp.md)|Opisuje typowe problemy przy konwersji typu i pokazuje, jak ich unikać.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
