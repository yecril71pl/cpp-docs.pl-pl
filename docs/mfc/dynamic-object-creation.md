---
title: Dynamiczne tworzenie obiektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- object creation [MFC], dynamically at run time
- CObject class [MFC], dynamic object creation
- objects [MFC], creating dynamically at run time
- dynamic object creation [MFC]
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5763e3f0f3ee5a0e58ac20fe9f637e4f7e097999
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346649"
---
# <a name="dynamic-object-creation"></a>Dynamiczne tworzenie obiektów
W tym artykule opisano sposób tworzenia obiektu dynamicznie w czasie wykonywania. Procedura wykorzystuje informacje o klasie czasu wykonywania, zgodnie z opisem w artykule [podczas uzyskiwania dostępu do środowiska wykonawczego informacje o klasie](../mfc/accessing-run-time-class-information.md).  
  
#### <a name="to-dynamically-create-an-object-given-its-run-time-class"></a>Można dynamicznie utworzyć obiekt na podstawie jego klasa czasu wykonywania  
  
1.  Poniższy kod umożliwia dynamiczne tworzenie obiektów przy użyciu `CreateObject` funkcji `CRuntimeClass`. Należy pamiętać, że w przypadku awarii, `CreateObject` zwraca **NULL** zamiast wywoływanie wyjątek:  
  
     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/cpp/dynamic-object-creation_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie obiektu CObject](../mfc/using-cobject.md)

