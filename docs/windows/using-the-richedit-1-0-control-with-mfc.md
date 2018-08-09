---
title: Używanie formantu RichEdit 1.0 z MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a00642c1aefdce57c37723ef4daf23381cee3c13
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39650751"
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Używanie formantu RichEdit 1.0 z MFC
Aby użyć kontrolki RichEdit, najpierw musisz wywołać [afxinitrichedit2 —](../mfc/reference/application-information-and-management.md#afxinitrichedit2) można załadować kontrolki 2.0 RichEdit (RICHED20. Biblioteka DLL), lub zadzwoń [afxinitrichedit —](../mfc/reference/application-information-and-management.md#afxinitrichedit) załadować starszej kontrolki RichEdit 1.0 (RICHED32. BIBLIOTEKA DLL).  
  
 Może używać bieżącego [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) klasy za pomocą starszej kontrolki RichEdit 1.0, ale `CRichEditCtrl` jest przeznaczona wyłącznie do obsługi formantu RichEdit w wersji 2.0. Większość metod będzie działać, ponieważ RichEdit 1.0 i RichEdit 2.0 są bardzo podobne, jednak należy pamiętać, że istnieją pewne różnice między kontrolkami 1.0 i 2.0, więc niektóre metody mogą nie działać prawidłowo lub nie działać w ogóle.  
  
## <a name="requirements"></a>Wymagania  
 MFC  
  
## <a name="see-also"></a>Zobacz też  
 [Rozwiązywanie problemów z edytorem okien dialogowych](../windows/troubleshooting-the-dialog-editor.md)   
 [Edytor okien dialogowych](../windows/dialog-editor.md)