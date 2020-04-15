---
title: Dokumentacja konsolidatora MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 2503e212e7325fc97f9057861cb85d5cf0571094
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336496"
---
# <a name="linking"></a>Konsolidacja

W projekcie C++ krok *łączenia* jest wykonywany po kompilatorze skompilował kod źródłowy do plików obiektów (*.obj). Konsolidator (link.exe) łączy pliki obiektów w jeden plik wykonywalny.

Opcje konsolidatora można ustawić wewnątrz lub na zewnątrz programu Visual Studio. W programie Visual Studio można uzyskać dostęp do opcji konsolidatora, klikając prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierając **polecenie Właściwości,** aby wyświetlić strony właściwości. Wybierz **pozycję Konsolidator** w lewym okienku, aby rozwinąć węzeł i wyświetlić wszystkie opcje.

## <a name="linker-command-line-syntax"></a>Składnia wiersza polecenia konsolidatora

Po uruchomieniu łącza poza programem Visual Studio można określić dane wejściowe na jeden lub więcej sposobów:

- W wierszu polecenia

- Korzystanie z plików poleceń

- W zmiennych środowiskowych

Łącze pierwsze opcje procesów określone w zmiennej środowiskowej LINK, a następnie opcje w kolejności, w jakiej są określone w wierszu polecenia i w plikach poleceń. Jeśli opcja jest powtarzana z różnymi argumentami, pierwszeństwo ma ostatni przetworzony.

Opcje dotyczą całej kompilacji; żadne opcje nie mogą być stosowane do określonych plików wejściowych.

Aby uruchomić LINK. EXE, należy użyć następującej składni polecenia:

```
LINK arguments
```

Opcje `arguments` dołączania i nazwy plików i mogą być określone w dowolnej kolejności. Najpierw przetwarzane są opcje, a następnie pliki. Użyj jednego lub więcej spacji lub kart, aby oddzielić argumenty.

> [!NOTE]
> To narzędzie można uruchomić tylko w wierszu polecenia programu Visual Studio. Nie można go uruchomić z wiersza polecenia systemowego lub z Eksploratora plików.

## <a name="command-line"></a>Wiersz polecenia

W wierszu polecenia opcja składa się ze specyfikatora opcji, myślnika (-) lub ukośnika do przodu (/), po którym następuje nazwa opcji. Nazwy opcji nie mogą być skracane. Niektóre opcje przyjmują argument określony po dwukropku (:). Żadne spacje lub karty nie są dozwolone w specyfikacji opcji, z wyjątkiem cytowanego ciągu w /COMMENT opcji. Określ argumenty liczbowe w notacji dziesiętnej lub w języku C. Nazwy opcji i ich argumenty słowa kluczowego lub nazwy pliku nie są uwzględniane wielkość liter, ale identyfikatory jako argumenty są rozróżniane wielkość liter.

Aby przekazać plik do konsolidatora, należy określić nazwę pliku w wierszu polecenia po poleceniu LINK. Można określić ścieżkę bezwzględną lub względną z nazwami plików i można użyć symboli wieloznacznych w nazwach plików. Jeśli pominięto kropkę (.) i rozszerzenie nazwy pliku, LINK przyjmuje .obj w celu znalezienia pliku. LINK nie używa rozszerzeń nazwy pliku lub ich braku do wprowadzania założeń dotyczących zawartości plików; określa typ pliku, badając go i przetwarza go odpowiednio.

plik link.exe zwraca zero dla powodzenia (bez błędów).  W przeciwnym razie konsolidator zwraca numer błędu, który zatrzymał łącze.  Na przykład jeśli konsolidator generuje LNK1104, konsolidator zwraca 1104.  W związku z tym najniższy numer błędu zwrócony na błąd przez konsolidator jest 1000.  Zwracana wartość 128 reprezentuje problem z konfiguracją z systemem operacyjnym lub plikiem .config; ładowarka nie załadowała ani pliku link.exe, ani c2.dll.

## <a name="link-command-files"></a>Wiersze poleceń LINK

Argumenty wiersza polecenia można przekazać do linku w postaci pliku polecenia. Aby określić plik polecenia do konsolidatora, należy użyć następującej składni:

> **Plik \@ ** <em>polecenia</em> LINK

Plik *polecenia* to nazwa pliku tekstowego. Między znakiem (at sign)**\@** a numerem pliku nie jest dozwolone żadne miejsce ani karta. Nie ma rozszerzenia domyślnego; należy określić pełną nazwę pliku, w tym każde rozszerzenie. Symbole wieloznaczne nie mogą być używane. Można określić ścieżkę bezwzględną lub względną z nazwami pliku. Funkcja LINK nie używa zmiennej środowiskowej do wyszukiwania pliku.

W pliku polecenia argumenty mogą być oddzielone spacjami lub kartami (jak w wierszu polecenia) i znakami nowego wiersza.

W pliku polecenia można określić całość wiersza polecenia lub jego część. W poleceniu LINK można użyć więcej niż jednego pliku polecenia. LINK akceptuje dane wejściowe pliku polecenia tak, jakby zostały określone w tej lokalizacji w wierszu polecenia. Nie można zagnieżdżać plików poleceń. LINK odzwierciedla zawartość plików poleceń, chyba że określono opcję [/NOLOGO.](nologo-suppress-startup-banner-linker.md)

## <a name="example"></a>Przykład

Następujące polecenie do utworzenia biblioteki DLL przekazuje nazwy plików obiektów i bibliotek w oddzielnych plikach poleceń i używa trzeciego pliku polecenia do specyfikacji opcji /EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Zmienne środowiskowe LINK

Narzędzie LINK używa następujących zmiennych środowiskowych:

- LINK \_i\_LINK , jeśli są zdefiniowane. Narzędzie LINK dołącza opcje i argumenty zdefiniowane w zmiennej środowiskowej LINK i \_dołącza\_ opcje i argumenty zdefiniowane w zmiennej środowiskowej LINK do argumentów wiersza polecenia przed przetworzeniem.

- LIB, jeśli jest zdefiniowana. Narzędzia LINK używają ścieżki LIB podczas wyszukiwania obiektu, biblioteki lub innego pliku określonego w wierszu polecenia lub przez opcję [/BASE.](base-base-address.md) Używa również ścieżki LIB, aby znaleźć plik pdb o nazwie w obiekcie. Zmienna LIB może zawierać jedną lub więcej specyfikacji ścieżki, oddzielonych średnikami. Jedna ścieżka musi wskazywać podkatalog \lib instalacji języka Visual C++.

- PATH, jeśli narzędzie musi uruchomić CVTRES i nie może znaleźć pliku w tym samym katalogu co sam LINK. (LINK wymaga CVTRES do połączenia pliku .res.) PATH musi wskazywać podkatalog \bin instalacji programu Visual C++.

- TMP, aby określić katalog podczas łączenia plików OMF lub .res.

## <a name="see-also"></a>Zobacz też

[C/C++ Building Reference](c-cpp-building-reference.md)
[Obsługa łącza](linker-support-for-delay-loaded-dlls.md) [plików](module-definition-dot-def-files.md)
Złącza
C/C++ Building Reference[MSVC](linker-options.md)
