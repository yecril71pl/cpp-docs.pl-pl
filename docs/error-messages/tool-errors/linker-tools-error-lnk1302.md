---
title: "Błąd narzędzi konsolidatora LNK1302 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1302
dev_langs: C++
helpviewer_keywords: LNK1302
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7154cc538e17050eafec251729cf26a3cd62e573
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1302"></a>Błąd narzędzi konsolidatora LNK1302
obsługiwana jest tylko połączenie bezpiecznych modułów .netmodule; Nie można skonsolidować modułu .netmodule pliku  
  
 Modułu .netmodule (skompilowane z **/LN**) została przekazana do konsolidatora użytkownika próba wywołania Konsolidacja MSIL.  Moduł C++ jest prawidłowa dla Konsolidacja MSIL, jeśli jest skompilowana przy użyciu **/CLR: Safe**.  
  
 Aby rozwiązać ten problem, skompiluj z **/CLR: Safe** do włączenia Konsolidacja MSIL lub Przekaż **/CLR** lub **/CLR: pure** pliku obj. do konsolidatora zamiast modułu.  
  
 Aby uzyskać więcej informacji, zobacz  
  
-   [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md)  
  
-   [modułu .netmodule pliki jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md)