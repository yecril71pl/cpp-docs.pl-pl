---
title: /Os, /Ot (Preferuj mały kod, Preferuj szybki kod)
description: Opcje kompilatora MSVC/OS i/OT określają, czy podczas optymalizowania kodu ma być preferowany rozmiar czy szybkość.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
helpviewer_keywords:
- favor fast code compiler option [C++]
- /Os compiler option [C++]
- Ot compiler option [C++]
- /Ot compiler option [C++]
- small machine code
- -Ot compiler option [C++]
- fast code
- favor small code compiler option [C++]
- Os compiler option [C++]
- -Os compiler option [C++]
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
ms.openlocfilehash: 384019ddf7b80b8dd4e00197d73d1e4ac536634c
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180828"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>`/Os`, `/Ot` (Preferuj mały kod, Preferuj szybki kod)

Minimalizuje lub maksymalizuje rozmiar exe i bibliotek DLL.

## <a name="syntax"></a>Składnia

> **`/Os`**\
> **`/Ot`**

## <a name="remarks"></a>Uwagi

**`/Os`**(Preferuj mały kod) minimalizuje rozmiar exe i bibliotek DLL, nakazuje kompilatorowi preferowanie rozmiaru. Kompilator może zmniejszyć wiele konstrukcji C i C++ do funkcjonalnie podobnych sekwencji kodu maszynowego. Sporadycznie te różnice oferują kompromisy wielkości i szybkości. **`/Os`** Opcje i **`/Ot`** umożliwiają określenie preferencji dla jednej w drugim:

**`/Ot`**(Preferuj szybki kod) maksymalizuje szybkość exe i bibliotek DLL, instruując kompilator, aby preferuje szybkość. **`/Ot`** jest wartością domyślną, gdy optymalizacje są włączone. Kompilator może zmniejszyć wiele konstrukcji C i C++ do funkcjonalnie podobnych sekwencji kodu maszynowego. Czasami różnice te oferują kompromisy wielkości i szybkości. **`/Ot`** Opcja jest implikowana przez [`/O2`](o1-o2-minimize-size-maximize-speed.md) opcję (maksymalizuj szybkość). **`/O2`** Opcja łączy kilka opcji, aby utworzyć szybszy kod.

> [!NOTE]
> Informacje gromadzone na podstawie przebiegów testów profilowania zastępują wszelkie optymalizacje, które w przeciwnym razie byłyby stosowane w przypadku określenia **`/Ob`** , **`/Os`** , lub **`/Ot`** . Aby uzyskać więcej informacji, zapoznaj się z tematem [optymalizacje](../profile-guided-optimizations.md)profilowane.

### <a name="x86-specific-example"></a>przykład dotyczący procesora x86

Poniższy przykładowy kod ilustruje różnicę między **`/Os`** opcją (Preferuj mały kod) i **`/Ot`** opcją (Preferuj szybki kod):

> [!NOTE]
> W tym przykładzie opisano oczekiwane zachowanie podczas korzystania z **`/Os`** lub **`/Ot`** . Jednak zachowanie kompilatora z wersji do wydania może spowodować inne optymalizacje dla poniższego kodu.

```c
/* differ.c
  This program implements a multiplication operator
  Compile with /Os to implement multiply explicitly as multiply.
  Compile with /Ot to implement as a series of shift and LEA instructions.
*/
int differ(int x)
{
    return x * 71;
}
```

Jak pokazano w poniższym fragmencie kodu komputera, gdy *`differ.c`* jest kompilowany dla rozmiaru ( **`/Os`** ), kompilator implementuje wyrażenie mnożenia w instrukcji return jawnie jako Pomnóż, aby utworzyć krótką, niemniejszą sekwencję kodu:

```asm
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Alternatywnie, gdy *`differ.c`* jest kompilowany dla szybkości ( **`/Ot`** ), kompilator implementuje wyrażenie mnożenia w instrukcji return jako serię przesunięcia i `LEA` instrukcje w celu utworzenia szybkiej, ale dłuższej sekwencji kodu:

```asm
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości optymalizacji**C/C++** właściwości konfiguracji  >  **Optimization** .

1. Zmodyfikuj wartość właściwości **rozmiar lub szybkość** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](o-options-optimize-code.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
