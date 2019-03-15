---
title: Odwołania konsolidatora MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 3a9eebef0a264b0131311b5ca96011a4d56264a1
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820380"
---
# <a name="linking"></a>Konsolidacja

W projekcie w języku C++ *łączenie* kroku odbywa się po kompilator został skompilowany kod źródłowy w plikach object (*.obj). Łączący (link.exe) łączy pliki obiektu w jednym pliku wykonywalnym. 

Można ustawić opcje konsolidatora wewnątrz lub na zewnątrz programu Visual Studio. W programie Visual Studio, opcje konsolidatora dostępu przez kliknięcie prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań** i wybierając pozycję **właściwości** do wyświetlania na stronach właściwości. Wybierz **konsolidatora** w lewym okienku rozwiń węzeł i wszystkie opcje. 


## <a name="linker-command-line-syntax"></a>Składnia wiersza polecenia konsolidatora

Po uruchomieniu łącze poza programem Visual Studio, należy określić dane wejściowe w jeden lub więcej sposobów:

- W wierszu polecenia

- Korzystanie z plików poleceń

- W zmiennych środowiskowych

Opcje procesów pierwszy LINK określone w zmiennej środowiskowej łącza, następuje opcje w kolejności są one określone w wierszu polecenia i w plikach poleceń. Jeśli opcja jest powtarzany z różnymi argumentami, pierwszeństwo ma ostatni przetworzony.

Opcje mają zastosowanie do całej kompilacji; Brak opcji można zastosować do określonych plików wejściowych.

Aby uruchomić łącza. Plik EXE, należy użyć następującej składni polecenia:

```
LINK arguments
```

`arguments` Obejmują opcje i nazwy plików i może być określony w dowolnej kolejności. Dostępne są opcje przetwarzania pierwsze, następnie pliki. Użyj miejsc do magazynowania lub karty do oddzielenia argumentów.

> [!NOTE]
>  To narzędzie można uruchomić tylko z poziomu wiersza polecenia programu Visual Studio. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików.

## <a name="command-line"></a>Wiersz polecenia

W wierszu polecenia opcję składa się z specyfikator opcji kreski (-) lub ukośnikiem (/), a następnie Nazwa opcji. Nie należy skracać nazwy opcji. Niektóre opcje przyjmować argument, określone po dwukropek (:). Nie spacje lub tabulatory są dozwolone w obrębie Specyfikacja opcji z wyjątkiem w ciąg w cudzysłowie w opcji/Comment. Określ argumenty liczbowe w wartości dziesiętne lub notacji języka C. Nie jest uwzględniana wielkość liter nazw opcji oraz ich argumentach — słowo kluczowe lub nazwę pliku, ale identyfikatorów jako argumentów jest uwzględniana wielkość liter.

Aby przekazać plik do konsolidatora, określ nazwę pliku w wierszu polecenia po poleceniu łącza. Można określić ścieżkę bezwzględną lub względną z nazwę pliku i można używać symboli wieloznacznych w nazwie pliku. Jeśli zostanie pominięty, kropki (.) i rozszerzenie nazwy pliku, łącze przyjęto założenie, .obj, w celu znajdowania plików. ŁĄCZE nie używa rozszerzenia nazw plików lub brak ich się założeń dotyczących zawartości plików. Określa typ pliku, badając ją i przetwarza je w związku z tym.

Link.exe zwraca 0 w przypadku sukcesu (bez błędów).  W przeciwnym razie program łączący zwraca numer błędu, który zatrzymał łącze.  Na przykład jeśli konsolidator wygeneruje LNK1104, konsolidator zwraca 1104.  W związku z tym najniższy numer błędu zwracany w przypadku błędu przez konsolidator wynosi 1000.  Zwracana wartość wynosząca 128 reprezentuje na problem z konfiguracją systemu operacyjnego lub pliku .config; Moduł ładujący nie została załadowana link.exe lub c2.dll.

## <a name="link-command-files"></a>Wiersze poleceń LINK

Argumenty wiersza polecenia można przekazać do LINKU w formie pliku polecenia. Aby określić plik poleceń do konsolidatora, użyj następującej składni:

> **ŁĄCZE \@**  <em>commandfile</em>

*Commandfile* to nazwa pliku tekstowego. Nie spacji lub tabulatorów jest dozwolone między znakiem (**\@**) i nazwę pliku. Nie ma rozszerzenia domyślną; należy określić pełną nazwę pliku, łącznie z dowolnym rozszerzeniem. Nie można używać symboli wieloznacznych. Można określić ścieżkę bezwzględną lub względną nazwę pliku. ŁĄCZE nie używa zmiennej środowiskowej, aby wyszukać ten plik.

W pliku poleceń argumenty mogą być oddzielone tabulacji lub spacji (jak w wierszu polecenia) i znaki nowego wiersza.

Całość lub część wiersza polecenia można określić w pliku poleceń. Można użyć więcej niż jeden plik polecenia za pomocą polecenia łącza. LINK akceptuje dane wejściowe plik poleceń tak, jakby zostały określone w tej lokalizacji, w wierszu polecenia. Pliki poleceń nie mogą być zagnieżdżone. LINK funkcją zawartość plików poleceń, chyba że [/nologo](nologo-suppress-startup-banner-linker.md) określono opcję.

## <a name="example"></a>Przykład

Następujące polecenie, aby tworzyć biblioteki DLL przekazuje nazwy plików obiektów i bibliotek w plikach osobne polecenie i używa innego polecenia w pliku Specyfikacja opcji/EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Zmienne środowiskowe LINK

Narzędzie łącze używane następujące zmienne środowiskowe:

- ŁĄCZA i \_łącze\_, jeśli została zdefiniowana. Narzędzie łącze dołącza opcje i argumenty zdefiniowanej zmiennej środowiskowej łącze i dołącza opcje i argumenty zdefiniowane w \_łącze\_ zmiennej środowiskowej, aby argumenty wiersza polecenia, przed rozpoczęciem przetwarzania.

- LIB, jeśli została zdefiniowana. Narzędzia łącze używa ścieżki LIB, aby wyszukać obiekt, bibliotekę lub inny plik określony w wierszu polecenia lub przez [/BASE](base-base-address.md) opcji. Używa również ścieżki biblioteki można znaleźć pliku .pdb o nazwie w obiekcie. Lib — zmienna może zawierać specyfikacji ścieżki, oddzielając je średnikami. Jedna ścieżka musi wskazywać podkatalog \lib instalację programu Visual C++.

- ŚCIEŻKA, jeśli narzędzie musi zostać uruchomiony CVTRES i nie można odnaleźć pliku w tym samym katalogu co LINKU. (LINK wymaga CVTRES połączyć plik .res). ŚCIEŻKA musi wskazywać w podkatalogu \bin instalację programu Visual C++.

- TMP, aby określić katalog podczas łączenia OMF lub .res plików.

## <a name="see-also"></a>Zobacz także

[Odwołanie kompilacji C/C++](c-cpp-building-reference.md)
[opcje konsolidatora MSVC](linker-options.md)
[pliki definicji modułu (.def)](module-definition-dot-def-files.md)
[Obsługa konsolidatora dla Bibliotek DLL załadowanych z opóźnieniem](linker-support-for-delay-loaded-dlls.md)
