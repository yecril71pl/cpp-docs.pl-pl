---
title: -Os, -Ot (Preferuj mały kod, Preferuj szybki kod) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed
- /os
- VC.Project.VCCLCompilerTool.FavorSizeOrSpeed
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d74f313caec7ecb98faa3988e8e0dd59847917d5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381520"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Preferuj mały kod, Preferuj szybki kod)

Minimalizuje lub maksymalizuje rozmiar plików exe i dll.

## <a name="syntax"></a>Składnia

```
/Os
/Ot
```

## <a name="remarks"></a>Uwagi

**/OS** (Preferuj mały kod) minimalizuje rozmiar plików exe i dll przez poinstruowanie kompilatora, aby preferował rozmiar nad szybkość. Kompilator może zmniejszyć liczbę konstrukcji języka C i C++ podobne sekwencji z kodu maszynowego. Czasami te różnice oferują wady rozmiar w zależności od szybkości. **/Os** i **/Ot** opcje pozwalają na określenie preferencji dla jednego z nich:

**/OT** (Preferuj szybko kod) maksymalizuje szybkość plików exe i dll przez poinstruowanie kompilatora, aby preferował szybkość nad rozmiar. (Jest to wartość domyślna). Kompilator może zmniejszyć liczbę konstrukcji języka C i C++ podobne sekwencji z kodu maszynowego. Czasami te różnice oferują wady rozmiar w zależności od szybkości. Opcja /Ot jest implikowane, Maksymalizuj szybkość ([/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)) opcji. **/O2** opcja łączy kilka opcji, aby utworzyć bardzo szybki kod.

Jeśli używasz **/Os** lub **/Ot**, a następnie należy także określić [/Og](../../build/reference/og-global-optimizations.md) do optymalizacji kodu.

> [!NOTE]
>  Informacje zebrane w trakcie przebiegów testowych profilowania zastąpią optymalizacje, które normalnie w efekcie w przypadku określenia **/Ob**, **/Os**, lub **/Ot**. Aby uzyskać więcej informacji [optymalizacje Profile-Guided](../../build/reference/profile-guided-optimizations.md).

**x86 Specific**

Poniższy przykład kodu ilustruje różnicę między Preferuj mały kod (**/Os**) opcje i Preferuj szybko kod (**/Ot**) opcja:

> [!NOTE]
>  Poniżej opisano oczekiwane zachowanie w przypadku korzystania z **/Os** lub **/Ot**. Jednak zachowanie kompilatora wersji może spowodować różne optymalizacje dla poniższy kod.

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

Jak pokazano we fragmencie kodu maszynowego poniżej, gdy DIFFER.c jest kompilowany dla rozmiaru (**/Os**), implementuje kompilatora mnożenia wyrażenie w instrukcji return jawnie jako wielokrotnie w celu wygenerowania krótką, ale wolniej sekwencji kodu:

```
mov    eax, DWORD PTR _x$[ebp]
imul   eax, 71                  ; 00000047H
```

Alternatywnie, gdy DIFFER.c jest kompilowany dla danej szybkości (**/Ot**), implementuje kompilatora mnożenia wyrażenie w instrukcji return w postaci serii obiektów shift i `LEA` instrukcje dotyczące tworzenia szybkich, ale dłużej sekwencji kodu:

```
mov    eax, DWORD PTR _x$[ebp]
mov    ecx, eax
shl    eax, 3
lea    eax, DWORD PTR [eax+eax*8]
sub    eax, ecx
```

**KONIEC x86 określonych**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **optymalizacji** stronę właściwości.

1. Modyfikowanie **preferować rozmiar czy szybkość** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)