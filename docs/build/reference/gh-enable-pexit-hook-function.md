---
title: /GH (Włącz funkcję _pexit Hook)
description: Opisuje opcję kompilatora/GH, aby ustawić lokalną funkcję haka _pexit.
ms.date: 07/06/2020
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: b8fc355503055af8b928874ced39cb8224901d3e
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058610"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (Włącz funkcję _pexit Hook)

Wywołuje `_pexit` funkcję na końcu każdej metody lub funkcji.

## <a name="syntax"></a>Składnia

> **`/GH`**

## <a name="remarks"></a>Uwagi

`_pexit`Funkcja nie jest częścią żadnej biblioteki. Istnieje możliwość podania definicji `_pexit` .

Jeśli nie planujesz jawnie wywołania `_pexit` , nie musisz podawać prototypu. Funkcja musi wypchnąć zawartość wszystkich rejestrów we wpisie i wyskakującą niezmieniona zawartość przy zamykaniu. Musi wyglądać tak, jakby miał następujący prototyp:

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

Ta deklaracja nie jest dostępna dla projektów 64-bitowych.

`_pexit`jest podobny do `_penter` ; Zobacz [ `/Gh` (włączanie funkcji Hook _penter)](gh-enable-penter-hook-function.md) , aby zapoznać się z przykładem sposobu pisania `_penter` funkcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz stronę właściwości **Konfiguracja**  >  wiersza polecenia**C/C++**  >  **Command Line** .

1. Wprowadź opcję kompilatora w polu **dodatkowe opcje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[`/Gh`(Włącz funkcję Hook _penter)](gh-enable-penter-hook-function.md)
