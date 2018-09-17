---
title: -DEBUGTYPE (opcje informacji debugowania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /debugtype
dev_langs:
- C++
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98edb5945c2cf01d90cd5dae1a750c0fdd37757f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723284"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (opcje informacji debugowania)

Opcja /DEBUGTYPE Określa typy informacji o debugowaniu wygenerowanych za pomocą opcji/Debug.

```
/DEBUGTYPE:[CV | PDATA | FIXUP]
```

## <a name="arguments"></a>Argumenty

**CV**<br/>
Informuje konsolidator, aby wyemitować informacji debugowania dla symboli, numery wierszy i inne informacje o kompilacji z obiektu w pliku PDB. Domyślnie ta opcja jest włączona po **/DEBUG** jest określona i **/DEBUGTYPE** nie zostanie określony.

**PDATA**<br/>
Informuje konsolidator, aby dodać wpisy .pdata i .xdata do informacji o strumieniu debugowania w pliku PDB. Domyślnie ta opcja jest włączona po zarówno **/DEBUG** i **Driver/Driver** są określone opcje. Jeśli **/DEBUGTYPE:PDATA** jest określony przez siebie, konsolidator automatycznie uwzględnia symboli w pliku PDB debugowania. Jeśli **/DEBUGTYPE:PDATA, naprawy** jest określona, konsolidator nie zawiera symboli w pliku PDB debugowania.

**NAPRAWY**<br/>
Informuje konsolidator, aby dodać wpisy tabeli relokacji do informacji o strumieniu debugowania w pliku PDB. Domyślnie ta opcja jest włączona po zarówno **/DEBUG** i **/PROFILE** są określone opcje. Jeśli **/DEBUGTYPE:FIXUP** lub **/DEBUGTYPE:FIXUP, PDATA** jest określona, konsolidator nie zawiera symboli w pliku PDB debugowania.

Argumenty **/DEBUGTYPE** mogą być łączone w dowolnej kolejności, oddzielając je przecinkami. **/DEBUGTYPE** opcję i jej argumenty nie są z uwzględnieniem wielkości liter.

## <a name="remarks"></a>Uwagi

Użyj **/DEBUGTYPE** opcję włączenia relokacji danych lub .pdata i .xdata informacje o nagłówku tabeli w strumieniu debugowania. Powoduje to programowi łączącemu uwzględnienie informacji na temat kodu w trybie użytkownika, który jest widoczny w debugerze jądra podczas dzielenia kodu trybu jądra. Aby udostępnić symbole debugowania w po **naprawy** jest określony, obejmują **CV** argumentu.

Aby debugować kod w trybie użytkownika, który jest typowy dla aplikacji, **/DEBUGTYPE** opcja nie jest potrzebna. Domyślnie dane wyjściowe przełączniki kompilatora, które określają, debugowanie ([/z7, / zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)) emisji, wszystkie informacje wymagane przez program Visual Studio debugera. Użyj **/DEBUGTYPE:PDATA** lub **Utwórz PDATA, naprawy** do debugowania kodu, który łączy składniki trybu jądra i trybu użytkownika, takie jak konfiguracji aplikacji dla sterownika urządzenia. Aby uzyskać więcej informacji na temat debugery trybu jądra, zobacz [debugowania narzędzi Tools for Windows (WinDbg KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)

## <a name="see-also"></a>Zobacz też

[/ DEBUG (generowanie informacji o debugowaniu)](../../build/reference/debug-generate-debug-info.md)
[Driver/Driver (sterownik trybu jądra Windows NT)](../../build/reference/driver-windows-nt-kernel-mode-driver.md)
[/profile (Profiler narzędzi wydajności)](../../build/reference/profile-performance-tools-profiler.md) 
 [Narzędzia do debugowania dla Windows (WinDbg KD, CDB, NTSD)](/windows-hardware/drivers/debugger/index)