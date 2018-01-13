---
title: Kontener Class::swap | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 09229429c64e895a722d52d203f0259cf69e6d24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="container-classswap"></a>Kontener Class::swap
> [!NOTE]
>  Ten temat dotyczy w dokumentacji Visual C++ prawidłowo przykład kontenerów używanych w standardowej bibliotece C++. Aby uzyskać więcej informacji, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).  
  
Zamienia kontrolowanej sekwencji między  **\*to** i jej argument.  
  
## <a name="syntax"></a>Składnia  
  
```  
void swap(Container& right);
```  
  
## <a name="remarks"></a>Uwagi  
Jeśli  **\*this.get\_alokatora ==** _prawo_**.get_allocator**, robi zamiana w czasie stałej. W przeciwnym razie wykonuje szereg element zadania i wywołania konstruktora proporcjonalny do liczby elementów w dwóch kontrolowanej sekwencji.  
  
## <a name="see-also"></a>Zobacz też  
[Sample Container, klasa](../standard-library/sample-container-class.md)
