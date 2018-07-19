---
title: Nawigacja w systemie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e6e14e0b94000972873b6050f0e8154891b4e57
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026802"
---
# <a name="file-system-navigation"></a>Nawigacja w systemie plików

\<Filesystem > nagłówka implementuje 18822:2015 C++ plik systemu Technical specyfikacji ISO/IEC usług terminalowych (ostatecznego projektu: [JTC ISO/IEC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)) i zawiera typy i funkcje, które umożliwiają użytkownikowi zapis Kod niezależny od platformy do nawigowania w systemie plików. Ponieważ jest dla wielu platform, zawiera interfejsy API, które nie są istotne dla systemu Windows. Oznacza to, że na przykład `is_fifo(const path&)` zawsze zwraca **false** na Windows.

## <a name="overview"></a>Omówienie

Użyj \<filesystem > interfejsy API w celu uwzględnienia poniższych zadań:

- Iteracja plików i katalogów w określonej ścieżce

- uzyskać informacje na temat plików w tym momencie tworzenia, rozmiar, rozszerzenia i katalog główny

- narzędzia Compose, rozkładania i porównywanie ścieżki

- Tworzenie, kopiowanie i usuwanie katalogów

- Kopiuj i usuwaj pliki

Aby uzyskać więcej informacji na temat we/wy pliku przy użyciu standardowej biblioteki zobacz [iostream Programming](../standard-library/iostream-programming.md).

## <a name="paths"></a>Ścieżki

### <a name="constructing-and-composing-paths"></a>Konstruowanie i tworzenie ścieżki

Ścieżki w Windows (od XP) są przechowywane w natywnie w formacie Unicode. [Ścieżki](../standard-library/path-class.md) klasy automatycznie wykonuje wszystkie konwersje niezbędne parametry. Akceptuje argumenty zarówno szerokiej i tablice wąskiego znaku, a także `std::string` i `std::wstring` typy w formacie UTF8 lub UTF16. `path` Klasy również automatycznie normalizuje separatorami ścieżki. Pojedynczy ukośnik służy jako separator katalogu w argumentach konstruktora. Dzięki temu można używać tego samego ciągów do przechowywania ścieżek w środowiskach Windows i UNIX:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Do łączenia dwóch ścieżek, można użyć przeciążonej `/` i `/=` operatorów, które są analogiczne do `+` i `+=` operatory na `std::string` i `std::wstring`. `path` Obiektu wygodnie będzie dostarczać separatory, jeśli nie istnieje.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Badanie ścieżek

Klasa ścieżka ma kilka metod, które zwracają informacje dotyczące różnych części ścieżki, jak różniący się od jednostki systemu plików, którego może dotyczyć. Można uzyskać katalogu głównego, ścieżki względnej, nazwę pliku i rozszerzenie pliku. Użytkownik może przejść przez obiekt ścieżki, aby sprawdzić wszystkie foldery w hierarchii. Poniższy przykład pokazuje, jak iteracji ścieżki (nie do katalogu, który odwołuje się do) i pobieranie informacji o jego części.

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

void main(int argc, char* argv[])
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

### <a name="comparing-paths"></a>Porównywanie ścieżki

`path` Klasy przeciążenia tej samej operatory porównania jako `std::string` i `std::wstring`. Podczas porównywania dwóch ścieżek po mają zostać znormalizowane separatory są wykonywane porównywania ciągów. Jeśli brakuje ukośnika (lub ukośnik odwrotny) nie jest dodawany i wpływa na wynik porównania. W poniższym przykładzie pokazano, jak porównanie wartości ścieżek:

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

Aby uruchomić ten kod, wklej go w pełnym przykładzie powyżej przed `main` i usuń znaczniki komentarza, który ją wywołuje w głównym oknie.

### <a name="converting-between-path-and-string-types"></a>Konwertowanie między typami ścieżki i parametry

A `path` obiekt jest niejawnie konwertowany na `std::wstring` lub `std::string`. Oznacza to, że można podać ścieżkę do funkcji takich jak [wofstream::open](../standard-library/basic-ofstream-class.md#open), jak pokazano w poniższym przykładzie:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

void main(int argc, char* argv[])
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

## <a name="iterating-directories-and-files"></a>Iteracja plików i katalogów

\<Systemu plików > zawiera nagłówek [directory_iterator](../standard-library/directory-iterator-class.md) typu do wykonywania iteracji jednego katalogów i [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) klasy do wykonywania iteracji cyklicznie katalog i jego podkatalogach. Po utworzenia iterator przez przekazanie jej `path` obiektu iterator który wskazuje na pierwszy directory_entry w ścieżce. Utwórz iteratora zakończenia przez wywołanie konstruktora domyślnego.

Podczas iteracji w katalogu, istnieje kilka rodzajów elementów, które można napotkać, w tym między innymi do katalogów, plików, linki symboliczne i plików gniazda. `directory_iterator` Zwraca jego elementów jako [directory_entry](../standard-library/directory-entry-class.md) obiektów.
