---
title: Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- what's new [C++], keywords
- what's new [C++], language features
- C++, keywords
- keywords [C++]
- Managed Extensions for C++, replacement syntax
ms.assetid: 1e400ee6-3ac9-4910-a608-9d3d5993e423
ms.openlocfilehash: 66cdd5c42de128b988e9283138745377afddefbc
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787154"
---
# <a name="component-extensions-for-net-and-uwp"></a>Component Extensions dla platformy .NET i platformy uniwersalnej systemu Windows

Standard języka C++ umożliwia kompilatora tych dostawców niestandardowych rozszerzeń języka. Firma Microsoft udostępnia rozszerzenia w celu łatwiejszego nawiązania połączenia w natywnym kodzie C++ kod do kodu, które jest uruchamiane na .NET Framework lub uniwersalnej platformy Windows (UWP). Rozszerzenia .NET są nazywane C + +/ CLI i wygenerować kod, który wykonuje w .NET zarządzanego środowiska wykonawczego, która jest wywoływana środowiska uruchomieniowego języka wspólnego (CLR). Rozszerzenia platformy uniwersalnej systemu Windows są nazywane C + +/ CX, a także tworzyć macierzystego kodu maszynowego.

> [!NOTE]
> W przypadku nowych aplikacji zaleca się za pomocą C + +/ WinRT, a nie C + +/ CX. C + +/ WinRT jest nowy, standard C ++ 17 języka dla interfejsów API środowiska wykonawczego Windows. Firma Microsoft będzie obsługiwać C + +/ CX i WRL, ale zdecydowanie zalecamy, aby użyć nowych aplikacji C + +/ WinRT. Aby uzyskać więcej informacji, zobacz [C + +/ WinRT](/windows/uwp/cpp-and-winrt-apis/index).

### <a name="two-runtimes-one-set-of-extensions"></a>Dwa środowiska uruchomieniowe, zestaw rozszerzeń

