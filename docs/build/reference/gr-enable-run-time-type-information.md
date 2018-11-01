---
title: /GR (Włącz informacje typu Run-Time)
ms.date: 11/04/2016
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: b0b618b1018912f1cf0172fc461ac2849c4faf5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579351"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Włącz informacje typu Run-Time)

Dodaje kod do sprawdzania typów obiektów w czasie wykonywania.

## <a name="syntax"></a>Składnia

```
/GR[-]
```

## <a name="remarks"></a>Uwagi

Gdy **GR** jest włączone, kompilator definiuje `_CPPRTTI` makro preprocesora. Domyślnie **GR** znajduje się na. **Trakcie** wyłącza informacje typu run-time.

Użyj **GR** Jeśli kompilator statycznie nie może rozpoznać typu obiektu w kodzie. Zazwyczaj wymaga **GR** opcji, gdy kod używa [dynamic_cast Operator](../../cpp/dynamic-cast-operator.md) lub [typeid](../../cpp/typeid-operator.md). Jednak **GR** zwiększa rozmiar fragmentów .rdata obrazu. Jeśli Twój kod nie korzysta z **dynamic_cast** lub **typeid**, **trakcie** może generować mniejszy obraz.

Aby uzyskać więcej informacji o sprawdzaniu typu run-time, zobacz [informacje typu Run-Time](../../cpp/run-time-type-information.md) w *C++ Language Reference*.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **języka** stronę właściwości.

1. Modyfikowanie **Włącz informacje typu Run-Time** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)