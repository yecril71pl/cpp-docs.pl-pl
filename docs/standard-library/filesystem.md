---
title: '&lt;filesystem&gt;'
description: Opisuje klasy, funkcje i typy w nagłówku filesystem biblioteki standardowej C++ .
ms.date: 01/22/2020
f1_keywords:
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: 86be11da1e2cef2fe0ca12691aeb0ce3dbe94202
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076512"
---
# &lt;filesystem&gt;

Dołącz nagłówek &lt;filesystem> w celu uzyskania dostępu do klas i funkcji, które manipulują i pobierają informacje o ścieżkach, plikach i katalogach.

## <a name="syntax"></a>Składnia

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> W wersji programu Visual Studio 2017 nagłówek \<filesystem> nie był jeszcze C++ standardem. C++w programie Visual Studio 2017 RTW implementuje ostateczną wersję standardową, która znajduje się w [normie ISO/IEC JTC 1/SC 22/powyżej 21 N4100](https://wg21.link/n4100). Program Visual Studio 2017 w wersji 15,7 lub nowszej obsługuje nowe filesystem> Standard C++ 17 \<.
> Jest to zupełnie nowa implementacja niezgodna z poprzednią wersją `std::experimental`. Było to wymagane przez pomoc techniczną link symboliczny, poprawki błędów i zmiany w zachowaniu standardowym. Obecnie w tym \<filesystem> udostępnia nowy `std::filesystem` i poprzedni `std::experimental::filesystem`. Uwzględnienie \<experimental/filesystem> zapewnia tylko starą implementację experimental. Implementacja experimental zostanie usunięta w następnej ABIej wersji biblioteki.

Ten nagłówek obsługuje systemy plików dla jednej z dwóch szerokich klas systemów operacyjnych hosta: Microsoft Windows i POSIX.

Chociaż większość funkcji jest wspólna dla obu systemów operacyjnych, ten dokument określa, gdzie występują różnice. Na przykład:

- System Windows obsługuje wiele nazw głównych, takich jak `c:` lub `\\network_name`. System plików składa się z lasu drzew, z których każdy ma swój własny katalog główny, taki jak `c:\` lub `\\network_name\`, oraz z własnym bieżącym katalogiem w celu ukończenia względnej nazwy ścieżki (która nie jest bezwzględną ścieżką).

- POSIX obsługuje pojedyncze drzewo bez nazwy głównej, jednego katalogu głównego `/`i jednego bieżącego katalogu.

Kolejną znaczącą różnicą jest natywna reprezentacja nazw ścieżek:

- System Windows używa sekwencji **wchar_tej** o wartości null zakodowanej jako UTF-16 (co najmniej jeden element dla każdego znaku).

- POSIX używa sekwencji **char** zakończonych znakiem null zakodowaną jako UTF-8 (co najmniej jeden element dla każdego znaku).

- Obiekt klasy `path` przechowuje nazwę ścieżki w postaci natywnej, ale obsługuje łatwą konwersję między tym przechowywanym formularzem i kilkoma formularzami zewnętrznymi:

  - Sekwencja **char** zakończona wartością null, zakodowana zgodnie z systemem operacyjnym.

  - Sekwencja **char** zakończona wartością null, zakodowana jako UTF-8.

  - Sekwencja **wchar_t** zakończona wartością null, zakodowana zgodnie z systemem operacyjnym.

  - Sekwencja **char16_t** zakończona wartością null, zakodowana jako UTF-16.

  - Sekwencja **char32_t** zakończona wartością null zakodowana jako UTF-32.

  Przekształcenie między tymi reprezentacjami jest korygowane w razie konieczności przy użyciu co najmniej jednego zestawu reguł `codecvt`. Jeśli nie określono określonego obiektu ustawień regionalnych, te zestawy są uzyskiwane z globalnych ustawień regionalnych.

Kolejną różnicą jest to, że każdy system operacyjny pozwala określić uprawnienia dostępu do pliku lub katalogu:

- System Windows rejestruje, czy plik jest tylko do odczytu, czy zapisywalny, atrybut, który nie ma znaczenia dla katalogów.

- POSIX rejestruje, czy plik może być odczytany, zapisany lub wykonany (zeskanowany, jeśli katalog). I czy każda operacja jest dozwolona dla właściciela, grupy właściciela lub dla każdego z nich oraz kilku innych uprawnień.

Wspólne dla obu systemów jest strukturą nałożoną na nazwę ścieżki po pobraniu nazwy głównej. Dla nazwy ścieżki `c:/abc/xyz/def.ext`:

- Nazwa główna jest `c:`.

- Katalog główny jest `/`.

- Ścieżka katalogu głównego jest `c:/`.

- Ścieżka względna jest `abc/xyz/def.ext`.

- Ścieżka nadrzędna jest `c:/abc/xyz`.

- Nazwa pliku jest `def.ext`.

- Trzon jest `def`.

- Rozszerzenie jest `.ext`.

Niewielka różnica to preferowany separator między sekwencją katalogów w nazwie ścieżki. Oba systemy operacyjne umożliwiają pisanie ukośnika `/`, ale w niektórych kontekstach okna preferuje `\`ukośnika odwrotnego. Implementacja przechowuje swój preferowany separator w składowej danych `preferred_separator` w `path`.

Na koniec obiekty `path` mają ważną funkcję: można ich używać wszędzie tam, gdzie argument filename jest wymagany w klasach zdefiniowanych w nagłówku [\<fstream — >](fstream.md).

Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja systemu plikówC++()](../standard-library/file-system-navigation.md).

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[Klasa directory_entry](../standard-library/directory-entry-class.md)|Opisuje obiekt, który jest zwracany przez `directory_iterator` lub `recursive_directory_iterator` i zawiera `path`.|
|[Klasa directory_iterator](../standard-library/directory-iterator-class.md)|Opisuje iterator danych wejściowych, który przechodzi przez nazwy plików w katalogu systemu plików.|
|[Klasa filesystem_error](../standard-library/filesystem-error-class.md)|Klasa bazowa dla wyjątków zgłaszanych w celu zgłaszania przepełnienia systemu niskiego poziomu.|
|[Path — Klasa](../standard-library/path-class.md)|Definiuje klasę, która przechowuje obiekt typu szablonu `String`, który jest odpowiedni do użycia jako nazwa pliku.|
|[Klasa recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)|Opisuje iterator danych wejściowych, który przechodzi przez nazwy plików w katalogu systemu plików. Iterator może również przydolnać do podkatalogów.|
|[Klasa file_status](../standard-library/file-status-class.md)|Zawija `file_type`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[Struktura space_info](../standard-library/space-info-structure.md)|Zawiera informacje o woluminie.|

## <a name="functions"></a>Funkcje

[\<filesystemfunkcji >](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operatory

[\<filesystemoperatory >](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Wyliczenie, które jest używane z [copy_file](../standard-library/filesystem-functions.md#copy_file) i określa zachowanie, jeśli plik docelowy już istnieje.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Wyliczenie określające opcje dla iteratorów katalogu.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Wyliczenie dla typów plików.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)| Wylicza opcje funkcji `permissions`. |
|[uprawnienia](../standard-library/filesystem-enumerations.md#perms)|Typ maski bitowej służący do przekazywania uprawnień i opcji do uprawnień|

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
