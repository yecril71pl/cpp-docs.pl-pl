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
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0619585a0a5b59ffb6b8cfbe22e7930909369b23
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386758"
---
# <a name="component-extensions-for-runtime-platforms"></a>Component Extensions dla platform środowiska uruchomieniowego

Visual C++ zapewnia rozszerzeń językowych, aby ułatwić programowanie platform środowiska uruchomieniowego. Za pomocą C + +/ CX, można programować aplikacje uniwersalne platformy Windows i składników, kompilowane do kodu natywnego. Chociaż można utworzyć aplikacji platformy uniwersalnej Windows, programowanie bezpośrednio w odniesieniu do interfejsów COM środowiska wykonawczego Windows, za pomocą C + +/ CX, można pracować z konstruktorów, wyjątki i innych nowoczesne idiomy programowania w języku C++. Aby włączyć programowania C++ w zarządzanym środowisku wykonywania na platformie .NET, można użyć C + +/ interfejsu wiersza polecenia.

### <a name="two-runtimes-one-set-of-extensions"></a>Dwa środowiska uruchomieniowe, zestaw rozszerzeń

C + +/ CX jest podzbiorem C + +/ interfejsu wiersza polecenia. Dla rozszerzeń, które są wspólne dla C + +/ CX i C + +/ CLI, semantyka zależą od tego, czy celem jest środowisko uruchomieniowe języka wspólnego (CLR) lub środowiska wykonawczego Windows. Aby skompilować aplikację do uruchamiania w środowisku uruchomieniowym Windows, należy określić `/ZW` — opcja kompilatora. Aby skompilować je do uruchomienia na środowisko CLR, należy określić `/clr` — opcja kompilatora. Te przełączniki są ustawiane automatycznie, gdy używasz programu Visual Studio, aby utworzyć projekt.

