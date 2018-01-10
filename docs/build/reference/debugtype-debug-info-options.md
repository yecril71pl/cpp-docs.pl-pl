---
title: -DEBUGTYPE (opcje informacji debugowania) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /debugtype
dev_langs: C++
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7c069caca9831b841c3cb4be347331b58f538ba6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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