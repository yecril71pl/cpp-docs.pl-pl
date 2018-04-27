---
title: '&lt;System plików&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
dev_langs:
- C++
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d4b644c5e238e3d07995219dd77fb5bbab13cd0
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltfilesystemgt"></a>&lt;filesystem&gt;

Dołącz nagłówek &lt;filesystem > do uzyskiwania dostępu do klasy i funkcje, które manipulowania i pobieranie informacji na temat ścieżek, plików i katalogów.

## <a name="syntax"></a>Składnia

```cpp
#include <experimental/filesystem> // C++-standard header file name
#include <filesystem> // Microsoft-specific implementation header file name
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Począwszy od wersji programu Visual Studio 2017 r. \<filesystem > nagłówka nie zostało jeszcze C++ standard. Visual C++ 2017 implementuje standardowe ostatecznego projektu, podczas gdy znaleziono w [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf).

Ten nagłówek obsługuje systemy plików dla jednej z dwóch klas szerokie systemów operacyjnych hosta: Microsoft Windows i Posix.

Większość funkcji jest wspólny dla obu systemów operacyjnych, ten dokument identyfikuje, których wystąpić różnice. Na przykład:

- System Windows obsługuje wiele nazw głównych, takich jak c: lub \\\network_name. System plików składa się z lasem drzewa, każda z własnego katalogu głównego, na przykład c:\ lub \\\network_name\\, a każda z własną bieżący katalog kończenia względną nazwę ścieżki (taki, który nie jest ścieżki).

- POSIX obsługuje jedno drzewo bez nazwy głównego katalogu z jednym elementem głównym oraz jeden katalog bieżący.

Inną istotną różnicą jest natywny reprezentacja nazwy ścieżek:

- System Windows używa sekwencji zerem wchar_t zakodowane jako UTF-16 (jeden lub dwa elementy dla każdego znaku).

- POSIX używa sekwencję zerem, char, został zakodowany jako UTF-8 (jeden lub więcej elementów, dla każdego znaku).

- Obiekt klasy ścieżki przechowuje nazwy ścieżki w postaci natywnej, ale obsługuje prosty konwersji między tą przechowywane formularza i kilka formularzy zewnętrznych:

- Sekwencja zerem char, został zakodowany jako favored przez system operacyjny.

- Sekwencja zerem char, został zakodowany jako UTF-8.

- Sekwencja zerem wchar_t zakodowane jako favored przez system operacyjny.

- Sekwencja zerem char16_t, został zakodowany jako UTF-16.

- Sekwencja zerem char32_t zakodowane jako UTF-32.

Interconversions między tymi reprezentacje są przenoszone przez, zgodnie z potrzebami, używając jednego lub więcej `codecvt` aspektami. Jeśli nie wyznaczono obiektu ustawień regionalnych, te aspekty są uzyskiwane z globalnych ustawień regionalnych.

Inna różnica polega na szczegółów, z którym każdy system operacyjny umożliwia określenie uprawnień dostępu do pliku lub katalogu:

1. Rejestruje Windows czy odczytu pliku tylko lub zapisywalny, atrybut, który nie ma znaczenia dla katalogów.

1. POSIX rejestruje, czy plik mogą być odczytywane, napisane lub wykonane (przeprowadzone skanowanie, jeśli katalog), przez właściciela, przez właściciela grupy lub przez każdy, a także kilka innych uprawnień.

Wspólne dla obu systemów struktury nakłada się na nazwę ścieżki po pokonać nazwy głównej. Dla pathname c:/abc/xyz/def.ext:

- Nazwa głównego jest c:.

- Katalog główny jest /.

- Ścieżka katalogu głównego to c: /.

- Ścieżka względna jest abc/xyz/def.ext.

- Ścieżka nadrzędna jest xyz-c:/abc.

- Nazwa pliku jest def.ext.

- Trzon jest def.

- Rozszerzenie jest. zewnętrzne

Drobne różnica polega na **preferowanych separatora**, między sekwencji katalogów w nazwie ścieżki. Obu systemów operacyjnych pozwalają na zapis ukośnik, ale w niektórych kontekstach Windows preferuje ukośnik odwrotny \\.

Na koniec ważna cecha obiektów ścieżki jest, której można je tam, gdzie filename argument jest wymagana w klas zdefiniowanych w nagłówku \<fstream — >.

Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).

## <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[directory_entry, klasa](../standard-library/directory-entry-class.md)|Opisuje obiekt, który jest zwracany przez `directory_iterator` lub `recursive_directory_iterator` i zawiera ścieżkę.|
|[directory_iterator, klasa](../standard-library/directory-iterator-class.md)|W tym artykule opisano iterację wejściowych, które sekwencji za pomocą nazwy pliku w katalogu systemu plików.|
|[filesystem_error, klasa](../standard-library/filesystem-error-class.md)|Klasa podstawowa dla wyjątków, które są zgłaszane do zgłaszania przepełnienie niskiego poziomu systemu.|
|[path, klasa](../standard-library/path-class.md)|Definiuje klasę, która przechowuje typu szablonu obiektu `String` jest odpowiednie do użycia jako nazwę pliku.|
|[recursive_directory_iterator, klasa](../standard-library/recursive-directory-iterator-class.md)|W tym artykule opisano iterację wejściowych, które sekwencji za pomocą nazwy pliku w katalogu systemu plików. Iterator można również malejąca do podkatalogów.|
|[file_status, klasa](../standard-library/file-status-class.md)|Opakowuje `file_type`.|

## <a name="structs"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[space_info, struktura](../standard-library/space-info-structure.md)|Przechowuje informacje o woluminie.|

## <a name="functions"></a>Funkcje

[\<FileSystem > Funkcje](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operatory

[\<FileSystem > operatory](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Wyliczenie, który jest używany z [copy_file —](http://msdn.microsoft.com/4af7a9b0-8861-45ed-b84e-0307f0669d60) i określa zachowanie, jeśli plik docelowy już istnieje.|
|[directory_options —](../standard-library/filesystem-enumerations.md#directory_options)|Wyliczenie określający opcje dla Iteratory katalogu.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Wyliczenie dla typów plików.|
|[PERMS](../standard-library/filesystem-enumerations.md#perms)|Typ maski używany do przekazania uprawnień i opcji, aby uprawnienia|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
