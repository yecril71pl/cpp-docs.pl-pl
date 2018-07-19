---
title: IUnknown | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, base interface
- IUnknown interface
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d832d2978bf9db82b290d77b236fea1c9bcada58
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953045"
---
# <a name="iunknown"></a>IUnknown
[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) jest interfejsem podstawowy każdego interfejsu COM.  Ten interfejs definiuje trzy metody: [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521), [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379), i [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317). [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) pozwala użytkownikowi interfejsu poprosić obiekt o wskaźnik do innego z jego interfejsów. [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) i [wersji](http://msdn.microsoft.com/library/windows/desktop/ms682317) zaimplementować na interfejsie zliczanie odwołań.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do modelu COM](../atl/introduction-to-com.md)   
 [IUnknown i dziedziczenia interfejsu](http://msdn.microsoft.com/library/windows/desktop/ms692713)

