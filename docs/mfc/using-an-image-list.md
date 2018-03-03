---
title: "Używanie List obrazów | Dokumentacja firmy Microsoft"
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
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4321649bf4e8fe0e34fef8fe37b8c96598bef2c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-an-image-list"></a>Używanie list obrazów
Typowy sposób listy obrazów jest zgodny ze wzorcem poniżej:  
  
-   Utworzyć [CImageList](../mfc/reference/cimagelist-class.md) obiektu i wywoływanie jednego z przeciążeń jego [Utwórz](../mfc/reference/cimagelist-class.md#create) funkcji do tworzenia listy obrazów i dołącz je do `CImageList` obiektu.  
  
-   Jeśli obrazy nie zostały dodane po utworzeniu listy obrazów, dodać obrazy do listy obrazów, wywołując [Dodaj](../mfc/reference/cimagelist-class.md#add) lub [odczytu](../mfc/reference/cimagelist-class.md#read) funkcję elementu członkowskiego.  
  
-   Skojarz listy obrazów z formantem przez wywołanie funkcji właściwego członka tego formantu lub rysowanie obrazów z listy obrazów, samodzielnie przy użyciu listy obrazów [rysowania](../mfc/reference/cimagelist-class.md#draw) funkcję elementu członkowskiego.  
  
-   Być może Zezwalaj użytkownikowi na przeciąganie obrazu, przy użyciu wbudowanych funkcji listy obrazów do przeciągania.  
  
> [!NOTE]
>  Jeśli na liście obraz został utworzony z **nowe** operatora, należy zniszczyć `CImageList` obiektu, gdy wszystko będzie gotowe z nim.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CImageList](../mfc/using-cimagelist.md)   
 [Kontrolki](../mfc/controls-mfc.md)

