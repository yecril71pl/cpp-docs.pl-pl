---
title: Karty i kartę kontroli atrybutów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f925f8b6a5c522e22890ee2c1082ae8d709d2220
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tabs-and-tab-control-attributes"></a>Karty i atrybuty formantu karty
Masz znaczną kontrolę nad wyglądu i zachowania kart, które tworzą formantu karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Każda karta może mieć etykietę, ikonę stanu elementu i zdefiniowanym przez aplikację 32-bitową wartość skojarzonych z nim. Dla każdej karty można wyświetlić ikony i etykiety.  
  
 Ponadto każdy element karta może mieć trzy stany: naciśnięty, nieklikniętego lub wyróżnione. Ten stan można ustawić tylko przez zmodyfikowanie istniejącego elementu kartę. Aby zmodyfikować istniejący element kartę, należy pobrać go z wywołaniem do [GetItem](../mfc/reference/ctabctrl-class.md#getitem), zmodyfikuj `TCITEM` — Struktura (w szczególności **dwState** i **dwStateMask** elementy członkowskie danych ), a następnie wróć do modyfikacji `TCITEM` struktury wywołaniem [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Jeśli musisz wyczyścić stanów elementu wszystkich elementów w karcie `CTabCtrl` obiektów, wywoływania [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Ta funkcja resetuje stan wszystkich elementów kartę lub wszystkie elementy oprócz jednego wybranego.  
  
 Poniższy kod usuwa stan wszystkich elementów kartę i następnie modyfikuje stan trzeciego elementu:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]  
  
 Aby uzyskać więcej informacji o karcie atrybutów, zobacz [karty i atrybuty karty](http://msdn.microsoft.com/library/windows/desktop/bb760550) w zestawie Windows SDK. Aby uzyskać więcej informacji na temat Dodawanie kart do formantu karty, zobacz [Dodawanie kart do formantu karty](../mfc/adding-tabs-to-a-tab-control.md) dalszej części tego tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

