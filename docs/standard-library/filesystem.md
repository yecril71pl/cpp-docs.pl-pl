---
title: '&lt;:::no-loc(filesystem):::&gt;'
description: 'Opisuje klasy, funkcje i typy w :::no-loc(filesystem)::: nagłówku standardowej biblioteki języka C++.'
ms.date: 01/22/2020
f1_keywords:
- <:::no-loc(filesystem):::>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- ':::no-loc(filesystem):::'
- ':::no-loc(experimental):::'
- ':::no-loc(char):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(char16_t):::'
- ':::no-loc(char32_t):::'
ms.openlocfilehash: 1b3f541619bde85131915a4d1586a44675c2906a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219147"
---
# &lt;:::no-loc(filesystem):::&gt;

Dołącz> nagłówka &lt; :::no-loc(filesystem)::: , aby uzyskać dostęp do klas i funkcji, które manipulują i pobierają informacje o ścieżkach, plikach i katalogach.

## <a name="syntax"></a>Składnia

```cpp
#include <:::no-loc(filesystem):::> // C++17 standard header file name
#include <:::no-loc(experimental):::/:::no-loc(filesystem):::> // Header file for pre-standard implementation
using namespace std:::::no-loc(experimental)::::::::no-loc(filesystem):::::v1;
```

