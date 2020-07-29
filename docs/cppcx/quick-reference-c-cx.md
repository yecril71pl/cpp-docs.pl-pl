---
title: Krótki przewodnik (C++/CX)
ms.date: 12/30/2016
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
ms.openlocfilehash: 6effcaec6a619bdd674dcae3bf4092fe82404d08
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214974"
---
# <a name="quick-reference-ccx"></a>Krótki przewodnik (C++/CX)

Środowisko wykonawcze systemu Windows obsługuje aplikacje platforma uniwersalna systemu Windows (platformy UWP), które działają tylko w godnym zaufania środowisku systemu operacyjnego, używają autoryzowanych funkcji, typów danych i urządzeń i są dystrybuowane w Microsoft Store. C++/CX upraszcza pisanie aplikacji dla środowisko wykonawcze systemu Windows. Ten artykuł jest szybkim odwołaniem. Aby uzyskać pełną dokumentację, zobacz [typu System](../cppcx/type-system-c-cx.md).

Podczas kompilowania w wierszu polecenia Użyj opcji kompilatora **/zw** , aby skompilować aplikację platformy UWP lub składnik środowisko wykonawcze systemu Windows. Aby uzyskać dostęp do środowisko wykonawcze systemu Windows deklaracji, które są zdefiniowane w plikach metadanych środowisko wykonawcze systemu Windows (WinMD), określ `#using` dyrektywę lub opcję kompilatora **/Fu** . Podczas tworzenia projektu dla aplikacji platformy UWP program Visual Studio domyślnie ustawia te opcje i dodaje odwołania do wszystkich bibliotek środowisko wykonawcze systemu Windows.

## <a name="quick-reference"></a>Krótki przewodnik

