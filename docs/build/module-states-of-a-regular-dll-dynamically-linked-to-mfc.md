---
title: Stany modułu zwykłej biblioteki MFC DLL połączone dynamicznie z MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- module states [C++]
- MFC DLLs [C++], regular MFC DLLs
- module states [C++], regular MFC DLLs dynamically linked to
- DLLs [C++], module states
ms.assetid: b4493e79-d25e-4b7f-a565-60de5b32c723
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d15f533473ebe90d6d105ddeb57dcdcddd90e87b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="module-states-of-a-regular-mfc-dll-dynamically-linked-to-mfc"></a>Stany modułu zwykłej biblioteki MFC DLL połączone dynamicznie z MFC
Dynamicznie połączyć zwykły biblioteki MFC DLL biblioteki MFC DLL możliwości niektóre konfiguracje, które są bardzo skomplikowane. Na przykład regularną bibliotekę DLL MFC i plik wykonywalny, który używa zarówno dynamicznie połączyć do biblioteki MFC DLL i wszystkie biblioteki DLL rozszerzeń MFC.  
  
 Ta konfiguracja stanowi problem w odniesieniu do danych globalnych MFC, takie jak wskaźnik do bieżącego `CWinApp` map obiekt i dojścia.  
  
 Przed MFC w wersji 4.0 to dane globalne znajdowały się w bibliotece MFC DLL się i został udostępniony przez wszystkie moduły w procesie. Ponieważ każdy proces, za pomocą biblioteki DLL Win32 uzyskuje on osobną kopię danych DLL, ten schemat podać prosty sposób śledzenia danych dla procesu. Ponadto ponieważ AFXDLL model założyć, że może istnieć tylko jeden `CWinApp` obiekt i tylko jeden zestaw obsługi mapy w procesie, te elementy można można śledzić w bibliotece MFC DLL sam.  
  
 Ale umożliwia dynamiczne łącze do biblioteki MFC DLL regularną bibliotekę DLL MFC, jest teraz możliwe co najmniej dwóch `CWinApp` obiektów w procesie —, a także co najmniej dwóch zestawów dojścia mapy. Jak MFC zachować informacje o te, które powinny używać?  
  
 Rozwiązanie to podać własną kopię tych informacji globalny stan poszczególnych modułów (aplikacji lub regularnych bibliotek DLL MFC). W związku z tym wywołaniu **afxgetapp —** w zwykłej biblioteki MFC DLL zwraca wskaźnik do `CWinApp` obiektu w bibliotece DLL, a nie podano w pliku wykonywalnego. -Module kopii danych globalnych MFC nosi nazwę stanu modułu i jest opisany w [58 Uwaga techniczna MFC](../mfc/tn058-mfc-module-state-implementation.md).  
  
 Procedurę okna wspólnych MFC automatycznie zmienia stan prawidłowy moduł, dzięki czemu nie trzeba martwić w dowolnej obsługi komunikatów w regularnych bibliotek DLL MFC. Jednak gdy wywołuje pliku wykonywalnego do regularne biblioteki DLL MFC, musisz jawnie Ustaw bieżący stan modułu dla biblioteki DLL. Aby to zrobić, użyj **afx_manage_state —** makra w każdej funkcji wyeksportowane z biblioteki DLL. Można to zrobić, dodając następujący wiersz kodu na początku funkcji wyeksportowanych z biblioteki DLL:  
  
```  
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))  
```  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Zarządzanie danymi stanu modułów MFC](../mfc/managing-the-state-data-of-mfc-modules.md)  
  
-   [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Biblioteki DLL rozszerzeń MFC](../build/extension-dlls-overview.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)