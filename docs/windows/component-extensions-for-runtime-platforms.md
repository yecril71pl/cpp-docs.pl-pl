---
title: Component Extensions dla platform środowiska uruchomieniowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- Visual C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e60a1285f54de6b1cbfe311d4d9cbbc547785176
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="component-extensions-for-runtime-platforms"></a>Component Extensions dla platform środowiska uruchomieniowego
Visual C++ udostępnia rozszerzenia języka aby program dla platform środowiska uruchomieniowego. Przy użyciu języka C + +/ CX, można program aplikacji platformy uniwersalnej systemu Windows i składników, które skompiluj do kodu natywnego. Mimo że można utworzyć aplikacji platformy uniwersalnej systemu Windows przez programowanie bezpośrednio przed interfejsy COM środowiska wykonawczego systemu Windows przy użyciu języka C + +/ CX, możesz pracować z konstruktorów wyjątków i innych modern C++ programowania idioms. Aby włączyć programowania w języku C++ w środowisku wykonania kodu zarządzanego na platformie .NET, można użyć C + +/ CLI.  
  
 **Dwóch środowisk uruchomieniowych jeden zestaw rozszerzeń**  
  
 C + +/ CX jest podzbiorem C + +/ CLI. Dla rozszerzeń, które są wspólne dla C + +/ CX i C + +/ CLI, semantykę zależą czy przeznaczonych dla środowisko uruchomieniowe języka wspólnego (CLR) lub środowiska uruchomieniowego systemu Windows. Aby skompilować aplikację do uruchamiania na środowiska uruchomieniowego systemu Windows, określ **/ZW** — opcja kompilatora. Aby skompilować go w CLR, określ **/CLR** — opcja kompilatora. Te przełączniki są ustawiane automatycznie podczas tworzenia projektu za pomocą programu Visual Studio.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia aplikacji platformy uniwersalnej systemu Windows w języku C++, zobacz [aplikacji plan za dla środowiska wykonawczego systemu Windows przy użyciu języka C++](http://msdn.microsoft.com/library/windows/apps/hh700360.aspx).  
  
 C + +/ CLI rozszerza norma ISO/ANSI C++ i jest zdefiniowany w obszarze Ecma C + +/ CLI standardowa. Aby uzyskać więcej informacji, zobacz [.NET Programowanie w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
## <a name="data-type-keywords"></a>Słowa kluczowe typu danych  
 Rozszerzenia językowe obejmują *agregacji słowa kluczowe*, będące słów kluczowych, które składają się z dwóch tokeny oddzielone biały znak. Tokeny mogą zawierać jeden znaczenia, gdy są one używane niezależnie i innego znaczenia, gdy są one używane razem. Na przykład wyraz "ref" jest identyfikatorem zwykłej i word "class" jest słowem kluczowym, który deklaruje klasy natywnej. Gdy te słowa, które są połączone do formularza, ale `ref class`, wynikowy — słowo kluczowe agregacji deklaruje jednostki, która jest nazywany *klasa środowiska uruchomieniowego*.  
  
 Rozszerzenia również obejmować *kontekstowa* słów kluczowych. Słowo kluczowe jest traktowany jako kontekstowa w zależności od rodzaju instrukcji, która zawiera i umieszczania jej w tej instrukcji. Na przykład token "property" może być identyfikator lub mogą zadeklarować specjalny rodzaj elementu członkowskiego klasy publicznej.  
  
 Poniższa tabela zawiera listę słów kluczowych rozszerzenia języka C++.  
  
|Słowo kluczowe|Kontekstowe|Cel|Tematy pomocy|  
|-------------|-----------------------|-------------|---------------|  
|`ref class`<br /><br /> `ref struct`|Nie|Deklaruje klasy.|[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`value class`<br /><br /> `value struct`|Nie|Deklaruje klasą wartości.|[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)|  
|`interface class`<br /><br /> `interface struct`|Nie|Deklaruje interfejsu.|[klasy interfejsu](../windows/interface-class-cpp-component-extensions.md)|  
|`enum class`<br /><br /> `enum struct`|Nie|Deklaruje wyliczenie.|[Enum — klasa](../windows/enum-class-cpp-component-extensions.md)|  
|`property`|Tak|Deklaruje właściwości.|[właściwość](../windows/property-cpp-component-extensions.md)|  
|`delegate`|Tak|Deklaruje delegata.|[delegate (C++ Component Extensions)](../windows/delegate-cpp-component-extensions.md)|  
|`event`|Tak|Deklaruje zdarzenie.|[event](../windows/event-cpp-component-extensions.md)|  
  
## <a name="override-specifiers"></a>Specyfikatory przesłonięć  
 Można użyć następujących słów kluczowych na kwalifikować się zastąpienie zachowania w operacji wyprowadzenia. Mimo że `new` — słowo kluczowe nie jest rozszerzeniem C++, znajduje się w tym miejscu ponieważ mogą być używane w kontekście dodatkowe. Niektóre specyfikatory również są prawidłowe dla natywnej programowania. Aby uzyskać więcej informacji, zobacz [porady: deklarowanie specyfikatorów zastąpienia w kompilacjach macierzystych (C + +/ CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
|Słowo kluczowe|Kontekstowe|Cel|Tematy pomocy|  
|-------------|-----------------------|-------------|---------------|  
|`abstract`|Tak|Wskazuje, że funkcje lub klasy abstrakcyjnej.|[abstract](../windows/abstract-cpp-component-extensions.md)|  
|`new`|Nie|Wskazuje, że funkcja nie jest przesłonięciem wersja klasy podstawowej.|[New (nowe gniazdo w vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|  
|`override`|Tak|Wskazuje, że metoda musi być zastąpienia wersji klasy podstawowej.|[override](../windows/override-cpp-component-extensions.md)|  
|`sealed`|Tak|Klasy uniemożliwia użycie jako klasy podstawowe.|[sealed](../windows/sealed-cpp-component-extensions.md)|  
  
## <a name="keywords-for-generics"></a>Słowa kluczowe dla typów ogólnych  
 Poniższe słowa kluczowe zostały dodane do obsługi typów ogólnych. Aby uzyskać więcej informacji, zobacz [ogólne](../windows/generics-cpp-component-extensions.md).  
  
|Słowo kluczowe|Kontekstowe|Cel|  
|-------------|-----------------------|-------------|  
|`generic`|Nie|Deklaruje typu ogólnego.|  
|`where`|Tak|Określa ograniczenia, które są stosowane do parametru typu ogólnego.|  
  
## <a name="miscellaneous-keywords"></a>Różne słowa kluczowe  
 Poniższe słowa kluczowe zostały dodane do rozszerzenia C++.  
  
|Słowo kluczowe|Kontekstowe|Cel|Tematy pomocy|  
|-------------|-----------------------|-------------|---------------|  
|`finally`|Tak|Wskazuje zachowanie handlings wyjątku.|[Obsługa wyjątków](../windows/exception-handling-cpp-component-extensions.md)|  
|`for each, in`|Nie|Wylicza elementów kolekcji.|[for each, in](../dotnet/for-each-in.md)|  
|`gcnew`|Nie|Przydziela typy w stercie zbierane pamięci. Użyj zamiast `new` i `delete`.|[REF new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`ref new`|Tak|Przydziela typem środowiska wykonawczego systemu Windows. Użyj zamiast `new` i `delete`.|[REF new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|  
|`initonly`|Tak|Wskazuje, że element członkowski mogą być inicjowane tylko w deklaracji lub w konstruktorze statycznym.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|  
|`literal`|Tak|Tworzy zmienną literału.|[Literału](../windows/literal-cpp-component-extensions.md)|  
|`nullptr`|Nie|Wskazuje, że dojście lub wskaźnik nie wskazuje na obiekt.|[nullptr](../windows/nullptr-cpp-component-extensions.md)|  
  
## <a name="template-constructs"></a>Konstrukcje szablonu  
 Następujące konstrukcji języka są implementowane jako szablon, a nie jako słowa kluczowe. Jeśli określisz **/ZW** — opcja kompilatora, są zdefiniowane w `lang` przestrzeni nazw. Jeśli określisz **/CLR** — opcja kompilatora, są zdefiniowane w `cli` przestrzeni nazw.  
  
|Słowo kluczowe|Cel|Tematy pomocy|  
|-------------|-------------|---------------|  
|`array`|Deklaruje tablicę.|[Tablice](../windows/arrays-cpp-component-extensions.md)|  
|`interior_ptr`|(Tylko CLR) Punkty danych w typu referencyjnego.|[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)|  
|`pin_ptr`|(Tylko CLR) Wskazuje typy referencyjne CLR tymczasowo pominąć systemu wyrzucanie elementów bezużytecznych.|[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)|  
|`safe_cast`|Określa i wykonuje metodę optymalne rzutowanie typu środowiska uruchomieniowego.|[safe_cast](../windows/safe-cast-cpp-component-extensions.md)|  
|`typeid`|(Tylko CLR) Pobiera <xref:System.Type?displayProperty=fullName> obiektu, który opisuje podanego typu lub obiektu.|[TypeID](../windows/typeid-cpp-component-extensions.md)|  
  
## <a name="declarators"></a>Deklaratory  
 Następujące deklaratorów typu poinstruuj środowiska uruchomieniowego automatycznie zarządzać okres istnienia i usuwanie obiektów przydzielone.  
  
|Operator|Cel|Tematy pomocy|  
|--------------|-------------|---------------|  
|`^`|Deklaruje uchwyt do obiektu. oznacza to, że wskaźnik do obiektu środowiska wykonawczego systemu Windows lub CLR, który jest automatycznie usuwana, gdy nie jest już używać.|[Operator uchwytu do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|  
|`%`|Deklaruje odwołanie śledzące; oznacza to, że odwołanie do obiektu środowiska wykonawczego systemu Windows lub CLR, który jest automatycznie usuwana, gdy nie jest już używać.|[Operator odwołania śledzenia](../windows/tracking-reference-operator-cpp-component-extensions.md)|  
  
## <a name="additional-constructs-and-related-topics"></a>Konstrukcje dodatkowe i Tematy pokrewne  
 Ta sekcja zawiera informacje o dodatkowych narzędzi programistycznych i tematy, które odnoszą się do środowiska CLR.  
  
|Temat|Opis|  
|-----------|-----------------|  
|[__identifier (C++/CLI)](../windows/identifier-cpp-cli.md)|(Środowisko wykonawcze systemu Windows i CLR) Umożliwia użycie słowa kluczowe jako identyfikatorów.|  
|[Listy zmiennych argumentów (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Środowisko wykonawcze systemu Windows i CLR) Włącza funkcję zmienną liczbę argumentów.|  
|[Odpowiedniki typów natywnych języka C++ w programie .NET Framework (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Wyświetla listę typów CLR, które są używane zamiast typów całkowitych C++.|  
|[elementu AppDomain](../cpp/appdomain.md) `__declspec` modyfikator|`__declspec` Modyfikator, która nakłada się, że zmienne statyczne i globalnych istnieje dla domeny appdomain.|  
|[Rzutowania w stylu języka C z/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|Opisuje sposób interpretowania rzutowania w stylu języka C.|  
|[__clrcall](../cpp/clrcall.md) konwencji wywoływania|Wskazuje zgodne CLR konwencję wywołania.|  
|`__cplusplus_cli`|[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)|  
|[Atrybuty niestandardowe](../windows/custom-attributes-cpp.md)|Opisuje sposób zdefiniowania własnych atrybuty CLR.|  
|[Obsługa wyjątków](../windows/exception-handling-cpp-component-extensions.md)|Omówienie obsługi wyjątków.|  
|[Jawne przesłonięcia](../windows/explicit-overrides-cpp-component-extensions.md)|Pokazuje, jak funkcje Członkowskie mogą zastąpić dowolne elementy członkowskie.|  
|[Przyjazne zestawy (C++)](../dotnet/friend-assemblies-cpp.md)|W tym artykule omówiono, jak zestaw klienta można uzyskać dostęp do wszystkich typów w zestawie składnika.|  
|[OPAKOWYWANIE](../windows/boxing-cpp-component-extensions.md)|Pokazuje, w wartości, które są opakowany typy warunków.|  
|[Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|W tym artykule omówiono sposób wykryć właściwości typów w czasie kompilacji.|  
|[zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) dyrektywy pragma|Pokazuje, jak zarządzane i niezarządzane funkcje mogą współistnieć w tym samym module.|  
|[proces](../cpp/process.md) `__declspec` modyfikator|`__declspec` Modyfikator, która nakłada się, że zmienne statyczne i globalnych istnieją na proces.|  
|[Odbicie (C++/CLI)](../dotnet/reflection-cpp-cli.md)|Pokazuje informacje typu run-time wersję środowiska CLR.|  
|[Ciąg](../windows/string-cpp-component-extensions.md)|W tym artykule omówiono konwersji kompilatora literałów ciągu do <xref:System.String>.|  
|[Przekazywanie dalej typu (C++/CLI)](../windows/type-forwarding-cpp-cli.md)|Umożliwia przenoszenie typu w zestawie wysyłki do innego zestawu, aby kod klienta nie ma być ponownie kompilowane.|  
|[Atrybuty zdefiniowane przez użytkownika](../windows/user-defined-attributes-cpp-component-extensions.md)|Pokazuje atrybuty zdefiniowane przez użytkownika.|  
|[#using — dyrektywa](../preprocessor/hash-using-directive-cpp.md)|Importuje zestawy zewnętrzne.|  
|[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)|Wyjaśniono dokumentacji XML na podstawie kodu za pomocą  [ /doc (przetwarzanie komentarzy dokumentacji) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [.NET programowania w języku C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)