|Pojęcie|Standard C++|C++/CX|Uwagi|
|-------------|--------------------|------------------------------------------------------------------|-------------|
|Typy podstawowe|Podstawowe typy języka C++.|C++/CX podstawowe typy, które implementują podstawowe typy, które są zdefiniowane w środowisko wykonawcze systemu Windows.|`default`Przestrzeń nazw zawiera wbudowane typy podstawowe języka C++/CX. Kompilator niejawnie mapuje podstawowe typy C++/CX na standardowe typy C++.<br /><br /> `Platform`Rodzina przestrzeni nazw zawiera typy implementujące podstawowe typy środowisko wykonawcze systemu Windows.|
||**`bool`**|**`bool`**|8-bitowa wartość logiczna.|
||**`wchar_t`**, **`char16_t`**|`char16`|16-bitowa wartość nieliczbowa, która reprezentuje punkt kodowy w formacie Unicode (UTF-16).|
||**`short`**<br /><br /> **`unsigned short`**|`int16`<br /><br /> `uint16`|16-bitowa liczba całkowita ze znakiem.<br /><br /> 16-bitowa liczba całkowita bez znaku.|
||**`int`**<br /><br /> **`unsigned int`**|**`int`**<br /><br /> `uint32`|32-bitowa liczba całkowita ze znakiem.<br /><br /> 32-bitowa liczba całkowita bez znaku.|
||**`long long`** oraz**`__int64`**<br /><br /> **`unsigned long long`**|`int64`<br /><br /> `uint64`|64-bitowa liczba całkowita ze znakiem.<br /><br /> 64-bitowa liczba całkowita bez znaku.|
||**`float`**, **`double`**|`float32, float64`|32-bitowa lub 64-bitowa liczba zmiennoprzecinkowa IEEE 754.|
||**`enum`**|**`enum class`**<br /><br /> -lub-<br /><br /> **`enum struct`**|Wyliczenie 32-bitowe.|
||(Nie dotyczy)|`Platform::Guid`|128-bitowa wartość nieliczbowa (GUID) w `Platform` przestrzeni nazw.|
||`std::time_get`|`Windows::Foundation::DateTime`|Struktura daty i godziny.|
||(Nie dotyczy)|`Windows::Foundation::TimeSpan`|Struktura TimeSpan.|
||(Nie dotyczy)|`Platform::Object^`|Obiekt podstawowy liczony z odwołaniami w widoku C++ systemu typu środowisko wykonawcze systemu Windows.|
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^`jest obliczanym przez odwołanie, niezmiennej sekwencji znaków Unicode, która reprezentuje tekst.|
|Wskaźnik|Wskaźnik do obiektu ( `*` ):<br /><br /> `std::shared_ptr`|Dojście do obiektu ( `^` , wymawiane "Hat"):<br /><br /> *Identyfikator T ^*|Wszystkie klasy środowisko wykonawcze systemu Windows są zadeklarowane za pomocą modyfikatora dojścia do obiektu. Dostęp do elementów członkowskich obiektu uzyskuje się za pomocą strzałek ( `->` ) klasy — operator dostępu.<br /><br /> Modyfikator Hat oznacza "wskaźnikiem do obiektu środowisko wykonawcze systemu Windows, który jest automatycznie traktowany jako". Dokładniej, dojście do obiektu deklaruje, że kompilator powinien wstawić kod, aby automatycznie zarządzać liczbą odwołań obiektu, i usunąć obiekt, jeśli liczba odwołań spadnie do zera.|
|Dokumentacja|Odwołanie do obiektu ( `&` ):<br /><br /> *T* `&` *Identyfikator* T|Odwołanie śledzenia ( `%` ):<br /><br /> *T* `%` *Identyfikator* T|Tylko typy środowisko wykonawcze systemu Windows mogą być deklarowane za pomocą modyfikatora odwołania śledzenia. Dostęp do elementów członkowskich obiektu uzyskuje się za pomocą operatora z dostępem typu kropka ( `.` ).<br /><br /> Odwołanie śledzące oznacza odwołanie do obiektu środowisko wykonawcze systemu Windows, do którego odwołuje się automatycznie. Dokładniej, odwołanie śledzenia deklaruje, że kompilator powinien wstawić kod, aby automatycznie zarządzać liczbą odwołań obiektu, i usunąć obiekt, jeśli liczba odwołań spadnie do zera.|
|Deklaracja typu dynamicznego|`new`|`ref new`|Przydziela obiekt środowisko wykonawcze systemu Windows, a następnie zwraca dojście do tego obiektu.|
|Zarządzanie okresem istnienia obiektu|`delete`*Identyfikator*<br /><br /> `delete[]`  *identyfikatora*|(Wywołuje destruktor).|Okres istnienia jest określany przez zliczanie odwołań. Wywołanie metody DELETE wywołuje destruktor, ale nie zwalnia pamięci.|
|Deklaracja tablicy|*Identyfikator T*`[]`<br /><br /> `std::array`*Identyfikator*|`Array<`*T* `^>^` *identifier* `(` *Rozmiar* identyfikatora T`)`<br /><br /> -lub-<br /><br /> `WriteOnlyArray<`*T* `^>` *identifier* `(` *Rozmiar* identyfikatora T  `)`|Deklaruje jednowymiarową tablicę modyfikowalną lub tylko do zapisu typu T ^. Sama tablica jest również obiektem zliczanym odwołań, który musi być zadeklarowany za pomocą modyfikatora dojścia do obiektu.<br /><br /> (Deklaracje tablic używają klasy nagłówka szablonu, która znajduje się w `Platform` przestrzeni nazw).|
|Deklaracja klasy|**`class`***Identyfikator*`{}`<br /><br /> **`struct`***Identyfikator*`{}`|**`ref class`***Identyfikator*`{}`<br /><br /> **`ref struct`***Identyfikator*`{}`|Deklaruje klasę środowiska uruchomieniowego z domyślną prywatną dostępnością.<br /><br /> Deklaruje klasę środowiska uruchomieniowego, która ma domyślną dostępność publiczną.|
|Deklaracja struktury|**`struct`***Identyfikator*`{}`<br /><br /> (to jest zwykła Stara struktura danych (POD))|**`value class`***Identyfikator*`{}`<br /><br /> **`value struct`***Identyfikator*`{}`|Deklaruje strukturę POD, która ma domyślny prywatny dostęp.<br /><br /> Klasa wartości może być reprezentowana w metadanych systemu Windows, ale nie można wykonać standardowej klasy języka C++.<br /><br /> Deklaruje strukturę POD, która ma domyślną dostępność publiczną.<br /><br /> Struktura wartości może być reprezentowana w metadanych systemu Windows, ale standardowa Struktura C++ nie może być.|
|Deklaracja interfejsu|Klasa abstrakcyjna, która zawiera tylko czyste funkcje wirtualne.|**`interface class`***Identyfikator*`{}`<br /><br /> **`interface struct`***Identyfikator*`{}`|Deklaruje interfejs, który ma domyślną dostępność prywatną.<br /><br /> Deklaruje interfejs, który ma domyślną dostępność publiczną.|
|Delegat|`std::function`|`public delegate`*typ delegata zwrotnego* *-Typ-identyfikator* `(` *[parametry]*`);`|Deklaruje obiekt, który może być wywoływany jak wywołanie funkcji.|
|Wydarzenie|(Nie dotyczy)|**`event`***Identyfikator zdarzenia* *delegata-Type* -Identifier`;`<br /><br /> *Delegat-Type-* identyfikator *delegata-identyfikator*  =  `ref new` *Delegat-Type-identyfikator* `( this` *[, parametry]*`);`<br /><br /> *Identyfikator zdarzenia* `+=` *Identyfikator delegata*`;`<br /><br /> -lub-<br /><br /> `EventRegistrationToken`*Identyfikator tokenu*  =  *obj* `.` *Identyfikator zdarzenia* `+=` *Identyfikator delegata*`;`<br /><br /> -lub-<br /><br /> **`auto`***Identyfikator tokenu*  =  *obj*. *Identyfikator zdarzenia* `::add(` *Identyfikator delegata*`);`<br /><br /> *obj* `.` *Identyfikator zdarzenia* `-=` *Identyfikator tokenu*`;`<br /><br /> -lub-<br /><br /> *obj* `.` *Identyfikator zdarzenia* `::remove(` *Identyfikator tokenu*`);`|Deklaruje obiekt zdarzenia, który przechowuje kolekcję programów obsługi zdarzeń (delegatów), które są wywoływane w przypadku wystąpienia zdarzenia.<br /><br /> Tworzy procedurę obsługi zdarzeń.<br /><br /> Dodaje procedurę obsługi zdarzeń.<br /><br /> Dodanie procedury obsługi zdarzeń zwraca token zdarzenia (*token-Identifier*). Jeśli zamierzasz jawnie usunąć procedurę obsługi zdarzeń, musisz zapisać token zdarzenia do późniejszego użycia.<br /><br /> Usuwa procedurę obsługi zdarzeń.<br /><br /> Aby usunąć program obsługi zdarzeń, należy określić token zdarzenia, który został zapisany podczas dodawania programu obsługi zdarzeń.|
|Właściwość|(Nie dotyczy)|**`property`***T* *Identyfikator*T;<br /><br /> **`property`***T* *identifier* `[` *Indeks* identyfikatora T`];`<br /><br /> **`property`***T* `default[` *Indeks* T`];`|Deklaruje, że dostęp do klasy lub funkcji składowej obiektu jest uzyskiwany za pomocą tej samej składni, która jest używana w celu uzyskania dostępu do elementu członkowskiego danych lub tablicy indeksowanej.<br /><br /> Deklaruje właściwość klasy lub funkcji składowej obiektu.<br /><br /> Deklaruje indeksowaną właściwość w funkcji składowej obiektu.<br /><br /> Deklaruje indeksowaną właściwość w funkcji składowej klasy.|
|Typy sparametryzowane|szablonów|`generic <typename`*T* `> interface class` *Identyfikator* T`{}`<br /><br /> `generic <typename`*T* `> delegate` *[return-Type]* *Delegat-Identifier*`() {}`|Deklaruje klasę interfejsu sparametryzowanego.<br /><br /> Deklaruje sparametryzowany obiekt delegowany.|
|Typy wartości dopuszczające wartość null|`boost::optional<T>`|[Platforma:: IBox\<T>](../cppcx/platform-ibox-interface.md)|Włącza zmienne typów skalarnych i struktur wartości, aby miało wartość **`nullptr`** .|

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++/CX](../cppcx/visual-c-language-reference-c-cx.md)
