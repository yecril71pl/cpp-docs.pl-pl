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
ms.openlocfilehash: 9be8573f5f9c344d2675bd7c9fc7d8beb3c8cffd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527650"
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

`_pexit` jest podobny do `_penter`; zobacz [/Gh (Włącz _penter funkcja podłączania)](../../build/reference/gh-enable-penter-hook-function.md) przykładem sposobu pisania `_pexit` funkcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)