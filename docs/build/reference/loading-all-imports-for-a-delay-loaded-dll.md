---
title: Importy Załaduj wszystko dla bibliotek DLL załadowanych z opóźnieniem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8afa206e62702407d9974802f9422c8597d772ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Importy Załaduj wszystko dla bibliotek DLL załadowanych z opóźnieniem
**__HrLoadAllImportsForDll** funkcji, która jest zdefiniowana w delayhlp.cpp, informuje konsolidator, aby załadować wszystkie Importy z biblioteki DLL, która została określona z [/delayload](../../build/reference/delayload-delay-load-import.md) — opcja konsolidatora.  
  
 Importy Załaduj wszystko Umożliwia wstrzymanie obsługi błędów w jednym miejscu w kodzie i nie trzeba używać obsługi wokół rzeczywistego wywołania do operacji importu wyjątków. Pozwala również uniknąć sytuacji, gdy aplikacja nie częściowo proces wyniku kodu pomocnika można załadować do importu.  
  
 Wywoływanie **__HrLoadAllImportsForDll** nie zmienia zachowanie punkty zaczepienia i błąd obsługi; zobacz [Obsługa błędów oraz powiadomienia](../../build/reference/error-handling-and-notification.md) Aby uzyskać więcej informacji.  
  
 Nazwa biblioteki DLL przekazany do **__HrLoadAllImportsForDll** jest porównywany z nazwą przechowywany w samej biblioteki DLL i jest rozróżniana wielkość liter.  
  
 Poniższy przykład przedstawia sposób wywołania **__HrLoadAllImportsForDll**:  
  
```  
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {  
   printf ( "failed on snap load, exiting\n" );  
   exit(2);  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)