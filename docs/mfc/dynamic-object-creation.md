---
title: "Dynamiczne tworzenie obiektów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 755cbf614966ad6faedbe8db9bbf11ac88c63328
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dynamic-object-creation"></a>Dynamiczne tworzenie obiektów
W tym artykule opisano sposób tworzenia obiektu dynamicznie w czasie wykonywania. Procedura wykorzystuje informacje o klasie czasu wykonywania, zgodnie z opisem w artykule [podczas uzyskiwania dostępu do środowiska wykonawczego informacje o klasie](../mfc/accessing-run-time-class-information.md).  
  
#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>Można dynamicznie utworzyć obiekt na podstawie jego klasa czasu wykonywania  
  
1.  Poniższy kod umożliwia dynamiczne tworzenie obiektów przy użyciu `CreateObject` funkcji `CRuntimeClass`. Należy pamiętać, że w przypadku awarii, `CreateObject` zwraca **NULL** zamiast wywoływanie wyjątek:  
  
     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie obiektu CObject](../mfc/using-cobject.md)

