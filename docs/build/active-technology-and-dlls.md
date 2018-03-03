---
title: Technologia Active i biblioteki dll | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- in-process server DLLs
- Automation [C++], DLLs
- DLLs [C++], Active Technology
- Active technology [C++]
- MFC DLLs [C++], Active Technology
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44dcc58aed4025af2e3e2177e978633c13f0ef20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="active-technology-and-dlls"></a>Technologia Active i biblioteki DLL
Technologia Active umożliwia serwerom obiektu do zaimplementowania całości wewnątrz biblioteki DLL. Ten typ serwera nosi nazwę serwera w procesie. MFC nie całkowicie obsługuje serwery wewnątrzprocesowe dla wszystkich funkcji edycja wizualna głównie, ponieważ jest to technologia Active nie umożliwiają serwerowi przyłączanie się do pętli komunikatów głównego kontenera. MFC wymaga dostępu do aplikacji kontenera pętli komunikatów do obsługi klawisze skrótów i przetwarzania w czasie bezczynności.  
  
 Jeśli piszesz serwera automatyzacji i serwer nie ma interfejsu użytkownika, możesz wprowadzić serwer server wewnątrzprocesowe i całkowicie umieszcza je do biblioteki DLL.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Serwery automatyzacji](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)