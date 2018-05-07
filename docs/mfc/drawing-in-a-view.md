---
title: Rysowanie w widoku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc716800c35aa922f7912f586d6e5b8429593615
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="drawing-in-a-view"></a>Rysowanie w widoku
Prawie wszystkie rysowania w aplikacji występuje w widoku `OnDraw` funkcji członkowskiej, który należy zastąpić w klasie widoku. (Wyjątkiem jest myszy rysowania, omówione w [interpretowanie danych wejściowych za pośrednictwem widoku użytkownika](../mfc/interpreting-user-input-through-a-view.md).) Twoje `OnDraw` zastąpienia:  
  
1.  Pobiera dane przez wywołanie funkcji Członkowskich, podane przez użytkownika dokumentu.  
  
2.  Wyświetla dane przez wywoływanie funkcji Członkowskich obiektu kontekstu urządzenia platformę przekazuje do `OnDraw`.  
  
 Po zmianie danych dokumentu w inny sposób, widok musi być narysowany ponownie, aby odzwierciedlić zmiany. Zazwyczaj dzieje się tak, gdy użytkownik zmieni za pośrednictwem widoku dokumentu. W takim przypadku widok wywołuje dokumentu [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) funkcji członkowskiej do wszystkich widoków na tym samym dokumencie, aby zaktualizować się powiadomienia. `UpdateAllViews` wywołuje każdego widoku [OnUpdate](../mfc/reference/cview-class.md#onupdate) funkcję elementu członkowskiego. Domyślna implementacja `OnUpdate` unieważnia obszaru klienckiego całego widoku. Można je zastąpić, zanim unieważni tylko tych regionów obszaru klienta, które mapują zmodyfikowane części dokumentu.  
  
 `UpdateAllViews` Funkcji członkowskiej klasy **CDocument** i `OnUpdate` funkcji członkowskiej klasy `CView` let przekazać informacje opisujące, które części dokumentu zostały zmodyfikowane. Ten mechanizm "wskazówka" pozwala ograniczyć obszar, który należy odświeżyć widok. `OnUpdate` przyjmuje dwa argumenty "wskazówka". Pierwsza strona, `lHint`, typu **LPARAM**, umożliwia przekazywanie danych Ci się podoba, a druga, `pHint`, typu `CObject`*, umożliwia wskaźnikiem do każdego obiektu pochodną `CObject`.  
  
 Gdy widok staje się nieprawidłowy, system Windows wysyła on `WM_PAINT` wiadomości. Widok [OnPaint](../mfc/reference/cwnd-class.md#onpaint) funkcji obsługi odpowiada na komunikat przez utworzenie obiektu kontekstu urządzenia klasy [cpaintdc —](../mfc/reference/cpaintdc-class.md) i wywołuje danego widoku `OnDraw` funkcję elementu członkowskiego. Nie masz zwykle można zapisać, zastępując `OnPaint` funkcji obsługi.  
  
 A [kontekstu urządzenia](../mfc/device-contexts.md) to struktura danych systemu Windows, która zawiera informacje o atrybuty rysowania urządzeniami, takimi jak ekranu lub drukarki. Wszystkie wywołania rysowania są wykonywane za pośrednictwem obiektu kontekstu urządzenia. Na rysunku na ekranie `OnDraw` jest przekazywany `CPaintDC` obiektu. Na rysunku na drukarce, jest przekazywany [CDC](../mfc/reference/cdc-class.md) obiektu dla bieżącej drukarki.  
  
 Rysowanie w widoku czy kod najpierw pobiera wskaźnik do dokumentu, a następnie wywołań rysowania za pomocą kontekstu urządzenia. Następujące prosty `OnDraw` przykładzie przedstawiono proces:  
  
 [!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]  
  
 W tym przykładzie należy zdefiniować `GetData` działać jako elementu członkowskiego klasy pochodnej dokumentu.  
  
 Przykład drukuje niezależnie od ciągu pobiera z dokumentu, wyśrodkowane w widoku. Jeśli `OnDraw` wywołanie jest do rysowania ekranu `CDC` przekazano obiekt `pDC` jest `CPaintDC` którego konstruktor została już wywołana `BeginPaint`. Wywołania funkcji rysowania są nawiązywane przy użyciu wskaźnika kontekst urządzenia. Zawiera informacje o kontekstach urządzenia i wywołania rysunku, klasa [CDC](../mfc/reference/cdc-class.md) w *odwołania MFC* i [Praca z obiektami okien](../mfc/working-with-window-objects.md).  
  
 Aby uzyskać więcej przykładów dotyczących tworzenia `OnDraw`, zobacz [MFC — przykłady](../visual-cpp-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie widoków](../mfc/using-views.md)

