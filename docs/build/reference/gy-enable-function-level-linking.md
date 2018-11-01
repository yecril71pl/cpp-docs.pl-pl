---
title: /Gy (Włączenie łączenia na poziomie funkcji)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableFunctionLevelLinking
- /gy
- VC.Project.VCCLWCECompilerTool.EnableFunctionLevelLinking
helpviewer_keywords:
- enable function-level linking compiler option [C++]
- COMDAT function
- Gy compiler option [C++]
- -Gy compiler option [C++]
- /Gy compiler option [C++]
- packaged functions
ms.assetid: 0d3cf14c-ed7d-4ad3-b4b6-104e56f61046
ms.openlocfilehash: 1fd06b17ca0cfb1583b3014fb2c8f02b5e5a5437
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629921"
---
# <a name="gy-enable-function-level-linking"></a>/Gy (Włączenie łączenia na poziomie funkcji)

Umożliwia kompilatorowi pakowanie indywidualnych funkcji w formę spakowanych funkcji (Comdat).

## <a name="syntax"></a>Składnia

```
/Gy[-]
```

## <a name="remarks"></a>Uwagi

Konsolidator wymaga, że funkcje można osobno spakowany jako Comdat aby wykluczyło lub kolejność poszczególnych funkcji w pliku DLL lub .exe.

Możesz użyć opcji konsolidatora [od (optymalizacje)](../../build/reference/opt-optimizations.md) wykluczyć nieużywane spakowane funkcje z pliku .exe.

Możesz użyć opcji konsolidatora [/order (umieścić funkcje w kolejności)](../../build/reference/order-put-functions-in-order.md) obejmujący opakowane funkcje w kolejności określonej w pliku .exe.

Funkcje śródwierszowe zawsze są pakowane, jeśli są one tworzone jako wywołania (która pojawia się, na przykład, jeśli jest to wbudowanie jest wyłączony lub zapoznasz się z adresu funkcji). Ponadto funkcji składowych języka C++ zdefiniowane w deklaracji klasy, automatycznie są pakowane; inne funkcje nie są, a wybranie tej opcji jest wymagany do kompilowania ich jako spakowane funkcje.

> [!NOTE]
>  [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) , używane do edycji i kontynuowania oraz powoduje **/Gy** opcji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **generowania kodu** stronę właściwości.

1. Modyfikowanie **Włącz łączenie na poziomie dla funkcji** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)