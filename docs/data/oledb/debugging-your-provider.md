---
title: Debugowanie dostawcy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c6258ddd3fd4317c608cb20486c364918fb5c73a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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