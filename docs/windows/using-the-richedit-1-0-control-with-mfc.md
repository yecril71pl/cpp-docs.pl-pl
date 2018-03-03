---
title: "Używanie formantu RichEdit 1.0 z MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d6c5393b006602084a50d18c8cfe76d59d2d6ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Używanie formantu RichEdit 1.0 z MFC
Aby korzystać z formantu RichEdit, należy najpierw wywołać [afxinitrichedit2 —](../mfc/reference/application-information-and-management.md#afxinitrichedit2) załadować formantu RichEdit 2.0 (RICHED20. Biblioteki DLL), lub zadzwoń [afxinitrichedit —](../mfc/reference/application-information-and-management.md#afxinitrichedit) załadować starsze formantu RichEdit 1.0 (RICHED32. BIBLIOTEKI DLL).  
  
 Można użyć bieżącej [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) klasy z formantu RichEdit 1.0 starsze, ale **CRichEditCtrl** jest przeznaczona wyłącznie do obsługi formantu RichEdit 2.0. Ponieważ RichEdit 1.0 i RichEdit 2.0 są bardzo podobne, będzie działać większości metod; należy jednak pamiętać, że istnieją pewne różnice między formantami 1.0 i 2.0, więc niektóre metody może działać prawidłowo lub nie działać w ogóle.  
  
## <a name="requirements"></a>Wymagania  
 MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z edytora okien dialogowych](../windows/troubleshooting-the-dialog-editor.md)   
 [Edytor okien dialogowych](../windows/dialog-editor.md)

