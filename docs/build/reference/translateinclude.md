---
title: /translateInclude (Przetłumacz dyrektywy include na dyrektywy import)
description: 'Użyj opcji kompilatora/translateInclude, aby przetłumaczyć dyrektywy #include dla nazwy nagłówka, który można zaimportować do dyrektywy import-Name.'
ms.date: 09/13/2020
f1_keywords:
- /translateInclude
helpviewer_keywords:
- /translateInclude
- Translate include directives into import directives
ms.openlocfilehash: 0050f2cb117e48d69cf97a587ef128b9b45790af
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079081"
---
# <a name="translateinclude-translate-include-directives-into-import-directives"></a>`/translateInclude` (Przetłumacz dyrektywy include na dyrektywy import)

Instruuje kompilator, aby przetłumaczy `#include` dyrektywy na nazwę nagłówka z portem do `import header-name;` dyrektywy, zamiast korzystać z dołączania do tekstu.

## <a name="syntax"></a>Składnia

> **`/translateInclude`**

## <a name="remarks"></a>Uwagi

**`/translateInclude`** Opcja kompilatora wymaga włączenia obsługi modułów eksperymentalnych przy użyciu [`/experimental:module`](experimental-module.md) opcji kompilatora, a także opcji [/std: c + + Najnowsza](std-specify-language-standard-version.md) . Ta opcja jest dostępna od wersji 16,8 programu Visual Studio 2019.

**`/translateInclude`** Opcja efektywnie wykonuje następujące przekształcenia, gdzie przykład `<vector>` jest jednostką nagłówka, który można przenieść:

```cpp
#include <vector>
```

Kompilator zastępuje niniejszą dyrektywę:

```cpp
import <vector> ;
```

W MSVC jednostka nagłówka z portem jest nazywana przez **`/headerUnit`** odwołanie. Aby uzyskać więcej informacji, zobacz [ `/headerUnit` (używanie jednostki nagłówka IFC)](headerunit.md).

### <a name="examples"></a>Przykłady

Nadano projekt, który odwołuje się do dwóch plików nagłówkowych i ich jednostek nagłówka wymienionych w tej tabeli:

| Plik nagłówka | Plik IFC |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

I plik źródłowy zawierający *`.cpp`* nagłówki,

```cpp
#include "utils/util.h"
#include "app/app.h"

int main() { }
```

**`/translateInclude`** Opcja umożliwia kompilatorowi Importowanie jednostek nagłówka zamiast ponownego kompilowania nagłówków. Oto przykładowy wiersz polecenia, który tłumaczy dyrektywy include dla *`util.h`* i *`app.h`* w Importy jednostek nagłówka:

```CMD
cl /IC:\ /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Ustaw listę rozwijaną **konfiguracji** na **wszystkie konfiguracje**.

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby dodać *`/translateInclude`* opcję. Następnie wybierz przycisk **OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[`/experimental:module` (Włącz obsługę modułów)](experimental-module.md)\
[ `/headerUnit` (Użyj IFC jednostki nagłówka)](headerunit.md). \
[`/module:exportHeader` (Utwórz jednostki nagłówka)](module-exportheader.md)\
[`/module:reference` (Użyj nazwanego modułu IFC)](module-reference.md)
