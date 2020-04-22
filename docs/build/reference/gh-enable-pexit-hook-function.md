---
title: /GH (Włącz funkcję _pexit Hook)
ms.date: 11/04/2016
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: 5382ba90f490aaa12e9e55767fdf15170a69ced5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749225"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (Włącz funkcję _pexit Hook)

Wywołuje `_pexit` funkcję na końcu każdej metody lub funkcji.

## <a name="syntax"></a>Składnia

```
/GH
```

## <a name="remarks"></a>Uwagi

Funkcja `_pexit` nie jest częścią żadnej biblioteki i to do `_pexit`Ciebie należy podanie definicji .

Jeśli nie planujesz `_pexit`jawnie wywołać, nie trzeba podać prototypu. Funkcja musi wyglądać tak, jakby miała następujący prototyp i musi wypchnąć zawartość wszystkich rejestrów przy wejściu i pop niezmienionej zawartości na wyjściu:

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit`jest podobny `_penter`do ; zobacz [/Gh (Włącz _penter funkcji haka)](gh-enable-penter-hook-function.md) na przykład `_pexit` jak napisać funkcję.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Kliknij folder **C/C++.**

1. Kliknij stronę właściwości **Wiersz polecenia.**

1. Wpisz opcję kompilatora w polu **Opcje dodatkowe.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