Aby uzyskać więcej informacji na temat tworzenia aplikacji uniwersalnych platformy Windows w języku C++, zobacz [plan for Windows aplikacji środowiska wykonawczego przy użyciu języka C++](https://msdn.microsoft.com/library/windows/apps/hh700360.aspx).

C + +/ CLI rozszerza standard ISO/ANSI C++ i jest zdefiniowana w obszarze Ecma C + +/ interfejsu wiersza polecenia Standard. Aby uzyskać więcej informacji, zobacz [programowania .NET w języku C + +/ interfejsu wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="data-type-keywords"></a>Słowa kluczowe typu danych

Rozszerzenia językowe obejmują *agregacji słowa kluczowe*, służą do słów kluczowych, które składają się z dwoma tokenami rozdzielonych biały znak. Tokeny może mieć jeden znaczenie, gdy są one używane oddzielnie i innym znaczenie, gdy są one używane razem. Na przykład wyraz "ref" jest identyfikatorem zwykłe i słowo "class" jest słowem kluczowym, która deklaruje klasy natywnej. Ale kiedy te wyrazy są łączone w celu formularza **klasy referencyjnej**, wynikowy — słowo kluczowe agregacji deklaruje jednostki, która jest znany jako *klasy środowiska uruchomieniowego*.

Rozszerzenia również obejmować *kontekstową* słów kluczowych. Słowo kluczowe jest traktowany jako kontekstowej, w zależności od rodzaju instrukcję, która zawiera on i jego położenie w tej instrukcji. Na przykład token "property" może być identyfikator lub je zadeklarować specjalny rodzaj składowej klasy publicznej.

Poniższa tabela zawiera listę słów kluczowych w rozszerzenie języka C++.

|Słowo kluczowe|Kontekstowa|Cel|Tematy pomocy|
|-------------|-----------------------|-------------|---------------|
|**Klasa REF**<br /><br /> **Struktura REF**|Nie|Deklaruje klasę.|[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)|
|**Klasa wartości**<br /><br /> **Struktura wartości**|Nie|Deklaruje klasę wartości.|[Klasy i struktury](../windows/classes-and-structs-cpp-component-extensions.md)|
|**Klasa interfejsu**<br /><br /> **Struktura interfejsu**|Nie|Deklaruje interfejsu.|[Klasa interfejsu](../windows/interface-class-cpp-component-extensions.md)|
|**Klasa wyliczeniowa**<br /><br /> **Struktura wyliczenia**|Nie|Deklaruje wyliczenie.|[Klasa wyliczeniowa](../windows/enum-class-cpp-component-extensions.md)|
|**właściwość**|Tak|Deklaruje właściwości.|[właściwość](../windows/property-cpp-component-extensions.md)|
|**delegate**|Tak|Deklaruje delegata.|[delegate (C++ Component Extensions)](../windows/delegate-cpp-component-extensions.md)|
|**event**|Tak|Deklaruje zdarzenie.|[event](../windows/event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>Specyfikatory przesłonięć

Następujące słowa kluczowe służy do kwalifikowania zastąpienie zachowania tworzenia wartości pochodnych. Mimo że **nowe** — słowo kluczowe nie jest rozszerzeniem języka c++, ta opcja jest wyświetlana w tym miejscu, ponieważ może służyć w dodatkowy kontekst. Niektóre specyfikatory również są prawidłowe dla natywnej programowania. Aby uzyskać więcej informacji, zobacz [porady: deklarowanie specyfikatorów zastąpienia w kompilacjach kodu natywnego (C + +/ interfejsu wiersza polecenia)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Słowo kluczowe|Kontekstowa|Cel|Tematy pomocy|
|-------------|-----------------------|-------------|---------------|
|**abstract**|Tak|Wskazuje, że funkcji lub klasy abstrakcyjnej.|[abstract](../windows/abstract-cpp-component-extensions.md)|
|**new**|Nie|Wskazuje, że funkcja nie jest przesłonięciem wersją klasy bazowej.|[New (nowe gniazdo w vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Tak|Wskazuje, że metoda musi być przesłonięciem wersję klasy podstawowej.|[override](../windows/override-cpp-component-extensions.md)|
|**sealed**|Tak|Zapobiega używana jako klay bazowe klasy.|[sealed](../windows/sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Słowa kluczowe dla typów ogólnych

Następujące słowa kluczowe zostały dodane do obsługi typów ogólnych. Aby uzyskać więcej informacji, zobacz [ogólne](../windows/generics-cpp-component-extensions.md).

|Słowo kluczowe|Kontekstowa|Cel|
|-------------|-----------------------|-------------|
|**Ogólny**|Nie|Deklaruje typu ogólnego.|
|**gdzie**|Tak|Określa ograniczenia, które są stosowane do parametru typu ogólnego.|

## <a name="miscellaneous-keywords"></a>Różne słów kluczowych

Następujące słowa kluczowe zostały dodane do rozszerzeń języka C++.

|Słowo kluczowe|Kontekstowa|Cel|Tematy pomocy|
|-------------|-----------------------|-------------|---------------|
|**finally**|Tak|Określa domyślne zachowanie handlings wyjątku.|[Obsługa wyjątków](../windows/exception-handling-cpp-component-extensions.md)|
|**for each, in**|Nie|Wylicza elementów kolekcji.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|Nie|Przydziela typy w stercie zebranych elementów bezużytecznych. Użyj zamiast **nowe** i **Usuń**.|[REF new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**nowe REF**|Tak|Przydziela typów środowiska wykonawczego Windows. Użyj zamiast **nowe** i **Usuń**.|[REF new, gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)|
|**InitOnly**|Tak|Wskazuje, że element członkowski może być inicjowane tylko w deklaracji lub w konstruktorze statycznym.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**literał**|Tak|Tworzy zmienną literału.|[literał](../windows/literal-cpp-component-extensions.md)|
|**nullptr**|Nie|Wskazuje, że dojście lub wskaźnik nie wskazuje na obiekt.|[nullptr](../windows/nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Konstrukcje szablonu

Następujące konstrukcji języka są implementowane jako szablon, zamiast jako słowa kluczowe. Jeśli określisz `/ZW` — opcja kompilatora, są zdefiniowane w `lang` przestrzeni nazw. Jeśli określisz `/clr` — opcja kompilatora, są zdefiniowane w `cli` przestrzeni nazw.

|Słowo kluczowe|Cel|Tematy pomocy|
|-------------|-------------|---------------|
|**Tablica**|Deklaruje tablicę.|[Tablice](../windows/arrays-cpp-component-extensions.md)|
|**pomocą interior_ptr**|(Tylko CLR) Punkty danych w typ odwołania.|[interior_ptr (C++/CLI)](../windows/interior-ptr-cpp-cli.md)|
|**pin_ptr**|(Tylko CLR) Wskazuje typy odwołań CLR, aby tymczasowo pominąć system wyrzucania elementów bezużytecznych.|[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)|
|**przedstawienie operacji safe_cast**|Określa i wykonuje metodę optymalne rzutowania, typu środowiska uruchomieniowego.|[przedstawienie operacji safe_cast](../windows/safe-cast-cpp-component-extensions.md)|
|**TypeID**|(Tylko CLR) Pobiera <xref:System.Type?displayProperty=fullName> obiekt, który opisuje dany typ lub obiekt.|[TypeID](../windows/typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Deklaratory

Następujący typ deklaratory poinstruować środowiska uruchomieniowego do automatycznego zarządzania okresem istnienia i usuwanie istnienia przydzielonych obiektów.

|Operator|Cel|Tematy pomocy|
|--------------|-------------|---------------|
|`^`|Deklaruje dojścia do obiektu; oznacza to, wskaźnik do obiektu Windows Runtime lub CLR, są automatycznie usuwane, gdy go nie jest już możliwe.|[Operator uchwytu do obiektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Deklaruje odwołanie śledzenia; oznacza to, że odwołanie do obiektu Windows Runtime lub CLR, są automatycznie usuwane, gdy nie jest już można używać.|[Operator odwołania śledzenia](../windows/tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Dodatkową konstrukcje i Tematy pokrewne

W tej sekcji przedstawiono dodatkowe konstrukcje programowania i tematy, które odnoszą się do środowiska CLR.

|Temat|Opis|
|-----------|-----------------|
|[__identifier (C++/CLI)](../windows/identifier-cpp-cli.md)|(Windows Runtime i środowiska CLR) Umożliwia korzystanie z słów kluczowych jako identyfikatorów.|
|[Listy zmiennych argumentów (...) (C++/CLI)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows Runtime i środowiska CLR) Włącza funkcję do wykonania zmienną liczbę argumentów.|
|[Odpowiedniki typów natywnych języka C++ w programie .NET Framework (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Zawiera listę typów CLR, które są używane zamiast typów całkowitych C++.|
|[Obiekt AppDomain](../cpp/appdomain.md) **__declspec** modyfikator|**__declspec** modyfikator zezwalający na użycie istnienia zmiennych globalnych i statycznych dla domeny appdomain.|
|[Rzutowania w stylu języka C z/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)|W tym artykule opisano, jak rzutowań w stylu C są interpretowane.|
|[Wywołanie __clrcall](../cpp/clrcall.md) konwencji wywoływania|Wskazuje CLS CLR konwencji wywoływania.|
|`__cplusplus_cli`|[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)|
|[Atrybuty niestandardowe](../windows/custom-attributes-cpp.md)|W tym artykule opisano sposób definiowania atrybutów CLR.|
|[Obsługa wyjątków](../windows/exception-handling-cpp-component-extensions.md)|Zawiera omówienie obsługi wyjątków.|
|[Jawne przesłonięcia](../windows/explicit-overrides-cpp-component-extensions.md)|Pokazuje, jak zastąpić dowolne elementy członkowskie funkcji elementów członkowskich.|
|[Przyjazne zestawy (C++)](../dotnet/friend-assemblies-cpp.md)|W tym artykule omówiono, jak zestaw klienta można dostęp do wszystkich typów w składniku zestawu.|
|[Konwersja boxing](../windows/boxing-cpp-component-extensions.md)|Pokazuje warunków w wartości, które są opakowany typów.|
|[Obsługa cech typu w kompilatorze](../windows/compiler-support-for-type-traits-cpp-component-extensions.md)|W tym artykule omówiono, jak wykrywać właściwości typów w czasie kompilacji.|
|[zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) dyrektywy pragma|Pokazuje, jak zarządzane i niezarządzane funkcje mogą współistnieć w tym samym module.|
|[proces](../cpp/process.md) **__declspec** modyfikator|**__declspec** modyfikator zezwalający na to, że zmiennych globalnych i statycznych istnieją na proces.|
|[Odbicie (C++/CLI)](../dotnet/reflection-cpp-cli.md)|Pokazuje informacje typu run-time w wersji środowiska CLR.|
|[Ciąg](../windows/string-cpp-component-extensions.md)|W tym artykule omówiono kompilatora konwersja z literałów ciągów do <xref:System.String>.|
|[Przekazywanie dalej typu (C++/CLI)](../windows/type-forwarding-cpp-cli.md)|Włącza przepływ typu w zestawie wysyłanie do innego zestawu. Dzięki temu kod klienta nie musi być ponownie kompilowane.|
|[Atrybuty zdefiniowane przez użytkownika](../windows/user-defined-attributes-cpp-component-extensions.md)|Pokazuje atrybuty zdefiniowane przez użytkownika.|
|[#using — dyrektywa](../preprocessor/hash-using-directive-cpp.md)|Importuje zestawy zewnętrzne.|
|[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)|Wyjaśnia dokumentacji oparty na składni XML kodu za pomocą  [ /doc (Przetwarzaj komentarze dokumentacji) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>Zobacz też

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)