---
title: "Ograniczenia bibliotek DLL ładowanych z opóźnieniem | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1f952de894cad02638a7f304590562f1846bc003
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="constraints-of-delay-loading-dlls"></a>Ograniczenia bibliotek DLL ładowanych z opóźnieniem
Istnieją ograniczenia dotyczące ładowania opóźnienia importowania.  
  
-   Importy danych nie może być obsługiwana. Obejście tego problemu jest jawnie importu danych samodzielnie przy użyciu `LoadLibrary` (lub `GetModuleHandle` po określeniu pomocnika opóźnionego ładowania została załadowana biblioteka DLL) i `GetProcAddress`.  
  
-   Opóźnienie załadowanie Kernel32.dll nie jest obsługiwane. Ta biblioteka DLL jest niezbędne do procedury pomocnika opóźnionego ładowania do wykonania opóźnienia ładowania.  
  
-   [Powiązanie](../../build/reference/binding-imports.md) wpisu punktów, które są przesyłane dalej nie jest obsługiwane.  
  
-   Opóźnienia ładowania biblioteki DLL nie może spowodować takie samo zachowanie procesu, jeśli inicjowanie na proces, które występują w punkcie wejścia biblioteki DLL załadowanych z opóźnieniem. Innych przypadkach obejmują zadeklarowane za pomocą statycznego TLS (lokalny magazyn wątków), [__declspec(thread)](../../cpp/thread.md), która nie jest obsługiwana podczas ładowania biblioteki DLL za pośrednictwem `LoadLibrary`. Dynamiczne TLS, używając `TlsAlloc`, `TlsFree`, `TlsGetValue`, i `TlsSetValue`, nadal można używać w statyczny lub ładowanych z opóźnieniem biblioteki dll.  
  
-   Wskaźniki funkcji statycznej (globalne) powinien należy ponownie zainicjować funkcji importowanych po pierwszym wywołaniu funkcji. Jest to spowodowane thunk wskaże pierwsze użycie wskaźnika funkcji.  
  
-   Nie istnieje sposób obecnie w celu opóźnienia ładowania tylko określonych procedur z biblioteki DLL podczas przy użyciu mechanizmu normalne importu.  
  
-   Niestandardowe konwencji wywoływania (np. przy użyciu kodów stanu na x86 architektury) nie są obsługiwane. Ponadto rejestrów zmiennoprzecinkowych nie są zapisywane na dowolnej platformie. Użycie procedury niestandardowego elementu pomocniczego lub procedury haku z typów zmiennoprzecinkowych, należy całkowicie zapisywanie i przywracanie stanu zmiennoprzecinkowych na maszynach z rejestrem konwencje z parametrami zmiennoprzecinkowe wywoływania. Należy rozważnie Opóźniaj ładowanie bibliotek DLL CRT można wywołać funkcji CRT, które przyjmują zmiennoprzecinkowe parametrów na stosie procesora danych numerycznych (NPR) w funkcji pomocy.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa konsolidatora dla bibliotek DLL załadowanych z opóźnieniem](../../build/reference/linker-support-for-delay-loaded-dlls.md)   
 [Funkcja LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175.aspx)   
 [Funkcja GetModuleHandle](http://msdn.microsoft.com/library/windows/desktop/ms683199.aspx)   
 [GetProcAddress — funkcja](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)   
 [Funkcja TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801.aspx)   
 [Funkcja TlsFree](http://msdn.microsoft.com/library/windows/desktop/ms686804.aspx)   
 [Funkcja TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812.aspx)   
 [Funkcja TlsSetValue](http://msdn.microsoft.com/library/windows/desktop/ms686818.aspx)