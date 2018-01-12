---
title: Debugowanie dostawcy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6cfcb90daaf23a5fd8e248d43b920340e38d8057
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-your-provider"></a>Debugowanie dostawcy
Istnieją dwa sposoby debugowania dostawcy:  
  
-   Ponieważ w procesie tworzenia dostawców, można utworzyć kodu konsumentów zwykle za pomocą szablony konsumentów OLE DB i Wkrocz do dostawcy.  
  
-   Można użyć narzędzia ITEST, który jest dostarczany z programem Visual C++.  
  
### <a name="to-use-the-itest-utility"></a>Aby korzystać z narzędzia ITEST  
  
1.  Otwórz projekt dostawcy.  
  
2.  Na **projekty** menu, kliknij przycisk **ustawienia**.  
  
3.  W **strony właściwości** okno dialogowe, kliknij przycisk **debugowania** kartę.  
  
4.  W **plik wykonywalny dla sesji debugowania** wybierz ITEST aplikacji.  
  
5.  Ustaw punkty przerwania, a następnie debugowania w zwykły sposób.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z szablonami dostawców OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)