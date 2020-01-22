---
title: Nawigacja w systemie plików
ms.date: 11/04/2016
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: ea9bf44a11087180d3bd02c5dcd5d1acfa4b9e57
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518507"
---
# <a name="file-system-navigation"></a>Nawigacja w systemie plików

W nagłówku > \<systemu C++ plików zaimplementowano specyfikację techniczną typu "ISO/iec TS 18822:2015 (końcowa wersja robocza: [ISO/IEC JTC 1/SC 22/Via 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)), która zawiera typy i funkcje, które umożliwiają pisanie kodu niezależnego od platformy w celu nawigowania w systemie plików. Ponieważ jest to platforma wieloplatformowa, zawiera interfejsy API, które nie są istotne dla systemów Windows. Na przykład oznacza to, że `is_fifo(const path&)` zawsze zwraca **wartość false** w systemie Windows.

## <a name="overview"></a>Omówienie

Użyj \<interfejsu API > dla następujących zadań:

- Iterowanie plików i katalogów w określonej ścieżce

- Uzyskaj informacje na temat plików, w tym czas utworzenia, rozmiar, rozszerzenie i katalog główny

- Twórz, rozkładaj i porównuj ścieżki

- Tworzenie, kopiowanie i Usuwanie katalogów

- Kopiowanie i usuwanie plików

Aby uzyskać więcej informacji na temat we/wy plików przy użyciu standardowej biblioteki, zobacz [programowanie iostream](../standard-library/iostream-programming.md).

## <a name="paths"></a>Ścieżki

### <a name="constructing-and-composing-paths"></a>Konstruowanie i tworzenie ścieżek

Ścieżki w systemie Windows (ponieważ XP) są przechowywane natywnie w formacie Unicode. Klasa [Path](../standard-library/path-class.md) automatycznie wykonuje wszystkie wymagane konwersje ciągów. Akceptuje ona argumenty zarówno szerokiej, jak i wąskich tablic znaków, a także `std::string` i `std::wstring` typy sformatowane jako UTF8 lub UTF16. Klasa `path` również automatycznie normalizuje separatory ścieżki. W argumentach konstruktora można użyć pojedynczego ukośnika w górę jako separatora katalogu. Dzięki temu można używać tych samych ciągów do przechowywania ścieżek w środowiskach Windows i UNIX:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Aby połączyć dwie ścieżki, można użyć przeciążonych `/` i operatorów `/=`, które są analogiczne do `+` i `+=` operatory w `std::string` i `std::wstring`. Obiekt `path` będzie wygodnie dostarczyć separatory, jeśli nie.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Badanie ścieżek

Klasa Path ma kilka metod, które zwracają informacje o różnych częściach samej ścieżki, w odróżnieniu od jednostki systemu plików, do której mogą się odwoływać. Możesz uzyskać katalog główny, ścieżkę względną, nazwę pliku, rozszerzenie pliku i inne. Można wykonać iterację obiektu ścieżki, aby przeanalizować wszystkie foldery w hierarchii. Poniższy przykład pokazuje, jak wykonać iterację ścieżki (nie jest to katalog, do którego się odwołuje) i pobrać informacje o jego częściach.

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

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

int main(int argc, char* argv[])
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

Kod generuje te dane wyjściowe:

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

Klasa `path` przeciąża te same operatory porównania co `std::string` i `std::wstring`. Porównując dwie ścieżki, wykonujesz porównanie ciągów po znormalizowaniu separatorów. Jeśli brakuje końcowego ukośnika (lub ukośnika odwrotnego), nie zostanie on dodany i ma wpływ na porównanie. Poniższy przykład ilustruje sposób porównywania wartości ścieżki:

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

Aby uruchomić ten kod, wklej go do pełnego powyższego przykładu przed `main` i usuń znaczniki komentarza wiersza, który wywołuje go w głównej.

### <a name="converting-between-path-and-string-types"></a>Konwertowanie między ścieżkami i typami ciągów

Obiekt `path` jest niejawnie konwertowany na `std::wstring` lub `std::string`. Oznacza to, że można przekazać ścieżkę do funkcji, takich jak [wofstream:: Open](../standard-library/basic-ofstream-class.md#open), jak pokazano w poniższym przykładzie:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

int main(int argc, char* argv[])
{
    wchar_t* p = L"C:/Users/Public/Documents";
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

Nagłówek > \<systemu plików zawiera typ [directory_iterator](../standard-library/directory-iterator-class.md) do iteracji dla pojedynczych katalogów, a Klasa [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) do iteracji cyklicznie w katalogu i jego podkatalogach. Po utworzeniu iteratora poprzez przekazanie go do `path` obiektu, iterator wskazuje na pierwszy directory_entry w ścieżce. Utwórz iterator końcowy, wywołując Konstruktor domyślny.

Podczas iteracji przez katalog istnieje kilka rodzajów elementów, które mogą wystąpić, w tym między innymi katalogi, pliki, linki symboliczne i pliki gniazda. `directory_iterator` zwraca swoje elementy jako obiekty [directory_entry](../standard-library/directory-entry-class.md) .
