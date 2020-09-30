---
title: /sourceDependencies (Zgłaszaj zależności na poziomie źródła)
description: Przewodnik dotyczący opcji kompilatora/sourceDependencies w programie Microsoft C++.
ms.date: 07/29/2020
f1_keywords:
- /sourceDependencies
helpviewer_keywords:
- /sourceDependencies compiler option
- /sourceDependencies
ms.openlocfilehash: 0c1866812435c777f6f1fd7ed7f9db788a8cf031
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502843"
---
# <a name="sourcedependencies-report-source-level-dependencies"></a>`/sourceDependencies` (Zależności na poziomie źródła raportu)

Instruuje kompilator, aby wygenerował plik JSON, który zawiera szczegółowe informacje o zależnościach poziomu źródła użytych podczas kompilacji.

Plik JSON zawiera listę zależności źródłowych, takich jak:

- Pliki nagłówkowe (zarówno przechodnie, jak i bezpośrednio dołączone nagłówki).
- Użyta wartość PCH (Jeśli **`/Yu`** jest określona).
- Zaimportowane moduły i zaimportowane jednostki nagłówka (zarówno przechodnie, jak i bezpośrednio importowane moduły/jednostki nagłówkowe).

## <a name="syntax"></a>Składnia

> **`/sourceDependencies`***Nazwa pliku*\
> **`/sourceDependencies`***katalog*

## <a name="arguments"></a>Argumenty

*Nazwa pliku*\
Kompilator zapisuje dane wyjściowe zależności źródłowej do określonej nazwy pliku, co może zawierać ścieżkę względną lub bezwzględną.

*katalogi*\
Jeśli argument jest katalogiem, kompilator generuje pliki zależności źródłowej w określonym katalogu. Nazwa pliku wyjściowego jest oparta na pełnej nazwie pliku wejściowego z dołączonym *`.json`* rozszerzeniem. Na przykład, jeśli plik dostarczony do kompilatora to *`main.cpp`* , wygenerowana nazwa pliku wyjściowego to *`main.cpp.json`* .

## <a name="remarks"></a>Uwagi

**`/sourceDependencies`** Opcja kompilatora jest dostępna w programie Visual Studio 2019 w wersji 16,7. Nie jest on domyślnie włączony.

Po określeniu **`/MP`** opcji kompilatora zalecamy użycie **`/sourceDependencies`** z argumentem katalogu. Jeśli podano pojedynczy argument filename, dwa wystąpienia kompilatora mogą próbować otworzyć plik wyjściowy jednocześnie i przyczynić się do błędu. Aby uzyskać więcej informacji na temat **`/MP`** , zobacz [ `/MP` (kompilacja z wieloma procesami)](mp-build-with-multiple-processes.md).

Gdy wystąpi błąd niekrytycznego kompilatora, informacje o zależnościach nadal są zapisywane w pliku wyjściowym.

Wszystkie ścieżki plików są wyświetlane jako ścieżki bezwzględne w danych wyjściowych.

### <a name="examples"></a>Przykłady

Pobrano następujący przykładowy kod:

```cpp
// main.cpp
#include "header.h"
import m;
import "other.h";

int main() { }
```

Można używać **`/sourceDependencies`** razem z pozostałymi opcjami kompilatora:

> `cl ... /sourceDependencies output.json ... main.cpp`

gdzie `...` reprezentuje inne opcje kompilatora. Ten wiersz polecenia generuje plik JSON *`output.json`* z zawartością podobną do:

```JSON
{
    "Version": "1.0",
    "Data": {
        "Source": "C:\\...\\main.cpp",
        "PCH": "C:\\...\\pch.pch",
        "Includes": [
            "C:\\...\\header.h"
        ],
        "Modules": [
            "C:\\...\\m.ifc",
            "C:\\...\\other.h.ifc"
        ]
    }
}
```

Użyto `...` do skracania raportowanych ścieżek. Raport zawiera ścieżki bezwzględne. Raportowane ścieżki zależą od lokalizacji, w której kompilator odnajdzie zależności. Jeśli wyniki są nieoczekiwane, warto sprawdzić ustawienia ścieżki dołączania projektu.

### <a name="to-set-the-sourcedependencies-compiler-option-in-visual-studio"></a>Aby ustawić opcję kompilatora/sourceDependencies w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** dla projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. W polu **dodatkowe opcje** Dodaj, *`/sourceDependencies: <filename>`* a następnie wybierz przycisk **OK** lub **Zastosuj** , aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Ta opcja nie ma programowego odpowiednika.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
