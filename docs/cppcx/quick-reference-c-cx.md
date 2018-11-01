---
title: Krótki przewodnik (C + +/ CX)
ms.date: 12/30/2016
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
ms.openlocfilehash: eb407a0264a68f9b89e4a180c8b151076fdd109a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445334"
---
# <a name="quick-reference-ccx"></a>Krótki przewodnik (C + +/ CX)

Środowisko wykonawcze Windows obsługuje aplikacje platformy uniwersalnej Windows (UWP), wykonywanie tylko w środowisku godne zaufania systemu operacyjnego przy użyciu funkcji autoryzowanych, typów danych i urządzeń, oraz są dystrybuowane za pośrednictwem Microsoft Store. C + +/ CX uproszczają pisanie aplikacji dla środowiska wykonawczego Windows. Ten artykuł stanowi krótki; dla bardziej wyczerpujące informacje, zobacz [System typów](../cppcx/type-system-c-cx.md).

W przypadku tworzenia w wierszu polecenia, użyj **/ZW** — opcja kompilatora do tworzenia aplikacji platformy uniwersalnej systemu Windows lub składnik środowiska wykonawczego Windows. Aby dostęp do środowiska wykonawczego Windows deklaracje, które są zdefiniowane w plikach metadanych (.winmd) środowiska wykonawczego Windows, należy określić `#using` dyrektywy lub **/FU** — opcja kompilatora. Kiedy tworzysz projekt aplikacji platformy uniwersalnej systemu Windows, Visual Studio domyślnie ustawia tych opcji i dodaje odwołania do wszystkich bibliotek środowiska wykonawczego Windows.

## <a name="quick-reference"></a>Krótki przewodnik

