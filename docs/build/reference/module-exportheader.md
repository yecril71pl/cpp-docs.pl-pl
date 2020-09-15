---
title: '/module: exportHeader (tworzenie jednostek nagłówka)'
description: 'Użyj opcji kompilatora/module: exportHeader, aby utworzyć jednostki nagłówka modułu dla nazwy nagłówka lub plików dołączanych.'
ms.date: 09/13/2020
f1_keywords:
- /module:exportHeader
helpviewer_keywords:
- /module:exportHeader
- Create header units
ms.openlocfilehash: f0c0ce1c593df742af77aa36189df1e89de75b6b
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079082"
---
# <a name="moduleexportheader-create-header-units"></a>`/module:exportHeader` (Utwórz jednostki nagłówka)

Instruuje kompilator, aby utworzył jednostki nagłówka określone przez argumenty wejściowe. Kompilator generuje dane wyjściowe w plikach IFC ( *`.ifc`* ).

## <a name="syntax"></a>Składnia

> **`/module:exportHeader`** *`header-name`* \[...]\
> **`/module:exportHeader`** *`filename`* \[...]

### <a name="arguments"></a>Argumenty

*`header-name`*\
Plik nagłówka do wyeksportowania. *`header-name`* Argument musi przyjmować ten sam formularz jako argument do `#include` dyrektywy.

*`filename`*\
Względna lub bezwzględna ścieżka do pliku nagłówkowego, z którego ma zostać utworzona jednostka nagłówka.

## <a name="remarks"></a>Uwagi

**`/module:exportHeader`** Opcja kompilatora wymaga włączenia obsługi modułów eksperymentalnych przy użyciu [`/experimental:module`](experimental-module.md) opcji kompilatora, a także opcji [/std: c + + Najnowsza](std-specify-language-standard-version.md) . Ta opcja jest dostępna od wersji 16,8 programu Visual Studio 2019.

Jedna **`/module:exportHeader`** Opcja kompilatora może określić tyle argumentów nazwy nagłówka, ile jest wymagana kompilacja. Nie trzeba określać ich osobno.

Domyślnie kompilator nie tworzy pliku obiektu w przypadku skompilowania jednostki nagłówka. Aby utworzyć plik obiektu, określ **`/Fo`** opcję kompilatora. Aby uzyskać więcej informacji, zobacz [ `/Fo` (nazwa pliku obiektu)](fo-object-file-name.md).

Kompilator rozpoznaje w *`header-name`* oparciu o kolejność przeszukiwania katalogów, w tym wszystkie określone. Aby uzyskać więcej informacji, zobacz [ `/I` (Dodatkowe katalogi dołączane)](i-additional-include-directories.md).

Argument *`header-name`* musi być określony tak samo jak w źródle. Argument jest wrażliwy na reguły i `<` `>` Operatory operatora i w wierszu polecenia. Prawidłowe polecenie ucieczki w celu skompilowania jednostki nagłówka, takiej jak `<vector>` użycie wiersza polecenia VS2019 może wyglądać następująco:

```cmd
cl ... /experimental:module /module:exportHeader "<vector>"
```

Tworzenie lokalnego nagłówka projektu, takiego jak `"utils/util.h"` może wyglądać następująco:

```cmd
cl ... /experimental:module /module:exportHeader """util/util.h"""
```

Reguły Quote w innych procesorach wiersza polecenia mogą się różnić.

W przypadku korzystania z *`header-name`* formy **`/module:exportHeader`** , przydatne może być użycie opcji uzupełniającej **`/module:showResolvedHeader`** . **`/module:showResolvedHeader`** Opcja drukuje ścieżkę bezwzględną do pliku, *`header-name`* do którego argument jest rozpoznawany.

**`/module:exportHeader`** może obsługiwać wiele wejść jednocześnie, nawet w obszarze **`/MP`** . Zalecamy użycie **`/module:output <directory>`** programu do utworzenia osobnego pliku IFC dla każdej kompilacji.

### <a name="examples"></a>Przykłady

Podaną nagłówki `"C:\util\util.h"` i `"C:\app\app.h"` , można eksportować je jako *`header-name`* argumenty przy użyciu tego polecenia:

```cmd
cl /IC:\ /experimental:module /module:exportHeader """util/util.h""" """app/app.h""" /FoC:\obj
```

Za pomocą tego polecenia można eksportować je jako *`filename`* argumenty:

```cmd
cl /IC:\ /experimental:module /module:exportHeader C:\util\util.h C:\app\app.h /FoC:\obj
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Ustaw listę rozwijaną **konfiguracji** na **wszystkie konfiguracje**.

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby dodać *`/module:exportHeader`* opcję i wszystkie argumenty. Następnie wybierz przycisk **OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[`/experimental:module` (Włącz obsługę modułów)](experimental-module.md)\
[`/headerUnit` (Użyj IFC jednostki nagłówka)](headerunit.md)\
[`/module:reference` (Użyj nazwanego modułu IFC)](module-reference.md)\
[`/translateInclude` (Przetłumacz dyrektywy include na dyrektywy import)](translateinclude.md)
