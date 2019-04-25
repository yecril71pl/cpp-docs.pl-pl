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
ms.openlocfilehash: 077096cc296f2aa2128127493a84a91da9a067c5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270916"
---
# <a name="gh-enable-pexit-hook-function"></a>/GH (Włącz funkcję _pexit Hook)

Wywołania `_pexit` funkcję na końcu każdej metody lub funkcji.

## <a name="syntax"></a>Składnia

```
/GH
```

## <a name="remarks"></a>Uwagi

`_pexit` Funkcja nie jest częścią wszystkie biblioteki i jest maksymalnie musisz podać definicję `_pexit`.

Jeśli nie chcesz jawnie wywołać `_pexit`, nie należy podać prototypu. Funkcja musi znajdować się tak, jakby miał poniższy prototyp i musi wypychania zawartości wszystkich rejestrów przy uruchamianiu i pop zawartości bez zmian przy zamykaniu:

```
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit` jest podobny do `_penter`; zobacz [/Gh (Włącz _penter funkcja podłączania)](gh-enable-penter-hook-function.md) przykładem sposobu pisania `_pexit` funkcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
