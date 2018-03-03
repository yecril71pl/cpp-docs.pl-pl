---
title: "Konwersje przypisań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- conversions, assignment
- assignment conversions
ms.assetid: 4ee01013-de32-4aae-b12e-0051d0cde927
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94087d5e07765b1052404a4c3e51f37db2a31e3d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="assignment-conversions"></a>Konwersje przypisań
W operacjach przypisania typ wartości jest przypisany jest konwertowana na typ zmiennej, która odbiera przypisania. C umożliwia konwersje przez przypisanie między typów całkowitych i zmiennoprzecinkowych, nawet wtedy, gdy informacje są tracone w konwersji. Metodę konwersji zależy od typów objętego przypisania, zgodnie z opisem w [popularne konwersje arytmetyczne](../c-language/usual-arithmetic-conversions.md) i w następujących sekcjach:  
  
-   [Konwersje z podpisanych typów całkowitych](../c-language/conversions-from-signed-integral-types.md)  
  
-   [Konwersje z niepodpisanych typów całkowitych](../c-language/conversions-from-unsigned-integral-types.md)  
  
-   [Konwersje z typów zmiennoprzecinkowych](../c-language/conversions-from-floating-point-types.md)  
  
-   [Konwersje do i z typów wskaźnika](../c-language/conversions-to-and-from-pointer-types.md)  
  
-   [Konwersje z innych typów](../c-language/conversions-from-other-types.md)  
  
 Kwalifikatory typu nie mają wpływu na istoty konwersji, mimo że **const** l wartości nie można używać po lewej stronie przypisania.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwersje typów](../c-language/type-conversions-c.md)