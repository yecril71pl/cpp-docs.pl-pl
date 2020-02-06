---
title: /Qspectre-load-cf
description: Opisuje opcję Microsoft C/C++ COMPILER (MSVC)/Qspectre-load-cf.
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load-cf
no-loc:
- Qspectre-load-cf
ms.openlocfilehash: c32b843df517cb6fbe662fba0b592cbf745f1764
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035523"
---
# /Qspectre-load-cf

Określa generowanie kompilatora serializacji instrukcji dla każdej instrukcji przepływu sterowania, która zawiera obciążenie. Ta opcja wykonuje podzestaw środków zaradczych wykonanych przez opcję [/Qspectre-Load](qspectre-load.md) .

## <a name="syntax"></a>Składnia

> **/Qspectre-load-cf**

## <a name="remarks"></a>Uwagi

**/Qspectre-load-cf** powoduje, że kompilator wykrywa `JMP`, `RET`i `CALL` instrukcji przepływu sterowania, które ładują z pamięci, i wstawia instrukcje serializacji po załadowaniu. Jeśli to możliwe, te instrukcje są podzielone na obciążenie i transfer przepływu sterowania. Po obciążeniu następuje `LFENCE`, aby upewnić się, że obciążenie jest chronione. Istnieją przypadki, w których kompilator nie może podzielić instrukcji, takich jak instrukcje `JMP`, więc używa alternatywnej techniki zaradczej. Na przykład kompilator ogranicza `jmp [rax]` przez dodanie instrukcji w celu załadowania obiektu docelowego przed usunięciem, jak pokazano poniżej:

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

Ponieważ **/Qspectre-load-cf** przerywa spekulacje wszystkich obciążeń w instrukcjach sterowania przepływem, wpływ na wydajność jest wysoki. Środki zaradcze nie są odpowiednie wszędzie. Jeśli istnieją kluczowe bloki wydajności kodu, które nie wymagają ochrony, możesz wyłączyć te środki zaradcze przy użyciu `__declspec(spectre(nomitigation))`.

Opcja **/Qspectre-load-cf** jest domyślnie wyłączona i obsługuje wszystkie poziomy optymalizacji.

Opcja **/Qspectre-load-cf** jest dostępna w programie Visual Studio 2019 w wersji 16,5 lub nowszej. Ta opcja jest dostępna tylko w kompilatorach przeznaczonych dla procesorów x86 i x64. Nie jest on dostępny w kompilatorach przeznaczonych dla procesorów ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

2. Wybierz **Właściwości konfiguracji** > stronie właściwości **generowanie kodu** **C++ C/**  > .

3. Wybierz nową wartość właściwości **ograniczenia Spectre** . Wybierz **przycisk OK** , aby zastosować zmianę.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q opcji (operacje na niskim poziomie)](q-options-low-level-operations.md)\
[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
