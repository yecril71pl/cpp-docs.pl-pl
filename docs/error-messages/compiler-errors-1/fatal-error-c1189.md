---
title: "Błąd krytyczny C1189 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1189
dev_langs: C++
helpviewer_keywords: C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e8d3c9ff44a436688accfe267141390d23c0eb5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1189"></a>Błąd krytyczny C1189
\#Błąd: komunikat o błędzie podanych przez użytkownika.  
  
 C1189 jest generowany przez `#error` dyrektywy. Projektanta, który kodów dyrektywa określa tekst komunikatu o błędzie. Aby uzyskać więcej informacji, zobacz [#error — dyrektywa (C/C++)](../../preprocessor/hash-error-directive-c-cpp.md).  
  
 Poniższy przykład generuje C1189. W przykładzie dewelopera wystawia niestandardowy komunikat o błędzie, ponieważ `_WIN32` nie zdefiniowano identyfikatora:  
  
```  
// C1189.cpp  
#undef _WIN32  
#if !defined(_WIN32)  
#error _WIN32 must be defined   // C1189  
#endif  
```  
  
 Ten błąd może być również wyświetlany, jeśli tworzysz Projekt ATL za pomocą **/ robust** MIDL — opcja kompilatora. Użyj **/ robust** przełącznika do tworzenia tylko [!INCLUDE[win2kfamily](../../c-runtime-library/includes/win2kfamily_md.md)] i nowszych wersjach systemu Windows. Aby rozwiązać ten problem, należy użyć jednej z następujących procedur:  
  
-   Zmień ten wiersz w pliku dlldatax.c:  
  
```  
#define _WIN32_WINNT 0x0400   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
 na:  
  
```  
#define _WIN32_WINNT 0x0500   // for WinNT 4.0 or Windows 95 with DCOM  
```  
  
-   Użyj **zaawansowane** stronę właściwości w **MIDL** folder strony właściwości do usunięcia **/ robust** przełącznik, a następnie określ **/no_robust** przełącznik. Aby uzyskać więcej informacji, zobacz [strony właściwości MIDL: zaawansowane](../../ide/midl-property-pages-advanced.md).  
  
## <a name="see-also"></a>Zobacz też  
 [#define — dyrektywa (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)