---
title: Okno klas pochodnych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- window class hierarchy
- hierarchies, window classes
- classes [MFC], derived
- CWnd class [MFC], classes derived from
- derived classes [MFC], window classes
- window classes [MFC], derived
ms.assetid: 6f7e437e-fbde-4a06-bfab-72d9dbf05292
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4601a04932f467be3b63527f12c46f797d9e11d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="derived-window-classes"></a>Pochodne klasy okien
Można utworzyć systemu windows bezpośrednio z [CWnd](../mfc/reference/cwnd-class.md), lub wyprowadzać nowe klasy okna z `CWnd`. Jest to, jak zwykle tworzenie własnych niestandardowych systemu windows. Jednak większość systemu windows używane w ramach programu zamiast tego są tworzone na podstawie jednej z `CWnd`-pochodnej klasy okien ramowych dostarczonych przez MFC.  
  
## <a name="frame-window-classes"></a>Klasy okien ramowych  
 [Cframewnd —](../mfc/reference/cframewnd-class.md)  
 Używany do SDI ramki okna, które ramki pojedynczego dokumentu i jego widoku. Okno ramowe jest główną ramkę okna aplikacji i okno ramowe w bieżącym dokumencie.  
  
 [Cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md)  
 Używane jako głównego okna ramowego dla aplikacji MDI. Główną ramkę okna jest kontenerem dla wszystkich okien dokumentu MDI i udostępnia je paska menu. Okna ramowe MDI jest najwyższego poziomu okno wyskakujące okienko wyświetlane na pulpicie.  
  
 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
 Używany dla pojedynczych dokumentów utworzonych w ramce głównej okna MDI. Każdy dokument i jego widoku w ramce są przez ramki okna podrzędnego MDI zawarty w główną ramkę okna MDI. Okna podrzędnego MDI okno ramowe typowe wygląda podobnie, ale znajduje się wewnątrz ramki okna MDI zamiast oczekuje na pulpicie. Jednak okna podrzędnego MDI nie ma własnego paska menu i muszą współdzielić na pasku menu MDI ramkę okna zawierającego go.  
  
 Aby uzyskać więcej informacji, zobacz [okien ramowych](../mfc/frame-windows.md).  
  
## <a name="other-window-classes-derived-from-cwnd"></a>Klasy okien, innych pochodnych CWnd  
 Oprócz okien ramowych kilka innych główne kategorie systemu windows są uzyskiwane z `CWnd`:  
  
 *Widoki*  
 Widoki są tworzone przy użyciu `CWnd`-klasy [CView](../mfc/reference/cview-class.md) (lub jeden z jej klas pochodnych). Widok jest podłączony do dokumentu i działa jako pośrednik między dokumentu i użytkownika. Widok jest okna podrzędnego (nie podrzędnych MDI) zwykle wypełnia obszaru klienckiego SDI ramkę okna lub ramki okna podrzędnego MDI (lub część obszaru klienta nie pasuje do żadnego paska narzędzi lub paska stanu).  
  
 *Okna dialogowe*  
 Okna dialogowe są tworzone przy użyciu `CWnd`-klasy [cdialog —](../mfc/reference/cdialog-class.md).  
  
 *Formularze*  
 Widoki formularzy na podstawie szablonu okna dialogowego zasobów, takich jak okna dialogowe, są tworzone przy użyciu klasy [CFormView](../mfc/reference/cformview-class.md), [CRecordView](../mfc/reference/crecordview-class.md), lub [CDaoRecordView](../mfc/reference/cdaorecordview-class.md).  
  
 *Kontrolki*  
 Formanty, takie jak przycisków i pola listy, pola kombi są tworzone przy użyciu innych klas pochodnych `CWnd`. Zobacz [kontrolować tematy](../mfc/controls-mfc.md).  
  
 *Paski sterowania*  
 Okno podrzędne, zawierające formanty. Przykładami paski narzędzi i paski stanu. Zobacz [paski sterowania](../mfc/control-bars.md).  
  
## <a name="window-class-hierarchy"></a>Hierarchia klasy okna  
 Zapoznaj się [diagram hierarchii MFC](../mfc/hierarchy-chart.md) w *odwołania MFC*. Widoki opisano szczegółowo w [architektury dokument/widok](../mfc/document-view-architecture.md). Okna dialogowe opisano szczegółowo w [okien dialogowych](../mfc/dialog-boxes.md).  
  
## <a name="creating-your-own-special-purpose-window-classes"></a>Tworzenie własnych klas specjalnych okna  
 Oprócz klasy okien pochodzącymi z biblioteki klas może być konieczne okno podrzędne specjalnych. Aby utworzyć okno programu, Utwórz swój własny [CWnd](../mfc/reference/cwnd-class.md)-klasy i stał się okna podrzędnego ramki lub widoku. Przy tym pamiętać, że platformę zarządza zakres obszar kliencki okno ramowe dokumentu. Większość obszaru klienckiego jest zarządzana przez widok, ale inne systemu windows, takich jak kontrola paski lub własne niestandardowe systemu windows może udostępniać przestrzeni widoku. Konieczne może wchodzić w interakcje z mechanizmów w klasach [CView](../mfc/reference/cview-class.md) i [ccontrolbar —](../mfc/reference/ccontrolbar-class.md) dla pozycjonowanie okien podrzędnych w oknie ramowym obszaru klienckiego.  
  
 [Tworzenie okien](../mfc/creating-windows.md) omówiono tworzenie obiektów okien i systemu windows, którymi zarządzają.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty okna](../mfc/window-objects.md)

