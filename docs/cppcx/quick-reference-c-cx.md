---
title: Krótki przewodnik (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ba457195-26e5-43aa-b99d-24a871e550f4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 830c27d89e427e2ea36a68d891aac0ebadcf3f21
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="quick-reference-ccx"></a>Krótki przewodnik (C + +/ CX)
Środowisko wykonawcze systemu Windows obsługuje aplikacje systemu Windows platformy Uniwersalnej, wykonać tylko w środowisku godne zaufania systemu operacyjnego, korzystając z funkcji autoryzowanych, typy danych i urządzeń, które są dystrybuowane za pośrednictwem Microsoft Store. C + +/ CX uprościć podczas opracowywania aplikacji dla środowiska uruchomieniowego systemu Windows. W tym artykule jest szybkie odwołanie; bardziej szczegółowy dokumentację można znaleźć [System typów](../cppcx/type-system-c-cx.md) i [Component Extensions dla platform środowiska uruchomieniowego](http://go.microsoft.com/fwlink/p/?linkid=228720).  
  
 Podczas kompilowania w wierszu polecenia, użyj **/ZW** — opcja kompilatora do tworzenia aplikacji platformy uniwersalnej systemu Windows lub składnik środowiska wykonawczego systemu Windows. Aby dostęp deklaracje środowiska wykonawczego systemu Windows, które są zdefiniowane w pliku metadanych (.winmd) środowiska wykonawczego systemu Windows, należy określić `#using` dyrektywy lub **/FU** — opcja kompilatora. Podczas tworzenia projektu dla aplikacji platformy uniwersalnej systemu Windows, programu Visual Studio domyślnie ustawia te opcje i dodaje odwołania do wszystkich bibliotek środowiska uruchomieniowego systemu Windows.  
  
## <a name="quick-reference"></a>Krótki przewodnik  
  
|Pojęcie|Standard C++|C++/CX|Uwagi|  
|-------------|--------------------|------------------------------------------------------------------|-------------|  
|Typy podstawowe|Typy podstawowe języka C++.|C + +/ CX typów podstawowych, które implementują typów podstawowych, które są zdefiniowane w środowisku wykonawczym systemu Windows.|`default` Przestrzeń nazw zawiera C + +/ CX wbudowanych, podstawowych typów. Kompilator niejawnie mapuje C + +/ CX typów podstawowych do standardowych typów języka C++.<br /><br /> `Platform` z nazw rodziny zawiera typy, które implementuje podstawowych typów środowiska wykonawczego systemu Windows.|  
||`bool`|`bool`|8-bitową wartość logiczna.|  
||`__wchar_t`|`char16`|16-bitową liczbą wartość odpowiadającą punkt kodu Unicode (UTF-16).|  
||`short`<br /><br /> `unsigned short`|`int16`<br /><br /> `uint16`|16-bitową liczbę całkowitą ze znakiem.<br /><br /> 16-bitową liczbę całkowitą bez znaku.|  
||`int`<br /><br /> `unsigned int`|`int`<br /><br /> `uint32`|Całkowita 32-bitowych.<br /><br /> 32-bitowa liczba całkowita bez znaku.|  
||`long long` - lub - `__int64`<br /><br /> `unsigned long long`|`int64`<br /><br /> `uint64`|Całkowita 64-bitowych.<br /><br /> 64-bitowa liczba całkowita bez znaku.|  
||`float, double`|`float32, float64`|32-bitowy lub 64-bitowych IEEE-754 liczba zmiennoprzecinkowa.|  
||`enum {}`|`enum class {}`<br /><br /> —lub—<br /><br /> `enum struct {}`|Wyliczenie 32-bitowych.|  
||(Nie dotyczy)|`Platform::Guid`|Wartość liczbą 128-bitowego (GUID) w `Platform` przestrzeni nazw.|  
||`std::time_get`|`Windows::Foundation::DateTime`|Struktura daty i godziny.|  
||(Nie dotyczy)|`Windows::Foundation::TimeSpan`|Struktura timespan.|  
||(Nie dotyczy)|`Platform::Object^`|Obiekt podstawowy zliczane odwołania w widoku C++ system typów środowiska wykonawczego systemu Windows.|  
||`std::wstring`<br /><br /> `L"..."`|`Platform::String^`|`Platform::String^` to zliczane odwołania, modyfikować, sekwencja znaków Unicode, które reprezentują tekstu.|  
|Wskaźnik|Wskaźnik do obiektu (`*`):<br /><br /> `std::shared_ptr`|Dojście do obiektu (`^`, w przypadku "hat"):<br /><br /> *T ^ identyfikator*|Wszystkie klasy środowiska wykonawczego systemu Windows są zadeklarowane przy użyciu modyfikatora uchwyt do obiektu. Elementy członkowskie obiektu są dostępne za pomocą strzałki (`->`) operatora dostępu do elementu członkowskiego klasy.<br /><br /> Modyfikator hat oznacza "zliczane wskaźnik do obiektu środowiska wykonawczego systemu Windows, który jest automatycznie odwołania." Mówiąc ściślej uchwyt do obiektu deklaruje, że kompilator powinien Wstaw kod, aby automatycznie zarządzać liczba odwołań obiektu i usuń go, jeśli liczba odwołań do zera.|  
|Tematy pomocy|Odwołanie do obiektu (`&`):<br /><br /> *T* `&` *identyfikator*|Odwołanie śledzące (`%`):<br /><br /> *T* `%` *identyfikator*|Modyfikator odwoływać się tylko środowiska wykonawczego systemu Windows, które typy mogą być deklarowane przy użyciu śledzenia. Elementy członkowskie obiektu są dostępne za pomocą kropki (`.`) operatora dostępu do elementu członkowskiego klasy.<br /><br /> Odwołanie śledzące oznacza "odwołanie do obiektu środowiska wykonawczego systemu Windows, który jest automatycznie zliczane odwołania." Mówiąc ściślej odwołaniem śledzącym deklaruje, że kompilator powinien Wstaw kod, aby automatycznie zarządzać liczba odwołań obiektu i usuń go, jeśli liczba odwołań do zera.|  
|Deklaracja typu dynamicznego|`new`|`ref new`|Przydziela obiektu środowiska wykonawczego systemu Windows, a następnie zwraca uchwyt do tego obiektu.|  
|Zarządzanie okresem istnienia obiektu|`delete` *Identyfikator*<br /><br /> `delete[]`  *Identyfikator*|(Wywołuje destruktor).|Okres istnienia jest określana przez liczenie odwołań. Wywołanie usunięcia wywołuje destruktor, ale sam nie spowoduje zwolnienia pamięci.|  
|Deklaracja tablicy|*Identyfikator T* `[]`<br /><br /> `std::array` *Identyfikator*|`Array<` *T* `^>^` *identyfikator* `(` *rozmiaru* `)`<br /><br /> —lub—<br /><br /> `WriteOnlyArray<` *T* `^>` *identyfikator* `(` *rozmiaru* `)`|Deklaruje można modyfikować lub w trybie tylko do zapisu tablicą jednowymiarową typu T ^. Tablica się również jest obiekt zliczane odwołania musi być zadeklarowany za pomocą modyfikatora uchwyt do obiektu.<br /><br /> (Deklaracje tablicy należy użyć klasy nagłówka szablonu, który znajduje się w `Platform` przestrzeni nazw.)|  
|Deklaracja klasy|`class`  *Identyfikator* `{}`<br /><br /> `struct`  *Identyfikator* `{}`|`ref class`  *Identyfikator* `{}`<br /><br /> `ref struct`  *Identyfikator* `{}`|Deklaruje klasy środowiska uruchomieniowego, która ma domyślne prywatną dostępność.<br /><br /> Deklaruje klasy środowiska uruchomieniowego, która ma domyślne powszechnej dostępności.|  
|Deklaracje struktury|`struct`  *Identyfikator* `{}`<br /><br /> (to znaczy zwykły starych danych struktury (POD))|`value class`  *Identyfikator* `{}`<br /><br /> `value struct`  *Identyfikator* `{}`|Deklaruje struktury POD zawierający domyślne prywatną dostępność.<br /><br /> Klasa wartości ma być reprezentowane w metadanych systemu Windows, ale nie może być klasą standard C++.<br /><br /> Deklaruje struktury POD zawierający domyślne powszechnej dostępności.<br /><br /> Struktura wartość może być reprezentowany w metadanych systemu Windows, ale standard C++ struktury nie mogą być.|  
|Deklaracja interfejsu|Klasa abstrakcyjna, która zawiera tylko czystych funkcji wirtualnych.|`interface class`  *Identyfikator* `{}`<br /><br /> `interface struct`  *Identyfikator* `{}`|Deklaruje interfejs, który ma domyślne prywatną dostępność.<br /><br /> Deklaruje interfejs, który ma domyślne powszechnej dostępności.|  
|Delegate|`std::function`|`public delegate` *zwracanego typu* *delegowanego typu identyfikatorów* `(` *[parametry]* `);`|Deklaruje obiekt, który może być wywoływany, takie jak wywołania funkcji.|  
|Zdarzenie|(Nie dotyczy)|`event` *Delegat typu identyfikatorów* *identyfikator zdarzenia* `;`<br /><br /> *Delegat typu identyfikatorów* *identyfikator obiektu delegowanego* = `ref new`*delegowanego typu identyfikatorów*`( this`*[, parametry]*`);`<br /><br /> *Identyfikator zdarzenia* `+=` *identyfikator delegata* `;`<br /><br /> —lub—<br /><br /> `EventRegistrationToken` *Identyfikator tokenu* = *obj*`.`*identyfikator zdarzenia*`+=`*identyfikator delegata*`;`<br /><br /> —lub—<br /><br /> `auto` *Identyfikator tokenu* = *obj*. *identyfikator zdarzenia*`::add(`*identyfikator delegata*`);`<br /><br /> *obj* `.` *identyfikator zdarzenia* `-=` *identyfikator tokenu* `;`<br /><br /> —lub—<br /><br /> *obj* `.` *identyfikator zdarzenia* `::remove(` *identyfikator tokenu* `);`|Deklaruje obiekt zdarzenia, który przechowuje kolekcja programów obsługi zdarzeń (obiekty delegowane), które są wywoływane, gdy wystąpi zdarzenie.<br /><br /> Tworzy program obsługi zdarzeń.<br /><br /> Dodaje program obsługi zdarzeń.<br /><br /> Dodawanie obsługi zdarzeń zwraca token zdarzenia (*identyfikator tokenu*). Jeśli zamierzasz usunąć obsługi zdarzeń, musisz najpierw zapisać token zdarzeń do późniejszego użycia.<br /><br /> Usuwa program obsługi zdarzeń.<br /><br /> Aby usunąć program obsługi zdarzeń, należy określić token zdarzenia zapisywane podczas dodawania obsługi zdarzeń.|  
|Właściwość|(Nie dotyczy)|`property` *T* *identyfikator*;<br /><br /> `property` *T* *identyfikator* `[` *indeksu* `];`<br /><br /> `property` *T* `default[` *index* `];`|Deklaruje, że funkcji członkowskiej klasy lub obiekt jest dostępny przy użyciu takiej samej składni, umożliwiające dostęp do elementu członkowskiego danych lub indeksowanego elementu tablicy.<br /><br /> Deklaruje właściwości dla funkcji członkowskiej klasy lub obiektu.<br /><br /> Deklaruje właściwości indeksowanych w funkcji Członkowskich obiektu.<br /><br /> Deklaruje właściwości indeksowanych w funkcji członkowskiej klasy.|  
|Typy z parametrami|szablony|`generic <typename` *T* `> interface class` *identyfikator* `{}`<br /><br /> `generic <typename` *T* `> delegate` *[zwracanego typu]* *identyfikator delegata* `() {}`|Deklaruje klasy sparametryzowane interfejsu.<br /><br /> Deklaruje delegata sparametryzowana.|  
|typy dopuszczające wartości zerowe wartości|`boost::optional<T>`|[Platform::IBox \<T >](../cppcx/platform-ibox-interface.md)|Włącza zmienne typy skalarne i struktury wartości, które mają wartość `nullptr`.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka Visual C++](../cppcx/visual-c-language-reference-c-cx.md)