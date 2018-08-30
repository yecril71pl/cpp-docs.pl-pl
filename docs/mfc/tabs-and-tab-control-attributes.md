---
title: Karty i kartę kontrolowania atrybuty | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c02f939c9f9314f3e24921879836c2743ae7d5ea
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43223285"
---
# <a name="tabs-and-tab-control-attributes"></a>Karty i atrybuty formantu karty
Masz znaczną kontrolę nad wyglądu i zachowania kart, które tworzą formantu karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Każda karta może mieć etykietę, ikony, stan elementu i zdefiniowanych przez aplikację 32-bitową wartość skojarzonych z nim. Dla każdej karty można wyświetlić, ikona i/lub etykiety.  
  
 Ponadto każdy element karta może mieć trzy stany: naciśnięty, nieklikniętego lub wyróżnione. Ten stan można ustawić tylko przez zmodyfikowanie istniejącego elementu karty. Aby zmodyfikować istniejący element kartę, należy pobrać go przy użyciu wywołania do [GetItem](../mfc/reference/ctabctrl-class.md#getitem), zmodyfikować `TCITEM` struktury (w szczególności *dwState* i *dwStateMask* elementy członkowskie danych ), a następnie zwracają zmodyfikowanego `TCITEM` struktury z wywołaniem [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Jeśli musisz wyczyścić stanów elementu wszystkich elementów w karcie `CTabCtrl` obiektu, wywołanie [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Ta funkcja resetuje stan wszystkich elementów kartę lub wszystkie elementy z wyjątkiem aktualnie wybrany.  
  
 Poniższy kod usuwa stan wszystkich elementów w karcie i następnie modyfikuje stan trzeci element:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]  
  
 Aby uzyskać więcej informacji na temat atrybutów karty zobacz [karty i atrybuty w karcie](/windows/desktop/Controls/tab-controls) w zestawie Windows SDK. Aby uzyskać więcej informacji na temat Dodawanie kart do formantu karty zobacz [Dodawanie kart do formantu karty](../mfc/adding-tabs-to-a-tab-control.md) w dalszej części tego tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

