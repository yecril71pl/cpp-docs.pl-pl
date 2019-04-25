---
title: / await (Włącz obsługę koprocedury)
ms.date: 08/15/2017
f1_keywords:
- /await
- -await
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
ms.openlocfilehash: c0c8c0183c356900ba8f95d39e427d56eb1ec96b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295009"
---
# <a name="await-enable-coroutine-support"></a>/ await (Włącz obsługę koprocedury)

Użyj **/ await** opcję kompilatora, aby włączyć obsługę kompilatora w koprocedury.

## <a name="syntax"></a>Składnia

> / await

## <a name="remarks"></a>Uwagi

**/ Await** — opcja kompilatora umożliwia obsługę kompilatora C++ koprocedury i słowa kluczowe **co_await**, **co_yield**, i **co_return**. Ta opcja jest domyślnie wyłączona. Aby uzyskać informacje na temat obsługi w koprocedury w programie Visual Studio, zobacz [blogu zespołu usługi Visual Studio](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/). Aby uzyskać więcej informacji o propozycji standardowego w koprocedury zobacz [N4628 pracy projektu, specyfikacji technicznej rozszerzenia C++ dla procedur wspólnych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf).

**/ Await** opcja jest dostępna począwszy od wersji programu Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz swój projekt **stron właściwości** okno dialogowe.

1. W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** folder i wybierz polecenie **wiersza polecenia** stronę właściwości.

1. Wprowadź **/ await** w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