|Pojęcie|Standard C++|C++/CX|Uwagi|
|-------------|--------------------|------------------------------------------------------------------|-------------|
|Typy podstawowe|Typów podstawowych języka C++.|C + +/ CX podstawowe typy, które implementują typów podstawowych, które są zdefiniowane w środowisku uruchomieniowym Windows.|`default` Przestrzeń nazw zawiera C + +/ CX typów wbudowanych, podstawowe. Kompilator niejawnie mapuje C + +/ CX podstawowych typów do standardowych typów C++.<br /><br /> `Platform` Rodziny przestrzenie nazw zawiera typy, które implementują podstawowych typów środowiska wykonawczego Windows.|
||`bool`|`bool`|Wartość logiczna 8-bitowych.|
||`__wchar_t`|`char16`|16-bitową liczbą wartość reprezentuje punkt kodu Unicode (UTF-16).|
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|Całkowita 16-bitowych.<br /><br /> 16-bitowa liczba całkowita bez znaku.|
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|Całkowita 32-bitowych.<br /><br /> 32-bitowa liczba całkowita bez znaku.|
||`long long` - lub - `__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|Całkowita 64-bitowych.<br /><br /> 64-bitowej nieoznaczonej liczby całkowitej.|
||`float, double`|`float32, float64`|32-bitową lub 64-bitowych IEEE 754 liczba zmiennoprzecinkowa.|
||`enum {}`|`enum class {}`<br /><br /> —lub—<br /><br /> `enum struct {}`|Wyliczenie 32-bitowych.|
||(Nie dotyczy)|`Platform::Guid`|Wartość nienumeryczna 128-bitowego (GUID) w `Platform` przestrzeni nazw.|
||`std::time_get`|`Windows::Foundation::DateTime`|Struktura daty i godziny.|
||(Nie dotyczy)|`Windows::Foundation::TimeSpan`|Struktura przedziału czasu.|
||(Nie dotyczy)|`Platform::Object^`|Obiekt podstawowy zliczonych odwołań w widoku C++ system typów środowiska wykonawczego Windows.|
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` to zliczonych odwołań, niezmienne, sekwencja znaków Unicode, które reprezentują tekstu.|
|Wskaźnik|Wskaźnik do obiektu (`*`):<br /><br /> `std::shared_ptr`|Dojście do obiektu (`^`, wymawiane "hat"):<br /><br /> *T ^ identyfikator*|Wszystkie klasy środowiska wykonawczego Windows są zadeklarowane za pomocą modyfikatora uchwytu do obiektu. Elementy członkowskie obiektu są dostępne za pomocą strzałki (`->`) operator dostępu do składowej klasy.<br /><br /> Modyfikator hat oznacza "wskaźnik do obiektu Windows Runtime, który jest automatycznie odwołanie zliczane." Bardziej precyzyjne uchwytu do obiektu deklaruje, że kompilator należy wstawić kod do automatycznego zarządzania licznik odwołań obiektu i usuń go, jeśli liczba odwołań osiąga zero.|
|Tematy pomocy|Odwołanie do obiektu (`&`):<br /><br /> *T* `&` *identyfikator*|Odwołanie śledzenia (`%`):<br /><br /> *T* `%` *identyfikator*|Modyfikator odwoływać się tylko środowiska wykonawczego Windows, które typy mogą być deklarowane przy użyciu śledzenia. Elementy członkowskie obiektu są dostępne przy użyciu kropki (`.`) operator dostępu do składowej klasy.<br /><br /> Odwołanie śledzenia oznacza "odwołanie do obiektu Windows Runtime, która automatycznie jest liczona liczba odwołań." Bardziej precyzyjne odwołaniem śledzącym deklaruje, że kompilator należy wstawić kod do automatycznego zarządzania licznik odwołań obiektu i usuń go, jeśli liczba odwołań osiąga zero.|
|Deklaracja typu dynamicznego|`new`|`ref new`|Przydziela obiektu Windows Runtime, a następnie zwraca uchwyt do tego obiektu.|
|Zarządzanie okresem istnienia obiektów|`delete` *Identyfikator*<br /><br /> `delete[]`  *Identyfikator*|(Wywołuje destruktor).|Okres istnienia jest określany przez zliczanie odwołań. Wywołanie w celu usunięcia wywołuje destruktor, ale sam nie spowoduje zwolnienia pamięci.|
|Deklaracja tablicy|*Identyfikator T* `[]`<br /><br /> `std::array` *Identyfikator*|`Array<` *T* `^>^` *identyfikator* `(` *rozmiar* `)`<br /><br /> —lub—<br /><br /> `WriteOnlyArray<` *T* `^>` *identyfikator* `(` *rozmiar* `)`|Deklaruje Jednowymiarowa tablica, można modyfikować, czy tylko do zapisu, typu T ^. Macierz, sama jest również zliczonych odwołań obiektu, który musi być zadeklarowany za pomocą modyfikatora uchwytu do obiektu.<br /><br /> (Deklaracje tablicy użycie klasy nagłówka szablonu, która znajduje się w `Platform` przestrzeni nazw.)|
|Deklaracja klasy|`class`  *Identyfikator* `{}`<br /><br /> `struct` *Identyfikator* `{}`|`ref class` *Identyfikator* `{}`<br /><br /> `ref struct` *Identyfikator* `{}`|Deklaruje klasy środowiska wykonawczego, która ma domyślne prywatną dostępność.<br /><br /> Deklaruje klasy środowiska wykonawczego, która ma domyślne powszechnej dostępności.|
|Deklaracji struktury|`struct` *Identyfikator* `{}`<br /><br /> (czyli zwykłe stare dane struktury (POD))|`value class` *Identyfikator* `{}`<br /><br /> `value struct` *Identyfikator* `{}`|Deklaruje struktury ZASOBNIKÓW, która ma domyślne prywatną dostępność.<br /><br /> Klasa wartości mogą być reprezentowane w metadanych Windows, ale klasa C++ standardowa nie może być.<br /><br /> Deklaruje struktury ZASOBNIKÓW, która ma domyślne powszechnej dostępności.<br /><br /> Struktura wartości mogą być reprezentowane w metadanych Windows, ale struktura standard C++ nie może być.|
|Deklaracja interfejsu|abstrakcyjna klasa, która zawiera tylko czyste funkcje wirtualne.|`interface class` *Identyfikator* `{}`<br /><br /> `interface struct` *Identyfikator* `{}`|Deklaruje interfejs, który ma domyślne prywatną dostępność.<br /><br /> Deklaruje interfejs, który ma domyślne powszechnej dostępności.|
|Delegate|`std::function`|`public delegate` *zwracany typ* *identyfikatora w przypadku typu delegata* `(` *[parametry]* `);`|Deklaruje obiekt, który może być wywoływany podobnie jak wywołania funkcji.|
|Zdarzenie|(Nie dotyczy)|`event` *Delegat typu identyfikatorów* *identyfikator zdarzenia* `;`<br /><br /> *Delegat typu identyfikatorów* *identyfikator delegata* = `ref new`*identyfikatora w przypadku typu delegata*`( this`*[, parametry]*`);`<br /><br /> *Identyfikator zdarzenia* `+=` *identyfikator delegata* `;`<br /><br /> —lub—<br /><br /> `EventRegistrationToken` *Identyfikator tokenu* = *obj*`.`*identyfikator zdarzenia*`+=`*identyfikator delegata*`;`<br /><br /> —lub—<br /><br /> `auto` *Identyfikator tokenu* = *obj*. *identyfikator zdarzenia*`::add(`*identyfikator delegata*`);`<br /><br /> *obj* `.` *identyfikator zdarzenia* `-=` *tokenu identyfikatora* `;`<br /><br /> —lub—<br /><br /> *obj* `.` *identyfikator zdarzenia* `::remove(` *tokenu identyfikatora* `);`|Deklaruje zdarzenie obiektu, który przechowuje kolekcję programów obsługi zdarzeń (delegatów), które są wywoływane, gdy wystąpi zdarzenie.<br /><br /> Tworzy program obsługi zdarzeń.<br /><br /> Dodaje procedurę obsługi zdarzeń.<br /><br /> Dodawanie obsługi zdarzeń zwraca token zdarzeń (*tokenu identyfikatora*). Jeśli zamierzasz usunąć program obsługi zdarzeń, musisz najpierw zapisać token zdarzeń do późniejszego użycia.<br /><br /> Usuwa procedurę obsługi zdarzeń.<br /><br /> Aby usunąć program obsługi zdarzeń, należy określić token zdarzeń, który został zapisany podczas dodawania programu obsługi zdarzeń.|
|Właściwość|(Nie dotyczy)|`property` *T* *identyfikator*;<br /><br /> `property` *T* *identyfikator* `[` *indeksu* `];`<br /><br /> `property` *T* `default[` *index* `];`|Deklaruje, że funkcji składowej klasy lub obiektu odbywa się przy użyciu tej samej składni, które umożliwiają dostęp do składowej danych lub indeksowane elementu tablicy.<br /><br /> Deklaruje właściwości dla funkcji składowej klasy lub obiektu.<br /><br /> Deklaruje właściwości indeksowanej na funkcję elementu członkowskiego obiektu.<br /><br /> Deklaruje indeksowana właściwość w funkcji składowej klasy.|
|Typy z parametrami|szablony|`generic <typename` *T* `> interface class` *identyfikator* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[return-type]* *identyfikator delegata* `() {}`|Deklaruje klasę sparametryzowane interfejsu.<br /><br /> Deklaruje sparametryzowane delegata.|
|Typy o wartości zerowalnej|`boost::optional<T>`|[Platform::IBox \<T >](../cppcx/platform-ibox-interface.md)|Włącza zmiennych typów skalarnych i strukturach wartości, które mają wartość `nullptr`.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)