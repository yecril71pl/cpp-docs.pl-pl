---
title: -Os -Ot (Preferuj mały kod, Preferuj szybki kod) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9f97ab0a53eb82b65149ea0f27139743e065f7ea
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378912"
---
# <a name="os-ot-favor-small-code-favor-fast-code"></a>/Os, /Ot (Preferuj mały kod, Preferuj szybki kod)
Minimalizuje lub maksymalizuje rozmiar plików exe i dll.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Os  
/Ot  
```  
  
## <a name="remarks"></a>Uwagi  
 **/ OS** (Preferuj mały kod) minimalizuje rozmiar plików exe i dll przez poinstruowanie kompilatora, aby preferował rozmiar nad szybkość. Kompilator może zmniejszyć wiele konstrukcji C i C++ podobne sekwencji kodu maszyny. Czasami różnice te oferują wady i zalety rozmiaru w zależności od szybkości. **/OS** i **/Ot** opcje umożliwiają określenie preferencji dla siebie:  
  
 **/OT** (Preferuj szybki kod) maksymalizuje szybkość plików exe i dll przez poinstruowanie kompilatora, aby preferował szybkość nad rozmiar. (Jest to wartość domyślna). Kompilator może zmniejszyć wiele konstrukcji C i C++ podobne sekwencji kodu maszyny. Czasami różnice te oferują wady i zalety rozmiaru w zależności od szybkości. Opcja /Ot jest implikowana przez Maksymalizuj szybkość ([/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)) opcja. **/O2** opcja łączy kilka opcji, aby wygenerować kod bardzo szybko.  
  
 Jeśli używasz **/OS** lub **/Ot**, a następnie należy również określić [/Og](../../build/reference/og-global-optimizations.md) do optymalizacji kodu.  
  
> [!NOTE]
>  Informacje, które są zbierane z profilowania uruchomień testów spowoduje zastąpienie optymalizacji, które w przeciwnym razie będą w efekcie Jeśli określisz **/Ob**, **/OS**, lub **/Ot**. Aby uzyskać więcej informacji [optymalizacje Profile-Guided](../../build/reference/profile-guided-optimizations.md).  
  
 **x86 Specific**  
  
 Poniższy przykładowy kod przedstawia różnice między Preferuj mały kod (**/OS**) opcje i Preferuj szybki kod (**/Ot**) opcja:  
  
> [!NOTE]
>  Poniżej opisano oczekiwane zachowanie w przypadku korzystania z **/OS** lub **/Ot**. Jednak zachowanie kompilatora wersji wersji może spowodować różne opcje optymalizacji kodu poniżej.  
  
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
  
 Jak przedstawiono fragment kodu maszynowego poniżej, gdy DIFFER.c jest skompilowany dla rozmiaru (**/OS**), implementuje kompilatora mnożenia wyrażenie w instrukcji return jawnie jako wielokrotnie w celu utworzenia sekwencji krótki, ale wolniej kodu:  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
imul   eax, 71                  ; 00000047H  
```  
  
 Alternatywnie, jeśli DIFFER.c skompilowanych dla poprawy szybkości (**/Ot**), implementuje kompilatora mnożenia wyrażenie w instrukcji return w postaci serii shift i `LEA` instrukcjami, aby utworzyć sekwencję szybki, ale dłużej kodu:  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
mov    ecx, eax  
shl    eax, 3  
lea    eax, DWORD PTR [eax+eax*8]  
sub    eax, ecx  
```  
  
 **KOŃCOWY x86 określonych**  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **optymalizacji** strony właściwości.  
  
4.  Modyfikowanie **preferować rozmiar czy szybkość** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)