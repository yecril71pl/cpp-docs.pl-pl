---
title: '&lt;filesystem&gt;'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
ms.openlocfilehash: a44fc3c6c6a37c20e1e1c294929ae3cb15cece58
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240697"
---
# <a name="ltfilesystemgt"></a>&lt;filesystem&gt;

Dołączyć nagłówek &lt;filesystem > Aby uzyskać dostęp do klasy i funkcje, które manipulowanie i pobieranie informacji na temat ścieżek, pliki i katalogi.

## <a name="syntax"></a>Składnia

```cpp
#include <experimental/filesystem> // C++-standard header file name
#include <filesystem> // Microsoft-specific implementation header file name
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Począwszy od wersji programu Visual Studio 2017 \<filesystem > nagłówka nie zostało jeszcze C++ standard. C++w Visual Studio 2017 (MSVC wersji 141) implementuje standardowe ostatecznego projektu, znaleźć w [JTC ISO/IEC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf).

Ten nagłówek obsługuje systemy plików, dla jednego z dwóch klas szerokiego systemów operacyjnych hosta: Program Microsoft Windows i Posix.

Większość funkcji jest wspólny dla obu systemów operacyjnych, w tym dokumencie określa, gdzie występują różnice. Na przykład:

- Windows obsługuje wiele nazw głównych, takich jak c: lub \\\network_name. System plików, który składa się z lasem drzewa, każdy z własną katalogu głównego, na przykład c:\ lub \\\network_name\\, a każdy z własną bieżącego katalogu, do ukończenia względną nazwę ścieżki (taki, który nie jest ścieżki).

- POSIX obsługuje jedno drzewo bez nazwy katalogu głównego katalogu z jednym elementem głównym / i jeden katalog bieżący.

Inny istotną różnicą jest natywna reprezentacja nazwy ścieżek:

- Windows używa sekwencji zakończony znakiem null wchar_t, zakodowanymi w formacie UTF-16 (jeden lub dwa elementy, dla każdego znaku).

- POSIX używa sekwencję zakończony znakiem null, char, zakodowanymi w formacie UTF-8 (jeden lub więcej elementów, dla każdego znaku).

- Obiekt ścieżki klas przechowuje nazwy ścieżki w postaci natywnej, ale obsługuje proste konwersji między tą przechowywane formularza i kilka postaci zewnętrznych:

- Sekwencja zakończony znakiem null char, zakodowanymi w formacie favored przez system operacyjny.

- Sekwencja zakończony znakiem null char, zakodowanymi w formacie UTF-8.

- Sekwencja zakończony znakiem null wchar_t, zakodowanymi w formacie favored przez system operacyjny.

- Sekwencja zakończony znakiem null char16_t, zakodowanymi w formacie UTF-16.

- Sekwencja zakończony znakiem null char32_t, zakodowanymi w formacie UTF-32.

Interconversions między te oświadczenia są przenoszone przez, zgodnie z potrzebami przy użyciu jednej lub więcej `codecvt` aspektami. Jeśli nie wyznaczono obiekt ustawień regionalnych, tych zestawów reguł są uzyskiwane z globalnych ustawień regionalnych.

Inna różnica polega na szczegóły, z którym każdy system operacyjny umożliwia określenie uprawnień dostępu do pliku lub katalogu:

1. Rekordy Windows czy odczytu pliku tylko lub zapisywalnego, atrybut, który nie ma znaczenia w przypadku katalogów.

1. POSIX — rejestruje, czy plik mogą być odczytywane, napisane, czy wykonywany (skanowane Jeśli katalogu), przez właściciela, przez właściciela grupy lub przez każdy, a także kilka innych uprawnień.

Wspólny dla obu systemów struktury nakłada się na nazwę ścieżki po pokonać nazwę katalogu głównego. Aby uzyskać c:/abc/xyz/def.ext nazwy ścieżki:

- Nazwa głównego to c:.

- Katalog główny jest /.

- Ścieżka katalogu głównego to c: /.

- Ścieżka względna jest abc/xyz/def.ext.

- Ścieżka nadrzędna jest xyz-c:/abc.

- Nazwa pliku jest def.ext.

- Stem jest def.

- To rozszerzenie. zewnętrzne

Drobne różnica polega na tym **preferowanych separator**, między sekwencji katalogów w nazwie ścieżki. Oba systemy operacyjne umożliwiają napisanie ukośnik /, ale w niektórych kontekstach Windows preferuje ukośnik odwrotny \\.

Na koniec ważną funkcją obiekty ścieżki jest, że można ich używać w dowolnym miejscu w klas zdefiniowanych w nagłówku wymagany jest argument pliku \<fstream — >.

Aby uzyskać więcej informacji i przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[directory_entry, klasa](../standard-library/directory-entry-class.md)|Opisuje obiekt, który jest zwracany przez `directory_iterator` lub `recursive_directory_iterator` i zawiera ścieżkę.|
|[directory_iterator, klasa](../standard-library/directory-iterator-class.md)|Opisuje iterator danych wejściowych, które sekwencji za pomocą nazwy plików w katalogu systemu plików.|
|[filesystem_error, klasa](../standard-library/filesystem-error-class.md)|Klasa bazowa dla wyjątków, które są generowane do zgłaszania przepełnienie niskiego poziomu systemu.|
|[path, klasa](../standard-library/path-class.md)|Definiuje klasę, która przechowuje obiekt typu szablonu `String` który jest odpowiedni do użytku jako nazwę pliku.|
|[recursive_directory_iterator, klasa](../standard-library/recursive-directory-iterator-class.md)|Opisuje iterator danych wejściowych, które sekwencji za pomocą nazwy plików w katalogu systemu plików. Iterator który można również jest elementem podrzędnym elementu do podkatalogów.|
|[file_status, klasa](../standard-library/file-status-class.md)|Opakowuje `file_type`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[space_info, struktura](../standard-library/space-info-structure.md)|Przechowuje informacje o woluminie.|

## <a name="functions"></a>Funkcje

[\<System plików > funkcji](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operatory

[\<System plików > operatorów](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Wyliczenie, które jest używane z [copy_file —](../standard-library/filesystem-functions.md#copy_file) i określa zachowanie, jeśli plik docelowy już istnieje.|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Wyliczenie, które jest używane z [copy_file —](../standard-library/filesystem-functions.md#copy_file) i określa zachowanie, jeśli plik docelowy już istnieje.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Wyliczenie, które określa opcje dla iteratorów katalogu.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Wyliczenie dla typów plików.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)||
|[PERMS](../standard-library/filesystem-enumerations.md#perms)|Typ maski bitów używany do przekazywania, uprawnień i opcje uprawnień|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
