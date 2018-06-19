---
title: Używanie list obrazów z formantami nagłówka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2da3737b54c53903f8fc8ff30cccba6165cbde45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382782"
---
# <a name="using-image-lists-with-header-controls"></a>Używanie list obrazów z formantami nagłówka
Elementy nagłówka mieć możliwość wyświetlania obrazu w elemencie nagłówka. Ten obraz przechowywany na liście skojarzony obraz jest 16 x 16 pikseli i ma takie same charakterystyki jako obrazów ikony używane w kontrolce widoku listy. Aby pomyślnie wdrożyć to zachowanie, należy najpierw utworzyć i zainicjować listy obrazów, skojarzony z formantem nagłówka listy, a następnie zmodyfikuj atrybuty elementu nagłówka, który wyświetla obraz.  
  
 Poniższa procedura przedstawia szczegółowe informacje, przy użyciu wskaźnika do formantu nagłówka (`m_pHdrCtrl`) i wskaźnika do listy obrazów (`m_pHdrImages`).  
  
### <a name="to-display-an-image-in-a-header-item"></a>Aby wyświetlić obraz w elemencie nagłówka  
  
1.  Konstrukcja nowej listy obrazów (lub użyć istniejącego obiektu listy obrazów) przy użyciu [CImageList](../mfc/reference/cimagelist-class.md) Konstruktor przechowywania wynikowego wskaźnika.  
  
2.  Zainicjuj nowy obiekt listy obrazów, wywołując [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Następujący kod jest przykładem tego wywołania.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]  
  
3.  Dodawanie obrazów dla każdego elementu nagłówka. Poniższy kod dodaje dwa obrazy wstępnie zdefiniowane.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]  
  
4.  Skojarz listy obrazów z formantem nagłówka wywołaniem [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).  
  
5.  Zmodyfikuj element nagłówka, aby wyświetlić obraz z listy skojarzony obraz. W poniższym przykładzie przypisano pierwszy obraz z `m_phdrImages`, aby pierwszy element nagłówka `m_pHdrCtrl`.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]  
  
 Aby uzyskać szczegółowe informacje na używane następujące wartości parametru, zapoznaj się odpowiednie [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).  
  
> [!NOTE]
>  Istnieje możliwość kilka formantów przy użyciu tej samej listy obrazów. Na przykład w kontrolce widok listy standardowych mogą wystąpić listy obrazów (of obrazów 16 x 16 pikseli) używany przez widoku małych ikon formantu widoku listy, a elementy nagłówka formantu widoku listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)

