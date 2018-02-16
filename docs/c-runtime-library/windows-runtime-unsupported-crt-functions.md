---
title: "Środowisko wykonawcze systemu Windows nieobsługiwane funkcje CRT | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- unsupported CRT functions, Windows Runtime
- Windows Runtime, unsupported CRT functions
ms.assetid: bb8386d6-0ef8-460c-88d8-addff009b6f1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a2f6b06b45da502e3eba898f2907042afeca65c2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="windows-runtime-unsupported-crt-functions"></a>Nieobsługiwane funkcje CRT środowiska uruchomieniowego systemu Windows
Nie można używać wielu C-run-time (CRT) interfejsów API w aplikacjach systemu Windows platformy Uniwersalnej, które są wykonywane w środowisku wykonawczym systemu Windows. Te aplikacje są tworzone za pomocą flagi kompilatora /ZW. Aby uzyskać listę nieobsługiwane funkcje CRT, zobacz [funkcje CRT, nie są obsługiwane przez /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
 Wszystkie interfejsy API CRT opisanym w [alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md) sekcji dokumentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)   
 [Alfabetyczne zestawienie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)