C + +/ CLI rozszerza standard ISO/ANSI C++ i jest zdefiniowana w obszarze Ecma C + +/ interfejsu wiersza polecenia Standard. Aby uzyskać więcej informacji, zobacz [programowania .NET w języku C + +/ interfejsu wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

C + +/ CX rozszerzenia są podzbiorem C + +/ interfejsu wiersza polecenia. Mimo że składnia rozszerzenia jest identyczny w większości przypadków, kod, który jest generowany jest zależna od tego, czy należy określić `/ZW` — opcja kompilatora z docelowym platformy uniwersalnej systemu Windows, lub `/clr` możliwość docelowej platformy .NET. Te przełączniki są ustawiane automatycznie, gdy używasz programu Visual Studio, aby utworzyć projekt.

## <a name="data-type-keywords"></a>Słowa kluczowe typu danych

Rozszerzenia językowe obejmują *agregacji słowa kluczowe*, które składają się z dwoma tokenami rozdzielane średnikami biały. Tokeny może mieć jeden znaczenie, gdy są one używane oddzielnie i innym znaczenie, gdy są one używane razem. Na przykład wyraz "ref" jest identyfikatorem zwykłe i słowo "class" jest słowem kluczowym, która deklaruje klasy natywnej. Ale kiedy te wyrazy są łączone w celu formularza **klasy referencyjnej**, wynikowy — słowo kluczowe agregacji deklaruje jednostki, która jest znany jako *klasy środowiska uruchomieniowego*.

Rozszerzenia również obejmować *kontekstową* słów kluczowych. Słowo kluczowe jest traktowany jako kontekstowej, w zależności od rodzaju instrukcję, która zawiera on i jego położenie w tej instrukcji. Na przykład token "property" może być identyfikator lub je zadeklarować specjalny rodzaj składowej klasy publicznej.

Poniższa tabela zawiera listę słów kluczowych w rozszerzenie języka C++.

|Słowo kluczowe|Kontekstowa|Cel|Tematy pomocy|
|-------------|-----------------------|-------------|---------------|
|**Klasa REF**<br /><br /> **Struktura REF**|Nie|Deklaruje klasę.|[Klasy i struktury](classes-and-structs-cpp-component-extensions.md)|
|**Klasa wartości**<br /><br /> **Struktura wartości**|Nie|Deklaruje klasę wartości.|[Klasy i struktury](classes-and-structs-cpp-component-extensions.md)|
|**Klasa interfejsu**<br /><br /> **Struktura interfejsu**|Nie|Deklaruje interfejsu.|[Klasa interfejsu](interface-class-cpp-component-extensions.md)|
|**Klasa wyliczeniowa**<br /><br /> **Struktura wyliczenia**|Nie|Deklaruje wyliczenie.|[Klasa wyliczeniowa](enum-class-cpp-component-extensions.md)|
|**właściwość**|Tak|Deklaruje właściwości.|[właściwość](property-cpp-component-extensions.md)|
|**delegate**|Tak|Deklaruje delegata.|[delegat  (C++/CLI i C++/CX)](delegate-cpp-component-extensions.md)|
|**event**|Tak|Deklaruje zdarzenie.|[event](event-cpp-component-extensions.md)|

## <a name="override-specifiers"></a>Specyfikatory zastąpienia

Następujące słowa kluczowe służy do kwalifikowania zastąpienie zachowania tworzenia wartości pochodnych. Mimo że **nowe** — słowo kluczowe nie jest rozszerzeniem języka c++, ta opcja jest wyświetlana w tym miejscu, ponieważ może służyć w dodatkowy kontekst. Niektóre specyfikatory również są prawidłowe dla natywnej programowania. Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie specyfikatorów przesłonięć w kompilacjach kodu natywnego (C + +/ CLI)](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

|Słowo kluczowe|Kontekstowa|Cel|Tematy pomocy|
|-------------|-----------------------|-------------|---------------|
|**abstract**|Tak|Wskazuje, że funkcji lub klasy abstrakcyjnej.|[abstract](abstract-cpp-component-extensions.md)|
|**new**|Nie|Wskazuje, że funkcja nie jest przesłonięciem wersją klasy bazowej.|[New (nowe gniazdo w vtable)](new-new-slot-in-vtable-cpp-component-extensions.md)|
|**override**|Tak|Wskazuje, że metoda musi być przesłonięciem wersję klasy podstawowej.|[override](override-cpp-component-extensions.md)|
|**sealed**|Tak|Zapobiega używana jako klay bazowe klasy.|[sealed](sealed-cpp-component-extensions.md)|

## <a name="keywords-for-generics"></a>Słowa kluczowe dla typów ogólnych

Następujące słowa kluczowe zostały dodane do obsługi typów ogólnych. Aby uzyskać więcej informacji, zobacz [ogólne](generics-cpp-component-extensions.md).

|Słowo kluczowe|Kontekstowa|Cel|
|-------------|-----------------------|-------------|
|**Ogólny**|Nie|Deklaruje typu ogólnego.|
|**gdzie**|Tak|Określa ograniczenia, które są stosowane do parametru typu ogólnego.|

## <a name="miscellaneous-keywords"></a>Różne słów kluczowych

Następujące słowa kluczowe zostały dodane do rozszerzeń języka C++.

|Słowo kluczowe|Kontekstowa|Cel|Tematy pomocy|
|-------------|-----------------------|-------------|---------------|
|**finally**|Tak|Określa domyślne zachowanie handlings wyjątku.|[Obsługa wyjątków](exception-handling-cpp-component-extensions.md)|
|**for each, in**|Nie|Wylicza elementów kolekcji.|[for each, in](../dotnet/for-each-in.md)|
|**gcnew**|Nie|Przydziela typy w stercie zebranych elementów bezużytecznych. Użyj zamiast **nowe** i **Usuń**.|[REF new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**nowe REF**|Tak|Przydziela typów środowiska wykonawczego Windows. Użyj zamiast **nowe** i **Usuń**.|[REF new, gcnew](ref-new-gcnew-cpp-component-extensions.md)|
|**initonly**|Tak|Wskazuje, że element członkowski może być inicjowane tylko w deklaracji lub w konstruktorze statycznym.|[initonly (C++/CLI)](../dotnet/initonly-cpp-cli.md)|
|**literał**|Tak|Tworzy zmienną literału.|[literał](literal-cpp-component-extensions.md)|
|**nullptr**|Nie|Wskazuje, że dojście lub wskaźnik nie wskazuje na obiekt.|[nullptr](nullptr-cpp-component-extensions.md)|

## <a name="template-constructs"></a>Konstrukcje szablonu

Następujące konstrukcji języka są implementowane jako szablon, zamiast jako słowa kluczowe. Jeśli określisz `/ZW` — opcja kompilatora, są zdefiniowane w `lang` przestrzeni nazw. Jeśli określisz `/clr` — opcja kompilatora, są zdefiniowane w `cli` przestrzeni nazw.

|Słowo kluczowe|Cel|Tematy pomocy|
|-------------|-------------|---------------|
|**Tablica**|Deklaruje tablicę.|[Tablice](arrays-cpp-component-extensions.md)|
|**interior_ptr**|(Tylko CLR) Punkty danych w typ odwołania.|[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)|
|**pin_ptr**|(Tylko CLR) Wskazuje typy odwołań CLR, aby tymczasowo pominąć system wyrzucania elementów bezużytecznych.|[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)|
|**safe_cast**|Określa i wykonuje metodę optymalne rzutowania, typu środowiska uruchomieniowego.|[safe_cast](safe-cast-cpp-component-extensions.md)|
|**TypeID**|(Tylko CLR) Pobiera <xref:System.Type?displayProperty=fullName> obiekt, który opisuje dany typ lub obiekt.|[TypeID](typeid-cpp-component-extensions.md)|

## <a name="declarators"></a>Deklaratory

Następujący typ deklaratory poinstruować środowiska uruchomieniowego do automatycznego zarządzania okresem istnienia i usuwanie istnienia przydzielonych obiektów.

|Operator|Cel|Tematy pomocy|
|--------------|-------------|---------------|
|`^`|Deklaruje dojścia do obiektu; oznacza to, wskaźnik do obiektu Windows Runtime lub CLR, są automatycznie usuwane, gdy go nie jest już możliwe.|[Operator uchwytu do obiektu (^)](handle-to-object-operator-hat-cpp-component-extensions.md)|
|`%`|Deklaruje odwołanie śledzenia; oznacza to, że odwołanie do obiektu Windows Runtime lub CLR, są automatycznie usuwane, gdy nie jest już można używać.|[Operator odwołania śledzenia](tracking-reference-operator-cpp-component-extensions.md)|

## <a name="additional-constructs-and-related-topics"></a>Dodatkową konstrukcje i Tematy pokrewne

W tej sekcji przedstawiono dodatkowe konstrukcje programowania i tematy, które odnoszą się do środowiska CLR.

|Temat|Opis|
|-----------|-----------------|
|[__identifier (C++/CLI)](identifier-cpp-cli.md)|(Windows Runtime i środowiska CLR) Umożliwia korzystanie z słów kluczowych jako identyfikatorów.|
|[Listy zmiennych argumentów (...) (C++/CLI)](variable-argument-lists-dot-dot-dot-cpp-cli.md)|(Windows Runtime i środowiska CLR) Włącza funkcję do wykonania zmienną liczbę argumentów.|
|[Odpowiedniki typów natywnych języka C++ w programie .NET Framework (C++/CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md)|Zawiera listę typów CLR, które są używane zamiast typów całkowitych C++.|
|[Obiekt AppDomain](../cpp/appdomain.md) **__declspec** modyfikator|**__declspec** modyfikator zezwalający na użycie istnienia zmiennych globalnych i statycznych dla domeny appdomain.|
|[Rzutowania w stylu języka C z/CLR (C + +/ CLI)](c-style-casts-with-clr-cpp-cli.md)|W tym artykule opisano, jak rzutowań w stylu C są interpretowane.|
|[Wywołanie __clrcall](../cpp/clrcall.md) konwencji wywoływania|Wskazuje CLS CLR konwencji wywoływania.|
|`__cplusplus_cli`|[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)|
|[Atrybuty niestandardowe](user-defined-attributes-cpp-component-extensions.md)|W tym artykule opisano sposób definiowania atrybutów CLR.|
|[Obsługa wyjątków](exception-handling-cpp-component-extensions.md)|Zawiera omówienie obsługi wyjątków.|
|[Jawne przesłonięcia](explicit-overrides-cpp-component-extensions.md)|Pokazuje, jak zastąpić dowolne elementy członkowskie funkcji elementów członkowskich.|
|[Przyjazne zestawy (C++)](../dotnet/friend-assemblies-cpp.md)|W tym artykule omówiono, jak zestaw klienta można dostęp do wszystkich typów w składniku zestawu.|
|[Konwersja boxing](boxing-cpp-component-extensions.md)|Pokazuje warunków w wartości, które są opakowany typów.|
|[Obsługa cech typu w kompilatorze](compiler-support-for-type-traits-cpp-component-extensions.md)|W tym artykule omówiono, jak wykrywać właściwości typów w czasie kompilacji.|
|[zarządzane, niezarządzane](../preprocessor/managed-unmanaged.md) dyrektywy pragma|Pokazuje, jak zarządzane i niezarządzane funkcje mogą współistnieć w tym samym module.|
|[proces](../cpp/process.md) **__declspec** modyfikator|**__declspec** modyfikator zezwalający na to, że zmiennych globalnych i statycznych istnieją na proces.|
|[Odbicie (C++/CLI)](../dotnet/reflection-cpp-cli.md)|Pokazuje informacje typu run-time w wersji środowiska CLR.|
|[Ciąg](string-cpp-component-extensions.md)|W tym artykule omówiono kompilatora konwersja z literałów ciągów do <xref:System.String>.|
|[Przekazywanie dalej typu (C++/CLI)](type-forwarding-cpp-cli.md)|Włącza przepływ typu w zestawie wysyłanie do innego zestawu. Dzięki temu kod klienta nie musi być ponownie kompilowane.|
|[Atrybuty zdefiniowane przez użytkownika](user-defined-attributes-cpp-component-extensions.md)|Pokazuje atrybuty zdefiniowane przez użytkownika.|
|[#using — dyrektywa](../preprocessor/hash-using-directive-cpp.md)|Importuje zestawy zewnętrzne.|
|[Dokumentacja XML](../build/reference/xml-documentation-visual-cpp.md)|Wyjaśnia dokumentacji oparty na składni XML kodu za pomocą  [ /doc (Przetwarzaj komentarze dokumentacji) (C/C++)](../build/reference/doc-process-documentation-comments-c-cpp.md)|

## <a name="see-also"></a>Zobacz też

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)