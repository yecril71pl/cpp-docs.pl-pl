---
title: /headerUnit (Użyj obiektu IFC jednostki nagłówka)
description: Użyj opcji kompilatora/headerUnit, aby określić istniejącą jednostkę nagłówka IFC do zaimportowania w bieżącej kompilacji.
ms.date: 09/13/2020
f1_keywords:
- /headerUnit
helpviewer_keywords:
- /headerUnit
- Use header unit IFC
ms.openlocfilehash: 2734df728b188dcfbbe5f475cfc67715a070975d
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079119"
---
# <a name="headerunit-use-header-unit-ifc"></a>`/headerUnit` (Użyj IFC jednostki nagłówka)

Instruuje kompilator, aby przetłumaczy `#include` dyrektywy na nazwę nagłówka z portem do `import header-name;` dyrektywy, zamiast korzystać z dołączania do tekstu.

## <a name="syntax"></a>Składnia

> **`/headerUnit`** *`header-filename`*=*`ifc-filename`*

### <a name="arguments"></a>Argumenty

*`header-filename`*\
Nazwa pliku, do którego kompilator rozpoznaje `header-name` . Podczas `import header-name ;` gdy kompilator rozpoznaje `header-name` plik na dysku. Użyj *`header-filename`* , aby określić ten plik. Po dopasowaniu kompilator otwiera odpowiadający mu obiekt IFC o nazwie *`ifc-filename`* na potrzeby importowania.

*`ifc-filename`*\
Nazwa pliku, który zawiera *dane IFC*, wstępnie skompilowane informacje modułu. Aby zaimportować więcej niż jedną jednostkę nagłówka, należy dołączyć osobną **`/headerUnit`** opcję dla każdego pliku.

## <a name="remarks"></a>Uwagi

**`/headerUnit`** Opcja kompilatora wymaga włączenia obsługi modułów eksperymentalnych przy użyciu [`/experimental:module`](experimental-module.md) opcji kompilatora, a także opcji [/std: c + + Najnowsza](std-specify-language-standard-version.md) . Ta opcja jest dostępna od wersji 16,8 programu Visual Studio 2019.

Kompilator nie może mapować jednego *`header-name`* do wielu plików IFC. Chociaż mapowanie wielu *`header-name`* argumentów do pojedynczego IFC jest możliwe, nie jest to zalecane. Zawartość IFC zostanie zaimportowana tak, jakby była tylko nagłówkiem określonym przez *`header-name`* .

### <a name="examples"></a>Przykłady

Nadano projekt, który odwołuje się do dwóch plików nagłówkowych i ich jednostek nagłówka wymienionych w tej tabeli:

| Plik nagłówka | Plik IFC |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

Opcje kompilatora odwołujące się do jednostek nagłówka dla tych określonych plików nagłówkowych mogą wyglądać podobnie do tego przykładu:

```CMD
cl ... /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Ustaw listę rozwijaną **konfiguracji** na **wszystkie konfiguracje**.

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby dodać *`/headerUnit`* Opcje i argumenty. Następnie wybierz przycisk **OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[`/experimental:module` (Włącz obsługę modułów)](experimental-module.md)\
[`/module:exportHeader` (Utwórz jednostki nagłówka)](module-exportheader.md)\
[`/module:reference` (Użyj nazwanego modułu IFC)](module-reference.md)\
[`/translateInclude` (Przetłumacz dyrektywy include na dyrektywy import)](translateinclude.md)\
