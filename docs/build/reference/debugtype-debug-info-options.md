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
ms.openlocfilehash: 66868f7648d20b890f3c1e8c40802d77e3af4544
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (opcje informacji debugowania)
Opcja /DEBUGTYPE Określa typy informacji dotyczących debugowania generowanych przez opcję/Debug.  
  
```  
/DEBUGTYPE:[CV | PDATA | FIXUP]  
```  
  
## <a name="arguments"></a>Argumenty  
 CV  
 Informuje konsolidator, aby wyemitować informacji debugowania dla symboli, numery wierszy i inne informacje o kompilacji z obiektu w pliku PDB. Domyślnie ta opcja jest włączona po **/DEBUG** określono i **/DEBUGTYPE** nie jest określona.  
  
 PDATA  
 Informuje konsolidator, aby dodać wpisy .pdata i .xdata do strumienia informacje o debugowaniu w pliku PDB. Domyślnie ta opcja jest włączona po zarówno **/DEBUG** i **/Driver** są określone opcje. Jeśli **/DEBUGTYPE:PDATA** jest określona, konsolidator automatycznie uwzględnia debugowania symboli w pliku PDB. Jeśli **/DEBUGTYPE:PDATA, naprawy** jest określona, konsolidator nie zawiera symboli w pliku PDB debugowania.  
  
 NAPRAWY  
 Informuje konsolidator, aby dodać wpisów tabeli relokacji do strumienia informacje o debugowaniu w pliku PDB. Domyślnie ta opcja jest włączona po zarówno **/DEBUG** i **/PROFILE** są określone opcje. Jeśli **/DEBUGTYPE:FIXUP** lub **/DEBUGTYPE:FIXUP, PDATA** jest określona, konsolidator nie zawiera symboli w pliku PDB debugowania.  
  
 Argumenty **/DEBUGTYPE** mogą być łączone w dowolnej kolejności, oddzielając je przecinkami. **/DEBUGTYPE** opcji i jej argumenty nie są z uwzględnieniem wielkości liter.  
  
## <a name="remarks"></a>Uwagi  
 Użyj **/DEBUGTYPE** opcję włączenia relokacji danych lub .pdata i .xdata informacje o nagłówku tabeli w strumieniu debugowania. Powoduje to, że konsolidator zawierają informacje o kodu w trybie użytkownika, które są widoczne w debuger jądra w przypadku dzielenia kodu w trybie jądra. Aby udostępnić symbole debugowania w po **naprawy** jest określony, obejmują **CV** argumentu.  
  
 Do debugowania kodu w trybie użytkownika, co jest typowe dla aplikacji, **/DEBUGTYPE** opcja nie jest potrzebna. Domyślnie dane wyjściowe przełączniki kompilatora, które określają debugowania ([/z7, / zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)) Emituj wszystkie informacje wymagane przez program Visual Studio debugera. Użyj **/DEBUGTYPE:PDATA** lub **/DEBUGTYPE:CV PDATA, naprawy** do debugowania kodu, który łączy trybu użytkownika i w trybie jądra składniki, takie jak aplikacja konfiguracji sterownika urządzenia. Aby uzyskać więcej informacji na temat debugery trybu jądra, zobacz [narzędzi debugowania dla systemu Windows (WinDbg, KD, CDB, NTSD)](http://go.microsoft.com/fwlink/p?LinkID=285651)  
  
## <a name="see-also"></a>Zobacz też  
 [/ DEBUG (generowanie informacji o debugowaniu)](../../build/reference/debug-generate-debug-info.md)   
 [/ DRIVER (sterownik trybu jądra systemu Windows NT)](../../build/reference/driver-windows-nt-kernel-mode-driver.md)   
 [/ PROFILE (Profiler narzędzi wydajności)](../../build/reference/profile-performance-tools-profiler.md)   
 [Narzędzia debugowania dla systemu Windows (WinDbg, KD, CDB, NTSD)](http://go.microsoft.com/fwlink/p?LinkID=285651)