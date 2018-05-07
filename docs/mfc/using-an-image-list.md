---
title: Używanie List obrazów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5722a2ef8c4e93e4996ee243b3c01b6dd6aeca78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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

