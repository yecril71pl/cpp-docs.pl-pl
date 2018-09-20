---
title: -Oi (Generuj funkcje wewnętrzne) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableIntrinsicFunctions
- /oi
- VC.Project.VCCLWCECompilerTool.EnableIntrinsicFunctions
dev_langs:
- C++
helpviewer_keywords:
- Oi compiler option [C++]
- intrinsic functions, generate
- /Oi compiler option [C++]
- -Oi compiler option [C++]
- generate intrinsic functions compiler option [C++]
ms.assetid: fa4a3bf6-0ed8-481b-91c0-add7636132b4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 792d1e1bc0ea2f6044bc9ad145d30c1fda3e3648
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423874"
---
# <a name="oi-generate-intrinsic-functions"></a>/Oi (Generuj funkcje wewnętrzne)

Zastępuje niektórych funkcji wywołuje w formularzach wewnętrzne lub w przeciwnym razie specjalnych funkcji, które pomagają aplikacji są wykonywane szybciej.

## <a name="syntax"></a>Składnia

```
/Oi[-]
```

## <a name="remarks"></a>Uwagi

Programy, które używają funkcje wewnętrzne są szybsze, ponieważ nie masz obciążenie związane z wywołania funkcji, ale może być większy ze względu na dodatkowy kod utworzony.

Zobacz [wewnętrzne](../../preprocessor/intrinsic.md) Aby uzyskać więcej informacji, na którym funkcje mają wewnętrzne formularzy.

**/OI** jest tylko żądania do kompilatora do zamiany wywołania funkcji, niektóre funkcje wewnętrzne; kompilator może wywołać funkcję (i nie Zamień na wywołanie funkcji wewnętrznej) Jeśli spowoduje lepszą wydajność.

**x86 Specific**

Wewnętrzne funkcje zmiennoprzecinkowe nie wykonywać żadnych specjalnych kontrole wartości wejściowe więc pracować w zakresach ograniczonych danych wejściowych i obsługę różnych wyjątków i warunków ograniczających niż biblioteki procedur o takiej samej nazwie. Za pomocą formularzy wewnętrzne true oznacza utraty IEEE wyjątków i utraty `_matherr` i `errno` funkcjonalności; jego oznacza utratę zgodność ANSI. Jednak wewnętrzne formularzy znacznie przyspieszyć floating-point intensywnie programów i wiele programów, problemów ze zgodnością są nieco praktyczne wartości.

Możesz użyć [Za](../../build/reference/za-ze-disable-language-extensions.md) opcję kompilatora, aby zastąpić generowania true wewnętrzne opcje zmiennoprzecinkowych. W takich przypadkach funkcje są generowane jako biblioteki procedur, które argumenty przekazywane bezpośrednio do zmiennoprzecinkowych mikroukładu zamiast wypychanie ich na stosie program.

**KONIEC x86 określonych**

Możesz także użyć [wewnętrzne](../../preprocessor/intrinsic.md) tworzyć funkcje wewnętrzne lub [— funkcja (C/C++)](../../preprocessor/function-c-cpp.md) jawnie wymusić wywołanie funkcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **optymalizacji** stronę właściwości.

1. Modyfikowanie **Włącz funkcje wewnętrzne** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableIntrinsicFunctions%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Funkcje wewnętrzne kompilatora](../../intrinsics/compiler-intrinsics.md)