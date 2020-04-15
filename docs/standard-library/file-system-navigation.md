---
title: Nawigacja w systemie plików
description: Jak poruszać się po systemie plików w standardzie standardu C++ Standard.
ms.date: 04/13/2020
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: 412d865582a14da7b8c31d9f07a43106b0c49491
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368429"
---
# <a name="file-system-navigation"></a>Nawigacja w systemie plików

Nagłówek \<> systemu plików implementuje specyfikację techniczną systemu plików C++ ISO/IEC TS 18822:2015 (wersja robocza końcowa: [ISO/IEC JTC 1/SC 22/WG 21 N4100)](https://wg21.link/n4100)i posiada typy i funkcje umożliwiające pisanie kodu niezależnego od platformy do nawigacji po systemie plików. Ponieważ jest wieloplatformowy, zawiera interfejsy API, które nie są istotne dla systemów Windows. Na przykład `is_fifo(const path&)` zawsze zwraca **false** w systemie Windows.

## <a name="overview"></a>Omówienie

Użyj \<interfejsu API systemu plików> dla następujących zadań:

- iteracji nad plikami i katalogami w określonej ścieżce

- uzyskać informacje o plikach, w tym o czasie utworzenia, rozmiarze, rozszerzeniu i katalogu głównym

- komponowanie, rozkład i porównywanie ścieżek

- tworzenie, kopiowanie i usuwanie katalogów

- kopiowanie i usuwanie plików

Aby uzyskać więcej informacji na temat we/wy pliku przy użyciu biblioteki standardowej, zobacz [Programowanie iostream](../standard-library/iostream-programming.md).

## <a name="paths"></a>Ścieżki

### <a name="constructing-and-composing-paths"></a>Konstruowanie i komponowanie ścieżek

Ścieżki w systemie Windows (od XP) są przechowywane natywnie w unicode. Klasa [ścieżki](../standard-library/path-class.md) automatycznie wykonuje wszystkie niezbędne konwersje ciągów. Akceptuje argumenty zarówno szerokich, jak i wąskich tablic znaków i obu `std::string` i `std::wstring` typów sformatowanych jako UTF8 lub UTF16. Klasa `path` automatycznie normalizuje również separatory ścieżek. Można użyć pojedynczego ukośnika do przodu jako separatora katalogów w argumentach konstruktora. Ten separator umożliwia używanie tych samych ciągów do przechowywania ścieżek zarówno w środowiskach Windows, jak i UNIX:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Aby połączyć dwie ścieżki, można użyć `/` `/=` przeciążonych operatorów, `+` które `+=` są `std::string` `std::wstring`analogiczne do operatorów i operatorów włączonych i . Obiekt `path` wygodnie dostarczy separatory, jeśli tego nie zrobisz.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Badanie ścieżek

Klasa path ma kilka metod, które zwracają informacje o różnych częściach samej ścieżki. Te informacje różnią się od informacji o jednostce systemu plików, do której może się odwoływać. Możesz uzyskać katalog główny, ścieżkę względną, nazwę pliku, rozszerzenie pliku i inne. Można iterować nad obiektem ścieżki, aby zbadać wszystkie foldery w hierarchii. W poniższym przykładzie pokazano, jak iterować nad obiektem ścieżki. I, jak pobrać informacje o jego częściach.

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

wstring DisplayPathInfo()
{
    // This path may or may not refer to an existing file. We are
    // examining this path string, not file system objects.
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");

    wostringstream wos;
    int i = 0;
    wos << L"Displaying path info for: " << pathToDisplay << endl;
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)
    {
        wos << L"path part: " << i++ << L" = " << *itr << endl;
    }

    wos << L"root_name() = " << pathToDisplay.root_name() << endl
        << L"root_path() = " << pathToDisplay.root_path() << endl
        << L"relative_path() = " << pathToDisplay.relative_path() << endl
        << L"parent_path() = " << pathToDisplay.parent_path() << endl
        << L"filename() = " << pathToDisplay.filename() << endl
        << L"stem() = " << pathToDisplay.stem() << endl
        << L"extension() = " << pathToDisplay.extension() << endl;

    return wos.str();
}

int main()
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

Kod tworzy następujące dane wyjściowe:

```Output
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt
path part: 0 = C:
path part: 1 = \
path part: 2 = FileSystemTest
path part: 3 = SubDir3
path part: 4 = SubDirLevel2
path part: 5 = File2.txt
root_name() = C:
root_path() = C:\
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2
filename() = File2.txt
stem() = File2
extension() = .txt
```

### <a name="comparing-paths"></a>Porównywanie ścieżek

Klasa `path` przeciąża te same operatory porównania co `std::string` i `std::wstring`. Podczas porównywania dwóch ścieżek, należy dokonać porównania ciągów po separatory zostały znormalizowane. Jeśli brakuje ukośnika końcowego (lub ukośnika odwrotnego), nie jest on dodawany, co ma wpływ na porównanie. W poniższym przykładzie pokazano, jak wartości ścieżki są porównywane:

```cpp
wstring ComparePaths()
{
    path p0(L"C:/Documents");                 // no trailing separator
    path p1(L"C:/Documents/");                // p0 < p1
    path p2(L"C:/Documents/2013/");           // p1 < p2
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3
    path p4(L"C:/Documents/2014/");           // p3 < p4
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5

    wostringstream wos;
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;
    return wos.str();
}
```

```Output
C:\Documents < C:\Documents\: true
C:\Documents\ < C:\Documents\2013\: true
C:\Documents\2013\ < C:\Documents\2013\Reports\: true
C:\Documents\2013\Reports\ < C:\Documents\2014\: true
C:\Documents\2014\ < D:\Documents\2013\Reports\: true
```

Aby uruchomić ten kod, wklej go `main` do pełnego przykładu powyżej przed i odkomentuj wiersz, który wywołuje go w głównym.

### <a name="converting-between-path-and-string-types"></a>Konwertowanie między typami ścieżek i ciągów

Obiekt `path` jest niejawnie `std::wstring` konwertowany na lub `std::string`. Oznacza to, że można przekazać ścieżkę do funkcji, takich jak [wofstream::open](../standard-library/basic-ofstream-class.md#open), jak pokazano w tym przykładzie:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

int main()
{
    const wchar_t* p{ L"C:/Users/Public/Documents" };
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

```Output
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit
```

## <a name="iterating-directories-and-files"></a>Iterowanie katalogów i plików

Nagłówek \<> systemu plików udostępnia typ [directory_iterator](../standard-library/directory-iterator-class.md) do iteracji w pojedynczych katalogach, a klasa [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do powtarzania powtarzalnej liczby nad katalogiem i jego podkatalogami. Po skonstruowaniu iteratora przez `path` przekazanie go obiektu, iterator wskazuje na pierwszy directory_entry w ścieżce. Utwórz iterator końcowy, wywołując domyślny konstruktor.

Podczas iteracji za pośrednictwem katalogu, istnieje kilka rodzajów elementów, które można odnajdyć. Elementy te obejmują katalogi, pliki, łącza symboliczne, pliki gniazda i inne. Zwraca `directory_iterator` jego elementy jako [directory_entry](../standard-library/directory-entry-class.md) obiektów.
