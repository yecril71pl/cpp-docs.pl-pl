---
title: -Ox (Włącz większość optymalizacji szybkości) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
dev_langs:
- C++
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3f5a39201283567285b37a0901929022b688104
ms.sourcegitcommit: 4cbde5d164d681204c4011dc95a921d75292f423
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459169"
---
# <a name="ox-enable-most-speed-optimizations"></a>/OX (Włącz większość optymalizacji szybkości)

**Ox** — opcja kompilatora umożliwia kombinacja optymalizacji, które preferował szybkość. W niektórych wersjach środowiska IDE programu Visual Studio i komunikat pomocy kompilatora, jest to nazywane *Pełna optymalizacja*, ale **ox** — opcja kompilatora umożliwia tylko podzbiór opcje optymalizacji szybkości, które są obsługiwane przez **/O2**.

## <a name="syntax"></a>Składnia

> **/Ox**

## <a name="remarks"></a>Uwagi

**Ox** włącza opcję kompilatora **/O** prędkości Preferuj opcji kompilatora. **Ox** — opcja kompilatora nie ma dodatkowych [/GF (eliminowanie ciągów zduplikowanych)](../../build/reference/gf-eliminate-duplicate-strings.md) i [/Gy (Włącz łączenie poziomie funkcji)](../../build/reference/gy-enable-function-level-linking.md) opcji włączane przez [/O1 lub/O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md). Dodatkowe opcje, które są stosowane przez **/O1** i **/O2** może spowodować, że wskaźnikami do ciągów lub do funkcji Udostępnianie adres docelowy, który może wpływać na debugowanie i zgodność języka strict. **Ox** opcja jest łatwym sposobem Włącz większość optymalizacji bez uwzględniania **/GF** i **/Gy**. Aby uzyskać więcej informacji, zobacz opisy [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) i [/Gy](../../build/reference/gy-enable-function-level-linking.md) opcje.

**Ox** — opcja kompilatora jest taka sama jak w połączeniu przy użyciu następujących opcji:

- [/OB (rozszerzenie funkcji wbudowanej)](../../build/reference/ob-inline-function-expansion.md), gdzie parametr opcji 2 (**/ob2**)

- [/Og (Optymalizacje globalne)](../../build/reference/og-global-optimizations.md)

- [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/OT (Preferuj szybki kod)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (pominięcie wskaźnika ramki)](../../build/reference/oy-frame-pointer-omission.md)

**Ox** jest wzajemnie wykluczających się od:

- [/ O1 (minimalizacja rozmiaru)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od (Wyłącz (Debuguj))](../../build/reference/od-disable-debug.md)

Można anulować odchylenie kierunku szybkości **ox** w przypadku określenia — opcja kompilatora **/Oxs**, które łączy w sobie **ox** — opcja kompilatora przy użyciu  [ /OS (Preferuj mały Kod)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md). Opcje połączone Preferuj mniejszego rozmiaru kodu.  **/Oxs** opcji jest dokładnie taka sama, jak określenie **ox** **/Os** po opcje są wyświetlane w tej kolejności.

Aby zastosować wszystkie dostępne optymalizacje poziomie plików dla kompilacji wydania, firma Microsoft zaleca, należy określić [/O2 (Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) zamiast **ox**, i [/O1 (Minimalizuj rozmiar)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) zamiast tego z **/Oxs**. Jeszcze więcej optymalizacji w wersji kompilacji, należy również rozważyć [/GL (Optymalizacja Całoprogramowa)](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora i [opcję/LTCG (Generowanie kodu Link-time)](../../build/reference/ltcg-link-time-code-generation.md) — opcja konsolidatora.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. W obszarze **właściwości konfiguracji**, otwórz **C/C++** , a następnie wybierz **optymalizacji** stronę właściwości.

1. Modyfikowanie **optymalizacji** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)