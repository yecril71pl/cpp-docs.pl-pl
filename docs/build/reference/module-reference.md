---
title: '/module: Reference (Użyj nazwanego modułu IFC)'
description: 'Użyj opcji kompilatora/module: Reference, aby utworzyć jednostki nagłówka modułu dla nazwy nagłówka lub plików dołączanych.'
ms.date: 09/13/2020
f1_keywords:
- /module:reference
helpviewer_keywords:
- /module:reference
- Use named module IFC
ms.openlocfilehash: 5f40f6b700c38f3238cc7a621313621085fbc289
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079115"
---
# <a name="modulereference-use-named-module-ifc"></a>`/module:reference` (Użyj nazwanego modułu IFC)

Instruuje kompilator, aby używał istniejącego IFC ( *`.ifc`* ) dla bieżącej kompilacji.

## <a name="syntax"></a>Składnia

> **`/module:reference`** *`module-name=filename`*\
> **`/module:reference`** *`filename`*

### <a name="arguments"></a>Argumenty

*`filename`*\
Nazwa pliku, który zawiera *dane IFC*, wstępnie skompilowane informacje modułu. Aby zaimportować więcej niż jeden moduł, należy dołączyć osobną **`/module:reference`** opcję dla każdego pliku.

*`module-name`*\
Prawidłowa nazwa wyeksportowanej nazwy jednostki interfejsu głównego modułu lub pełna nazwa partycji modułu.

## <a name="remarks"></a>Uwagi

**`/module:reference`** Opcja kompilatora wymaga włączenia obsługi modułów eksperymentalnych przy użyciu [`/experimental:module`](experimental-module.md) opcji kompilatora, a także opcji [/std: c + + Najnowsza](std-specify-language-standard-version.md) . Ta opcja jest dostępna od wersji 16,8 programu Visual Studio 2019.

Jeśli **`/module:reference`** argument jest *`filename`* bez *`module-name`* , plik zostanie otwarty w czasie wykonywania, aby sprawdzić, czy *`filename`* nazwa argumentu dotyczy określonego importu. Może to spowodować wolniejszą wydajność środowiska uruchomieniowego w scenariuszach, które mają wiele **`/module:reference`** argumentów.

Wartość *`module-name`* musi być prawidłową nazwą jednostki interfejsu głównego modułu lub pełną nazwą partycji modułu. Przykłady nazw interfejsów modułu podstawowego obejmują:

- `M`
- `M.N.O`
- `MyModule`
- `my_module`

Przykłady pełnych nazw partycji modułu obejmują:

- `M:P`
- `M.N.O:P.Q`
- `MyModule:Algorithms`
- `my_module:algorithms`

Jeśli odwołanie do modułu jest tworzone przy użyciu *`module-name`* , inne moduły w wierszu polecenia nie są przeszukiwane, jeśli kompilator napotka import tej nazwy. Na przykład, uwzględniając ten wiersz polecenia:

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m=n.ifc
```

W powyższym przypadku, jeśli kompilator widzi `import m;` , *`m.ifc`* nie zostanie przeszukany.

### <a name="examples"></a>Przykłady

Podano trzy moduły wymienione w tej tabeli:

| Moduł | Plik IFC |
|--|--|
| *`M`* | *`m.ifc`* |
| *`M:Part1`* | *`m-part1.ifc`* |
| *`Core.Networking`* | *`Networking.ifc`* |

Opcje odwołania przy użyciu *`filename`* argumentu mogą wyglądać następująco:

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m-part.ifc /module:reference Networking.ifc
```

Opcje odwołania przy użyciu *`module-name=filename`* mogą wyglądać następująco:

```cmd
cl ... /experimental:module /module:reference m=m.ifc /module:reference M:Part1=m-part.ifc /module:reference Core.Networking=Networking.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Ustaw listę rozwijaną **konfiguracji** na **wszystkie konfiguracje**.

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby dodać *`/module:reference`* opcję i jej argumenty. Następnie wybierz przycisk **OK** lub **Zastosuj** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[`/experimental:module` (Włącz obsługę modułów)](experimental-module.md)\
[`/headerUnit` (Użyj IFC jednostki nagłówka)](headerunit.md)\
[`/module:exportHeader` (Utwórz jednostki nagłówka)](module-exportheader.md)\
[`/translateInclude` (Przetłumacz dyrektywy include na dyrektywy import)](translateinclude.md)
