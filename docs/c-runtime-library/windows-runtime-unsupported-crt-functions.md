---
title: "Środowisko wykonawcze systemu Windows nieobsługiwane funkcje CRT | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- unsupported CRT functions, Windows Runtime
- Windows Runtime, unsupported CRT functions
ms.assetid: bb8386d6-0ef8-460c-88d8-addff009b6f1
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f9fb74dbc28235f211f24d64ef125f2cccdafc7d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="windows-runtime-unsupported-crt-functions"></a>Nieobsługiwane funkcje CRT środowiska uruchomieniowego systemu Windows
Nie można używać wielu interfejsów API czasu wykonywania (CRT) C w [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] aplikacje, które są wykonywane w środowisku wykonawczym systemu Windows. Te aplikacje są tworzone za pomocą flagi kompilatora /ZW. Aby uzyskać listę nieobsługiwane funkcje CRT, zobacz [funkcje CRT, nie są obsługiwane przez /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
 Wszystkie interfejsy API CRT opisanym w [alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md) sekcji dokumentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)   
 [Alfabetyczne odwołanie funkcji](../c-runtime-library/reference/crt-alphabetical-function-reference.md)