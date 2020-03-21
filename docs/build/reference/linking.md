---
title: Dokumentacja konsolidatora MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: d46874b5eaff889834df284ba90e6c6f196d8d66
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079510"
---
# <a name="linking"></a>Konsolidacja

W C++ projekcie krok *konsolidacji* jest wykonywany po skompilowaniu przez kompilator kodu źródłowego w plikach obiektów (*. obj). Konsolidator (link. exe) łączy pliki obiektów w jeden plik wykonywalny.

Opcje konsolidatora można ustawić wewnątrz lub na zewnątrz programu Visual Studio. W programie Visual Studio można uzyskać dostęp do opcji konsolidatora, klikając prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierając **Właściwości** , aby wyświetlić strony właściwości. Wybierz **konsolidator** w okienku po lewej stronie, aby rozwinąć węzeł i wyświetlić wszystkie opcje.

## <a name="linker-command-line-syntax"></a>Składnia wiersza polecenia konsolidatora

Gdy uruchamiasz LINK poza programem Visual Studio, możesz określić dane wejściowe na jeden lub kilka sposobów:

- W wierszu polecenia

- Używanie plików poleceń

- W zmiennych środowiskowych

Opcja Połącz pierwsze procesy określone w zmiennej środowiskowej LINKu, a następnie opcje w kolejności określonej w wierszu polecenia i w plikach poleceń. Jeśli opcja jest powtórzona przy użyciu różnych argumentów, pierwszeństwo ma ostatnie.

Opcje mają zastosowanie do całej kompilacji; nie można zastosować żadnych opcji do określonych plików wejściowych.

Do uruchomienia LINKu. EXE, użyj następującej składni polecenia:

```
LINK arguments
```

`arguments` zawierają opcje i nazwy plików, które można określić w dowolnej kolejności. Opcje są przetwarzane jako pierwsze, a następnie pliki. Użyj co najmniej jednej spacji lub tabulatorów, aby oddzielić argumenty.

> [!NOTE]
>  To narzędzie można uruchomić tylko z poziomu wiersza polecenia programu Visual Studio. Nie można uruchomić go z poziomu wiersza polecenia systemu lub Eksploratora plików.

## <a name="command-line"></a>Wiersz polecenia

W wierszu polecenia opcja składa się ze specyfikatora opcji, kreski (-) lub ukośnika (/), po którym następuje nazwa opcji. Nazwy opcji nie mogą być skracane. Niektóre opcje przyjmują argument, określony po dwukropku (:). W specyfikacji opcji nie można używać spacji ani tabulatorów, z wyjątkiem cudzysłowu w ciągu w opcji/COMMENT. Określ argumenty liczbowe w notacji dziesiętnej lub w języku C. W nazwach opcji i ich słowach kluczowych lub nazwach plików nie jest rozróżniana wielkość liter, ale w identyfikatorach jako argumenty jest uwzględniana wielkość liter.

Aby przekazać plik do konsolidatora, należy określić nazwę pliku w wierszu polecenia po poleceniu LINK. Można określić ścieżkę bezwzględną lub względną z nazwą pliku i można użyć symboli wieloznacznych w nazwie pliku. W przypadku pominięcia rozszerzenia kropki (.) i nazwy pliku LINK zakłada. obj na potrzeby znajdowania pliku. LINK nie używa rozszerzeń nazw plików ani braku ich w celu założeń dotyczących zawartości plików; Określa typ pliku, sprawdzając go i odpowiednio przetwarza.

link. exe zwraca zero dla sukcesu (bez błędów).  W przeciwnym razie konsolidator zwraca numer błędu, który zatrzymał link.  Na przykład, jeśli konsolidator generuje LNK1104, konsolidator zwraca 1104.  W związku z tym najniższy numer błędu zwrócony w przypadku błędu przez konsolidatora to 1000.  Wartość zwracana przez 128 reprezentuje problem z konfiguracją w systemie operacyjnym lub pliku. config; moduł ładujący nie załadował pliku link. exe lub C2. dll.

## <a name="link-command-files"></a>Wiersze poleceń LINK

Argumenty wiersza polecenia można przekazać do LINKu w postaci pliku poleceń. Aby określić plik poleceń dla konsolidatora, należy użyć następującej składni:

> **LINK \@** <em>CommandFile</em>

*CommandFile* jest nazwą pliku tekstowego. Między znakiem ( **\@** ) i nazwą pliku nie można używać spacji ani tabulatora. Nie ma domyślnego rozszerzenia; należy określić pełną nazwę pliku, łącznie z dowolnym rozszerzeniem. Nie można używać symboli wieloznacznych. Można określić ścieżkę bezwzględną lub względną z nazwą pliku. LINK nie używa zmiennej środowiskowej do wyszukania pliku.

W pliku poleceń argumenty mogą być oddzielone spacjami lub tabulatorami (podobnie jak w wierszu polecenia) i znakami nowego wiersza.

Możesz określić wszystko lub część wiersza polecenia w pliku poleceń. W poleceniu LINKu można użyć więcej niż jednego pliku polecenia. LINK akceptuje dane wejściowe z pliku polecenia, tak jakby były określone w tej lokalizacji w wierszu polecenia. Pliki poleceń nie mogą być zagnieżdżane. LINK zwraca zawartość plików poleceń, o ile nie określono opcji [/nologo](nologo-suppress-startup-banner-linker.md) .

## <a name="example"></a>Przykład

Następujące polecenie do kompilowania biblioteki DLL przekazuje nazwy plików obiektów i bibliotek w oddzielnych plikach poleceń i używa trzeciego pliku poleceń do określenia opcji/EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Zmienne środowiskowe LINK

W narzędziu LINKu są stosowane następujące zmienne środowiskowe:

- LINKI i \_linków\_, jeśli zostały zdefiniowane. Narzędzie LINKu łączy opcje i argumenty zdefiniowane w zmiennej środowiskowej KONSOLIDACJi i dołącza opcje i argumenty zdefiniowane w zmiennej środowiskowej\_ \_do argumentów wiersza polecenia przed przetworzeniem.

- LIB, jeśli jest zdefiniowana. Narzędzia łączy używają ścieżki LIB podczas wyszukiwania obiektu, biblioteki lub innego pliku określonego w wierszu polecenia lub przez opcję [/Base](base-base-address.md) . Używa również ścieżki LIB, aby znaleźć plik. pdb o nazwie w obiekcie. Zmienna LIB może zawierać co najmniej jedną specyfikację ścieżki rozdzieloną średnikami. Jedna ścieżka musi wskazywać podkatalog \lib instalacji wizualizacji C++ .

- ŚCIEŻKA, jeśli narzędzie wymaga uruchomienia CVTRES i nie może znaleźć pliku w tym samym katalogu, co sam LINK. (LINK wymaga CVTRES, aby połączyć plik. res). ŚCIEŻKA musi wskazywać podkatalog \Bin instalacji wizualizacji C++ .

- TMP, aby określić katalog podczas łączenia plików OMF lub res.

## <a name="see-also"></a>Zobacz też

[Odwołanie CC++ /Building](c-cpp-building-reference.md)
[opcje konsolidatora MSVC](linker-options.md)
[pliki definicji modułów (. def)](module-definition-dot-def-files.md)
[Obsługa konsolidatora dla bibliotek DLL ładowanych z opóźnieniem](linker-support-for-delay-loaded-dlls.md)
