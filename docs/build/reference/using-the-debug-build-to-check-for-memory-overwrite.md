---
title: "Korzystanie z kompilacji debugowania do sprawdzania nadpisywania pamięci | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7b8fc223a1e4e1162ce99bb3275152c49828aa99
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Korzystanie z kompilacji debugowania do sprawdzania nadpisywania pamięci
Aby korzystać z kompilacji debugowania do sprawdzania nadpisywania pamięci, należy najpierw ponownie skompiluj projekt do debugowania. Następnie przejdź do początku części aplikacji `InitInstance` funkcji i Dodaj następujący wiersz:  
  
```  
afxMemDF |= checkAlwaysMemDF;  
```  
  
 Debugowanie alokatora umieszcza bajtów guard wokół wszystkich alokacji pamięci. Jednak te zabezpieczenia bajtów nie wykonuj żadnych dobrej, należy sprawdzić, czy zostały zmienione (co oznaczałoby Zastąp pamięci). W przeciwnym razie po prostu zapewnia buforu, który może być w rzeczywistości pozwalają na pobranie nieobecności z Zastąp pamięci.  
  
 Przez włączenie `checkAlwaysMemDF`, zostanie wymuszone MFC do wywoływania `AfxCheckMemory` funkcji zawsze wywołanie **nowe** lub **usunąć** staje się. Jeśli został wykryty zastępowania pamięci, wygeneruje komunikat śledzenia, która wygląda podobnie do następującego:  
  
```  
Damage Occurred! Block=0x5533  
```  
  
 Jeśli zostanie wyświetlony jeden z tych wiadomości, należy do wykonania kroków opisanych swój kod, aby określić, w którym wystąpiło uszkodzenie. Aby wyizolować dokładniej, gdzie Zastąp pamięci wystąpił, należy wybrać jawnego wywołania `AfxCheckMemory` samodzielnie. Na przykład:  
  
```  
ASSERT(AfxCheckMemory());  
    DoABunchOfStuff();  
    ASSERT(AfxCheckMemory());  
```  
  
 Jeśli pierwszy ASSERT zakończy się pomyślnie, a drugi ulegnie awarii, oznacza to, że Zastąp pamięci musi wystąpiły w funkcji między dwoma wywołania.  
  
 W zależności od charakteru aplikacji może się okazać, że `afxMemDF` powoduje, że program do uruchomienia zbyt wolno, aby przetestować nawet. `afxMemDF` Powoduje, że zmienna `AfxCheckMemory` można wywołać dla każdego wywołania do nowych i usuwania. W takim przypadku należy punktowy wywołania do `AfxCheckMemory`(), jak pokazano powyżej i spróbuj do izolowania pamięć zastąpić w ten sposób.  
  
## <a name="see-also"></a>Zobacz też  
 [Naprawianie problemów kompilacji wydania](../../build/reference/fixing-release-build-problems.md)