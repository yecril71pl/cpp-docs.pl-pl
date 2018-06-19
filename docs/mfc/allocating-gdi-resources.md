---
title: Alokowanie zasobów GDI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 25f05c29c74756276cdf3fd1f88048b9a5b87fa7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343224"
---
# <a name="allocating-gdi-resources"></a>Alokowanie zasobów GDI
W tym artykule wyjaśniono, jak można przydzielić i deallocate potrzebne do drukowania obiekty interfejsu (GDI) systemu Windows grafiki urządzeń.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji, zobacz dokumentację interfejsu GDI + SDK w: [ http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).  
  
 Załóżmy, że należy używać niektórych czcionek, pióra lub inne obiekty GDI do drukowania, ale nie dla ekranu. Z powodu pamięci, które wymagają one jest nieefektywne przydzielić tych obiektów, podczas uruchamiania aplikacji. Jeśli aplikacja nie jest drukowanie dokumentu, pamięci, mogą być wymagane do innych celów. Warto ich przydzielić po rozpoczęciu drukowanie, a następnie usuń je, podczas drukowania zakończenia.  
  
 Aby przydzielić te obiekty GDI, Przesłoń [OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting) funkcję elementu członkowskiego. Ta funkcja jest dobrze nadają się do tego celu dwóch powodów: struktura wywołuje tej funkcji raz na początku każdego zadania drukowania i, w odróżnieniu od [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting), ta funkcja ma dostęp do [CDC](../mfc/reference/cdc-class.md) Obiekt reprezentujący sterownika urządzenia. Te obiekty do użycia podczas wykonywania zadania drukowania można przechowywać przez definiowanie zmiennych Członkowskich w klasie widoku, które obiekty GDI (na przykład **cfont — \***  elementów członkowskich i tak dalej).  
  
 Aby użyć Obiekty GDI zostały utworzone, zaznacz je do kontekstu urządzenia drukarki w [OnPrint](../mfc/reference/cview-class.md#onprint) funkcję elementu członkowskiego. Jeśli potrzebujesz różnych obiektów GDI na różnych stronach dokumentu należy zbadać `m_nCurPage` członkiem [cprintinfo —](../mfc/reference/cprintinfo-structure.md) struktury i odpowiednio wybierz obiekt GDI. Jeśli potrzebujesz obiektów GDI na kolejnych stronach systemu Windows wymaga wybrania go do kontekstu urządzenia zawsze `OnPrint` jest wywoływana.  
  
 Aby cofnąć te obiekty GDI, Przesłoń [OnEndPrinting](../mfc/reference/cview-class.md#onendprinting) funkcję elementu członkowskiego. Struktura wywołuje tę funkcję na końcu każdego zadania drukowania, umożliwiając możliwość deallocate Obiekty GDI drukowanie specyficzne, zanim aplikacja powróci do innych zadań.  
  
## <a name="see-also"></a>Zobacz też  
 [Drukowanie](../mfc/printing.md)   
 [Jak jest wykonywane drukowanie domyślne](../mfc/how-default-printing-is-done.md)

