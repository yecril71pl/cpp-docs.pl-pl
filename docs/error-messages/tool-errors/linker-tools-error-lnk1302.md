---
title: Błąd narzędzi konsolidatora LNK1302 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1302
dev_langs:
- C++
helpviewer_keywords:
- LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6aa84a411f91303c84acb44e2e6c0ab3d975e19f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1302"></a>Błąd narzędzi konsolidatora LNK1302
obsługiwana jest tylko połączenie bezpiecznych modułów .netmodule; Nie można skonsolidować modułu .netmodule pliku  
  
 Modułu .netmodule (skompilowane z **/LN**) została przekazana do konsolidatora użytkownika próba wywołania Konsolidacja MSIL.  Moduł C++ jest prawidłowa dla Konsolidacja MSIL, jeśli jest skompilowana przy użyciu **/CLR: Safe**.  
  
 Aby rozwiązać ten problem, skompiluj z **/CLR: Safe** do włączenia Konsolidacja MSIL lub Przekaż **/CLR** lub **/CLR: pure** pliku obj. do konsolidatora zamiast modułu.  
  
 Aby uzyskać więcej informacji, zobacz artykuł  
  
-   [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md)  
  
-   [Pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md)