> [!IMPORTANT]
> W wersji programu Visual Studio 2017 \<:::no-loc(filesystem):::> nagłówek nie był jeszcze standardem C++. C++ w programie Visual Studio 2017 RTW implementuje ostateczną wersję standardową, która znajduje się w [normie ISO/IEC JTC 1/SC 22/N4100](https://wg21.link/n4100). Program Visual Studio 2017 w wersji 15,7 lub nowszej obsługuje nowy standard C++ 17 \<:::no-loc(filesystem):::> .
> Jest to zupełnie nowa implementacja niezgodna z poprzednią `std:::::no-loc(experimental):::` wersją. Było to wymagane przez pomoc techniczną link symboliczny, poprawki błędów i zmiany w zachowaniu standardowym. Obecnie obejmuje \<:::no-loc(filesystem):::> to nowe `std:::::no-loc(filesystem):::` i poprzednie `std:::::no-loc(experimental)::::::::no-loc(filesystem):::` . Obejmuje \<:::no-loc(experimental):::/:::no-loc(filesystem):::> to tylko starą :::no-loc(experimental)::: implementację. :::no-loc(experimental):::Implementacja zostanie usunięta w następnej ABI-twardej wersji bibliotek.

Ten nagłówek obsługuje systemy plików dla jednej z dwóch szerokich klas systemów operacyjnych hosta: Microsoft Windows i POSIX.

Chociaż większość funkcji jest wspólna dla obu systemów operacyjnych, ten dokument określa, gdzie występują różnice. Na przykład:

- System Windows obsługuje wiele nazw głównych, takich jak `c:` lub `\\network_name` . System plików składa się z lasu drzew, z których każdy ma swój własny katalog główny, taki jak `c:\` lub `\\network_name\` , i każdego z nich z własnym bieżącym katalogiem, do ukończenia względnej nazwy ścieżki (która nie jest bezwzględną nazwą ścieżki).

- POSIX obsługuje pojedyncze drzewo bez nazwy głównej, jednego katalogu głównego `/` i jednego bieżącego katalogu.

Kolejną znaczącą różnicą jest natywna reprezentacja nazw ścieżek:

- System Windows używa sekwencji zakończonych znakiem null **`:::no-loc(wchar_t):::`** , kodowanej jako UTF-16 (co najmniej jeden element dla każdego :::no-loc(char)::: acteru).

- POSIX używa sekwencji zakończonych znakiem null **`:::no-loc(char):::`** , kodowanej jako UTF-8 (co najmniej jeden element dla każdego :::no-loc(char)::: acteru).

- Obiekt klasy `path` przechowuje nazwę ścieżki w postaci natywnej, ale obsługuje łatwą konwersję między tym przechowywanym formularzem i kilkoma formularzami zewnętrznymi:

  - Sekwencja zakończona wartością null **`:::no-loc(char):::`** , zakodowana zgodnie z systemem operacyjnym.

  - Sekwencja zakończona wartością null **`:::no-loc(char):::`** , zakodowana jako UTF-8.

  - Sekwencja zakończona wartością null **`:::no-loc(wchar_t):::`** , zakodowana zgodnie z systemem operacyjnym.

  - Sekwencja zakończona wartością null **`:::no-loc(char16_t):::`** , zakodowana jako UTF-16.

  - Sekwencja zakończona wartością null **`:::no-loc(char32_t):::`** , zakodowana jako UTF-32.

  Przekształcenie między tymi reprezentacjami jest korygowane w razie konieczności przy użyciu co najmniej jednego `codecvt` aspektu. Jeśli nie określono określonego obiektu ustawień regionalnych, te zestawy są uzyskiwane z globalnych ustawień regionalnych.

Kolejną różnicą jest to, że każdy system operacyjny pozwala określić uprawnienia dostępu do pliku lub katalogu:

- System Windows rejestruje, czy plik jest tylko do odczytu, czy zapisywalny, atrybut, który nie ma znaczenia dla katalogów.

- POSIX rejestruje, czy plik może być odczytany, zapisany lub wykonany (zeskanowany, jeśli katalog). I czy każda operacja jest dozwolona dla właściciela, grupy właściciela lub dla każdego z nich oraz kilku innych uprawnień.

Wspólne dla obu systemów jest strukturą nałożoną na nazwę ścieżki po pobraniu nazwy głównej. Dla nazwy ścieżki `c:/abc/xyz/def.ext` :

- Nazwa główna to `c:` .

- Katalog główny to `/` .

- Ścieżka katalogu głównego to `c:/` .

- Ścieżka względna to `abc/xyz/def.ext` .

- Ścieżka nadrzędna to `c:/abc/xyz` .

- Nazwa pliku to `def.ext` .

- Trzon ma wartość `def` .

- Rozszerzenie to `.ext` .

Niewielka różnica to preferowany separator między sekwencją katalogów w nazwie ścieżki. Oba systemy operacyjne pozwalają pisać ukośniki `/` , ale w niektórych kontekstach okna preferują ukośnik odwrotny `\` . Implementacja przechowuje swój preferowany separator w składowej danych `preferred_separator` w `path` .

Na koniec `path` obiekty mają ważną funkcję: można ich używać wszędzie tam, gdzie argument filename jest wymagany w klasach zdefiniowanych w nagłówku [\<fstream>](fstream.md) .

Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md).

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[directory_entry, klasa](../standard-library/directory-entry-class.md)|Opisuje obiekt, który jest zwracany przez `directory_iterator` lub `recursive_directory_iterator` i i zawiera `path` .|
|[directory_iterator, klasa](../standard-library/directory-iterator-class.md)|Opisuje iterator danych wejściowych, który przechodzi przez nazwy plików w katalogu systemu plików.|
|[:::no-loc(filesystem):::Klasa _error](../standard-library/:::no-loc(filesystem):::-error-class.md)|Klasa bazowa dla wyjątków zgłaszanych w celu zgłaszania przepełnienia systemu niskiego poziomu.|
|[path, klasa](../standard-library/path-class.md)|Definiuje klasę, która przechowuje obiekt typu szablonu `String` , który jest odpowiedni do użycia jako nazwa pliku.|
|[recursive_directory_iterator, klasa](../standard-library/recursive-directory-iterator-class.md)|Opisuje iterator danych wejściowych, który przechodzi przez nazwy plików w katalogu systemu plików. Iterator może również przydolnać do podkatalogów.|
|[file_status, klasa](../standard-library/file-status-class.md)|Zawija `file_type` .|

### <a name="structs"></a>Struktury

|||
|-|-|
|[Struktura space_info](../standard-library/space-info-structure.md)|Zawiera informacje o woluminie.|

## <a name="functions"></a>Funkcje

[\<:::no-loc(filesystem):::>obowiązki](../standard-library/:::no-loc(filesystem):::-functions.md)

## <a name="operators"></a>Operatory

[\<:::no-loc(filesystem):::>zainteresowanych](../standard-library/:::no-loc(filesystem):::-operators.md)

## <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[copy_options](../standard-library/:::no-loc(filesystem):::-enumerations.md#copy_options)|Wyliczenie, które jest używane z [copy_file](../standard-library/:::no-loc(filesystem):::-functions.md#copy_file) i określa zachowanie, jeśli plik docelowy już istnieje.|
|[directory_options](../standard-library/:::no-loc(filesystem):::-enumerations.md#directory_options)|Wyliczenie określające opcje dla iteratorów katalogu.|
|[file_type](../standard-library/:::no-loc(filesystem):::-enumerations.md#file_type)|Wyliczenie dla typów plików.|
|[perm_options](../standard-library/:::no-loc(filesystem):::-enumerations.md#perm_options)| Wylicza opcje `permissions` funkcji. |
|[uprawnienia](../standard-library/:::no-loc(filesystem):::-enumerations.md#perms)|Typ maski bitowej służący do przekazywania uprawnień i opcji do uprawnień|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
