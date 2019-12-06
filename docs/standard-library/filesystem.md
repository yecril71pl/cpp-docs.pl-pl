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
ms.openlocfilehash: 0f2c90bd7c1d88a94d1dab05b98442111faa71a2
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898814"
---
# <a name="ltfilesystemgt"></a>&lt;filesystem&gt;

Dołącz nagłówek &lt;systemu plików >, aby uzyskać dostęp do klas i funkcji, które manipulują i pobierają informacje o ścieżkach, plikach i katalogach.

## <a name="syntax"></a>Składnia

```cpp
#include <experimental/filesystem> // C++-standard header file name
#include <filesystem> // Microsoft-specific implementation header file name
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Począwszy od wersji programu Visual Studio 2017, nagłówek > systemu plików \<nie był C++ standardem. C++w programie Visual Studio 2017 (MSVC najnowsze 141) jest zaimplementowany ostatni projekt Standard, który znajduje się w [normie ISO/IEC JTC 1/SC 22/+ 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf).

Ten nagłówek obsługuje systemy plików dla jednej z dwóch szerokich klas systemów operacyjnych hosta: Microsoft Windows i POSIX.

Chociaż większość funkcji jest wspólna dla obu systemów operacyjnych, ten dokument określa, gdzie występują różnice. Na przykład:

- System Windows obsługuje wiele nazw głównych, takich jak c: lub \\\ network_name. System plików składa się z lasu drzew z własnym katalogiem głównym, na przykład c:\ lub \\\ network_name\\oraz z własnym bieżącym katalogiem, aby zakończyć względną nazwę ścieżki (taką, która nie jest bezwzględną nazwą ścieżki).

- POSIX obsługuje pojedyncze drzewo bez nazwy głównej, jednego katalogu głównego/i jednego bieżącego katalogu.

Kolejną znaczącą różnicą jest natywna reprezentacja nazw ścieżek:

- System Windows używa sekwencji wchar_tej o wartości null zakodowanej jako UTF-16 (jeden lub dwa elementy dla każdego znaku).

- W modelu POSIX jest stosowana sekwencja znaków zakończona wartością null, zakodowana jako UTF-8 (co najmniej jeden element dla każdego znaku).

- Obiekt ścieżki klasy przechowuje nazwę ścieżki w postaci natywnej, ale obsługuje łatwą konwersję między tym przechowywanym formularzem i kilkoma formularzami zewnętrznymi:

- Sekwencja znaków zakończona znakiem null, zakodowana zgodnie z systemem operacyjnym.

- Sekwencja znaków zakończona znakiem null, zakodowana jako UTF-8.

- Sekwencja wchar_t zakończona wartością null, zakodowana zgodnie z systemem operacyjnym.

- Sekwencja char16_t zakończona wartością null, zakodowana jako UTF-16.

- Sekwencja char32_t zakończona wartością null zakodowana jako UTF-32.

Przekształcenie między tymi reprezentacjami jest korygowane w razie konieczności przy użyciu co najmniej jednego zestawu reguł `codecvt`. Jeśli określony obiekt ustawień regionalnych nie jest wyznaczono, te zestawy są uzyskiwane z globalnych ustawień regionalnych.

Kolejną różnicą jest to, że każdy system operacyjny pozwala określić uprawnienia dostępu do pliku lub katalogu:

1. System Windows rejestruje, czy plik jest tylko do odczytu, czy tylko do zapisu, atrybut, który nie ma znaczenia dla katalogów.

1. POSIX rejestruje, czy plik może być odczytany, zapisany lub wykonany (zeskanowany, jeśli katalog) przez właściciela, przez grupę właściciela lub przez każdego użytkownika, a także kilka innych uprawnień.

Wspólne dla obu systemów jest strukturą nałożoną na nazwę ścieżki po pobraniu nazwy głównej. Dla nazwy ścieżki c:/ABC/XYZ/def. ext:

- Nazwa główna to c:.

- Katalog główny to/.

- Ścieżka katalogu głównego to c:/.

- Ścieżka względna to ABC/XYZ/def. ext.

- Ścieżka nadrzędna to c:/ABC/XYZ.

- Nazwa pliku jest def. ext.

- Trzon jest def.

- Rozszerzenie to. ext.

Niewielka różnica to **preferowany separator**między sekwencją katalogów w nazwie ścieżki. Oba systemy operacyjne pozwalają napisać ukośnik/, ale w niektórych kontekstach okna preferuje \\ukośnika odwrotnego.

Na koniec ważna funkcja obiektów Path polega na tym, że można ich używać wszędzie tam, gdzie argument filename jest wymagany w klasach zdefiniowanych w nagłówku \<fstream — >.

Aby uzyskać więcej informacji i przykładów kodu, zobacz [Nawigacja systemu plikówC++()](../standard-library/file-system-navigation.md).

## <a name="members"></a>Elementy członkowskie

### <a name="classes"></a>Klasy

|||
|-|-|
|[directory_entry, klasa](../standard-library/directory-entry-class.md)|Opisuje obiekt, który jest zwracany przez `directory_iterator` lub `recursive_directory_iterator` i zawiera ścieżkę.|
|[directory_iterator, klasa](../standard-library/directory-iterator-class.md)|Opisuje iterator danych wejściowych, który przechodzi przez nazwy plików w katalogu systemu plików.|
|[filesystem_error, klasa](../standard-library/filesystem-error-class.md)|Klasa bazowa dla wyjątków zgłaszanych w celu zgłaszania przepełnienia systemu niskiego poziomu.|
|[path, klasa](../standard-library/path-class.md)|Definiuje klasę, która przechowuje obiekt typu szablonu `String`, który jest odpowiedni do użycia jako nazwa pliku.|
|[recursive_directory_iterator, klasa](../standard-library/recursive-directory-iterator-class.md)|Opisuje iterator danych wejściowych, który przechodzi przez nazwy plików w katalogu systemu plików. Iterator może również przydolnać do podkatalogów.|
|[file_status, klasa](../standard-library/file-status-class.md)|Zawija `file_type`.|

### <a name="structs"></a>Struktury

|||
|-|-|
|[space_info, struktura](../standard-library/space-info-structure.md)|Zawiera informacje o woluminie.|

## <a name="functions"></a>Funkcje

[\<funkcje > systemu plików](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operatory

[\<operatory > systemu plików](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Wyliczenie, które jest używane z [copy_file](../standard-library/filesystem-functions.md#copy_file) i określa zachowanie, jeśli plik docelowy już istnieje.|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Wyliczenie, które jest używane z [copy_file](../standard-library/filesystem-functions.md#copy_file) i określa zachowanie, jeśli plik docelowy już istnieje.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Wyliczenie określające opcje dla iteratorów katalogu.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Wyliczenie dla typów plików.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)||
|[uprawnienia](../standard-library/filesystem-enumerations.md#perms)|Typ maski bitowej służący do przekazywania uprawnień i opcji do uprawnień|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
