---
title: /Os, /Ot (Preferuj mały kod, Preferuj szybki kod)
ms.date: 11/04/2016
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
ms.openlocfilehash: 0eda9461b3ef730e0e0a832aa94a688e03c7e1bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336184"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Preferuj mały kod, Preferuj szybki kod)

Minimalizuje lub maksymalizuje rozmiar EXE i bibliotek DLL.

## <a name="syntax"></a>Składnia

```
/Os
/Ot
```

## <a name="remarks"></a>Uwagi

**/Os** (Favor Small Code) minimalizuje rozmiar EXEs i bibliotek DLL, instruując kompilator, aby faworyzował rozmiar ponad szybkość. Kompilator można zmniejszyć wiele konstrukcji C i C++ do funkcjonalnie podobnych sekwencji kodu maszynowego. Czasami różnice te oferują kompromisy wielkości w porównaniu z szybkością. Opcje **/Os** i **/Ot** umożliwiają określenie preferencji dla jednego nad drugim:

**/Ot** (Favor Fast Code) maksymalizuje szybkość EXEs i DLL, instruując kompilator, aby preferował szybkość nad rozmiarem. (Jest to wartość domyślna). Kompilator można zmniejszyć wiele konstrukcji C i C++ do funkcjonalnie podobnych sekwencji kodu maszynowego. Czasami różnice te oferują kompromisy wielkości w porównaniu z szybkością. Opcja **/Ot** jest implikowana przez opcję Maksymalizuj szybkość ([/O2).](o1-o2-minimize-size-maximize-speed.md) Opcja **/O2** łączy w sobie kilka opcji, aby utworzyć bardzo szybki kod.

Jeśli używasz **/Os** lub **/Ot**, należy również określić [/Og,](og-global-optimizations.md) aby zoptymalizować kod.

> [!NOTE]
> Informacje zebrane z przebiegów testów profilowania zastąpią optymalizacje, które w przeciwnym razie miałyby obowiązywać, jeśli określisz **/Ob**, **/Os**lub **/Ot**. Aby uzyskać więcej informacji, [optymalizacje z przewodnikiem profilu](../profile-guided-optimizations.md).

**x86 Specyficzne**

Poniższy przykładowy kod pokazuje różnicę między opcjami Favor Small Code ( /Os ) a opcją Favor Fast Code **(/Ot):The**following example code demonstrates the difference between the Favor Small Code (**/Os**) options and the Favor Fast Code ( /Ot ) option:

> [!NOTE]
> Poniżej opisano oczekiwane zachowanie podczas korzystania **z /Os** lub **/Ot**. Jednak zachowanie kompilatora od wydania do wydania może spowodować różne optymalizacje dla poniższego kodu.

```
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

Jak pokazano w fragmencie kodu maszynowego poniżej, gdy DIFFER.c jest kompilowany dla rozmiaru (**/Os**), kompilator implementuje wyrażenie mnożenia w instrukcji return jawnie jako mnożenie do produkcji krótkiej, ale wolniejszej sekwencji kodu:

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Alternatywnie, gdy DIFFER.c jest skompilowany dla prędkości (**/Ot**), kompilator implementuje `LEA` wyrażenie mnożenia w instrukcji return jako serię zmian i instrukcje do uzyskania szybkiej, ale dłuższej sekwencji kodu:

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**KONIEC x86 Specyficzny**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Kliknij folder **C/C++.**

1. Kliknij stronę właściwości **Optymalizacja.**

1. Zmodyfikuj **właściwość Rozmiar lub Szybkość.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (optymalizuj kod)](o-options-optimize-code.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
