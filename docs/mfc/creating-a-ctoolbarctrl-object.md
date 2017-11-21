---
title: Tworzenie obiektu CToolBarCtrl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CToolBarCtrl
dev_langs: C++
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eecb599d84cedd742a15c4a5572ce4c130b19669
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-ctoolbarctrl-object"></a>Tworzenie obiektu CToolBarCtrl
[Ctoolbarctrl —](../mfc/reference/ctoolbarctrl-class.md) obiekty zawierają szeregu struktur danych wewnętrznych — lista mapy bitowe przycisków obrazu, lista ciągów Etykieta przycisku i listę `TBBUTTON` struktury — która skojarzyć obrazu i/lub ciągu pozycji, style, stan, i Identyfikator polecenia przycisku. Każdy z elementów tych struktur danych odwołuje się liczony od zera indeks. Przed użyciem `CToolBarCtrl` obiektu, należy skonfigurować te struktury danych. Aby uzyskać listę struktury danych, zobacz [formanty paska narzędzi](https://msdn.microsoft.com/library/47xcww9x.aspx) w zestawie Windows SDK. Lista ciągów można używać tylko etykiet przycisk; Nie można pobrać ciągów z paska narzędzi.  
  
 Aby użyć `CToolBarCtrl` obiektu, zazwyczaj będzie wykonaj następujące kroki:  
  
### <a name="to-use-a-ctoolbarctrl-object"></a>Aby użyć obiektu CToolBarCtrl  
  
1.  Utworzyć [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiektu.  
  
2.  Wywołanie [Utwórz](../mfc/reference/ctoolbarctrl-class.md#create) Tworzenie formantu typowych narzędzi systemu Windows i dołączenie go do `CToolBarCtrl` obiektu. Mapy bitowe przycisków, dodać mapy bitowe przycisków na pasku narzędzi przez wywołanie metody [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Ciąg etykiety w przypadku przycisków, dodać ciągi do paska narzędzi przez wywołanie metody [AddString](../mfc/reference/ctoolbarctrl-class.md#addstring) i/lub [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Po wywołaniu `AddString` i/lub `AddStrings`, należy wywołać [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) Aby uzyskać ciąg lub ciągów są wyświetlane.  
  
3.  Dodawanie przycisku struktury do paska narzędzi przez wywołanie metody [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).  
  
4.  Jeśli chcesz etykietki narzędzi obsługi **TTN_NEEDTEXT** wiadomości w pasku narzędzi okno właściciela, zgodnie z opisem w [Obsługa powiadomień dotyczących Porada narzędzi](../mfc/handling-tool-tip-notifications.md).  
  
5.  Jeśli chcesz użytkownikowi można dostosowywać pasek narzędzi obsługi dostosowania komunikatów powiadomień w oknie właściciela zgodnie z opisem w [Obsługa powiadomień dotyczących dostosowania](../mfc/handling-customization-notifications.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Formanty](../mfc/controls-mfc.md)

