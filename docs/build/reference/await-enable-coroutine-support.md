---
title: -await (Włącz obsługę koprocedury) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /await
- -await
dev_langs:
- C++
helpviewer_keywords:
- /await enable coroutine support [C++]
- -await enable coroutine support [C++]
- await enable coroutine support [C++]
ms.assetid: 302c8e69-09b6-4c58-bcdd-0a6a8713a8df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09cab9f0c7d94c3c51eb63008ec6b7cfb1292f89
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860579"
---
# <a name="await-enable-coroutine-support"></a>/ await (Włącz obsługę koprocedury)

Użyj **/ await** opcję kompilatora, aby włączyć obsługę kompilatora w koprocedury.

## <a name="syntax"></a>Składnia

> / await

## <a name="remarks"></a>Uwagi

**/ Await** — opcja kompilatora umożliwia obsługę kompilatora w koprocedury C++ i słów kluczowych **co_await**, **co_yield**, i **co_return**. Ta opcja jest domyślnie wyłączona. Aby uzyskać informacje na temat obsługi w koprocedury w programie Visual Studio, zobacz [blogu zespołu usługi Visual Studio](https://blogs.msdn.microsoft.com/vcblog/category/coroutine/). Aby uzyskać więcej informacji o propozycji standardowego w koprocedury zobacz [N4628 pracy projektu, specyfikacji technicznej rozszerzenia C++ dla procedur wspólnych](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/n4628.pdf).

**/ Await** opcja jest dostępna począwszy od wersji programu Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz swój projekt **stron właściwości** okno dialogowe.

1. W obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** folder i wybierz polecenie **wiersza polecenia** stronę właściwości.

1. Wprowadź **/ await** w — opcja kompilatora **dodatkowe opcje** pole. Wybierz **OK** lub **Zastosuj** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
