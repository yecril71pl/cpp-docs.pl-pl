---
title: /OX (Włącz większość optymalizacji szybkości)
ms.date: 10/18/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: e39905608087425fe5a445f4ef88434d73bb2ded
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811280"
---
# <a name="ox-enable-most-speed-optimizations"></a>/OX (Włącz większość optymalizacji szybkości)

**Ox** — opcja kompilatora umożliwia kombinacja optymalizacji, które preferował szybkość. W niektórych wersjach środowiska IDE programu Visual Studio i komunikat pomocy kompilatora, jest to nazywane *Pełna optymalizacja*, ale **ox** — opcja kompilatora umożliwia tylko podzbiór opcje optymalizacji szybkości, które są obsługiwane przez **/O2**.

## <a name="syntax"></a>Składnia

> **/Ox**

## <a name="remarks"></a>Uwagi

**Ox** włącza opcję kompilatora **/O** prędkości Preferuj opcji kompilatora. **Ox** — opcja kompilatora nie ma dodatkowych [/GF (eliminowanie ciągów zduplikowanych)](gf-eliminate-duplicate-strings.md) i [/Gy (Włącz łączenie poziomie funkcji)](gy-enable-function-level-linking.md) opcji włączane przez [/O1 lub/O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](o1-o2-minimize-size-maximize-speed.md). Dodatkowe opcje, które są stosowane przez **/O1** i **/O2** może spowodować, że wskaźnikami do ciągów lub do funkcji Udostępnianie adres docelowy, który może wpływać na debugowanie i zgodność języka strict. **Ox** opcja jest łatwym sposobem Włącz większość optymalizacji bez uwzględniania **/GF** i **/Gy**. Aby uzyskać więcej informacji, zobacz opisy [/GF](gf-eliminate-duplicate-strings.md) i [/Gy](gy-enable-function-level-linking.md) opcje.

**Ox** — opcja kompilatora jest taka sama jak w połączeniu przy użyciu następujących opcji:

- [/OB (rozszerzenie funkcji wbudowanej)](ob-inline-function-expansion.md), gdzie parametr opcji 2 (**/ob2**)

- [/Og (Optymalizacje globalne)](og-global-optimizations.md)

- [/Oi (Generuj funkcje wewnętrzne)](oi-generate-intrinsic-functions.md)

- [/OT (Preferuj szybki kod)](os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (pominięcie wskaźnika ramki)](oy-frame-pointer-omission.md)

**Ox** jest wzajemnie wykluczających się od:

- [/ O1 (minimalizacja rozmiaru)](o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (Maksymalizuj szybkość)](o1-o2-minimize-size-maximize-speed.md)

- [/Od (Wyłącz (Debuguj))](od-disable-debug.md)

Można anulować odchylenie kierunku szybkości **ox** w przypadku określenia — opcja kompilatora **/Oxs**, które łączy w sobie **ox** — opcja kompilatora przy użyciu  [ /OS (Preferuj mały Kod)](os-ot-favor-small-code-favor-fast-code.md). Opcje połączone Preferuj mniejszego rozmiaru kodu.  **/Oxs** opcji jest dokładnie taka sama, jak określenie **ox** **/Os** po opcje są wyświetlane w tej kolejności.

Aby zastosować wszystkie dostępne optymalizacje poziomie plików dla kompilacji wydania, firma Microsoft zaleca, należy określić [/O2 (Maksymalizuj szybkość)](o1-o2-minimize-size-maximize-speed.md) zamiast **ox**, i [/O1 (Minimalizuj rozmiar)](o1-o2-minimize-size-maximize-speed.md) zamiast tego z **/Oxs**. Jeszcze więcej optymalizacji w wersji kompilacji, należy również rozważyć [/GL (Optymalizacja Całoprogramowa)](gl-whole-program-optimization.md) — opcja kompilatora i [opcję/LTCG (Generowanie kodu Link-time)](ltcg-link-time-code-generation.md) — opcja konsolidatora.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. W obszarze **właściwości konfiguracji**, otwórz **C/C++** , a następnie wybierz **optymalizacji** stronę właściwości.

1. Modyfikowanie **optymalizacji** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Zobacz także

[/O Opcje (Optymalizuj kod)](o-options-optimize-code.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
