---
title: "Alokowanie zasobów GDI | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7420dbdc1f7560eae9bc5b1a15954c3d68b59678
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="allocating-gdi-resources"></a>Alokowanie zasobów GDI
W tym artykule wyjaśniono, jak można przydzielić i deallocate potrzebne do drukowania obiekty interfejsu (GDI) systemu Windows grafiki urządzeń.  
  
> [!NOTE]
>  GDI + jest dołączony do systemu Windows XP i jest dostępny jako pakiet redystrybucyjny systemu Windows NT 4.0 z dodatkiem SP6, Windows 2000, Windows 98 i systemu Windows. Aby pobrać najnowszy pakiet redystrybucyjny programu, zobacz [http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm](http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm). Aby uzyskać więcej informacji, zobacz dokumentację interfejsu GDI + SDK w: [http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp](http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).  
  
 Załóżmy, że należy używać niektórych czcionek, pióra lub inne obiekty GDI do drukowania, ale nie dla ekranu. Z powodu pamięci, które wymagają one jest nieefektywne przydzielić tych obiektów, podczas uruchamiania aplikacji. Jeśli aplikacja nie jest drukowanie dokumentu, pamięci, mogą być wymagane do innych celów. Warto ich przydzielić po rozpoczęciu drukowanie, a następnie usuń je, podczas drukowania zakończenia.  
  
 Aby przydzielić te obiekty GDI, Przesłoń [OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting) funkcję elementu członkowskiego. Ta funkcja jest dobrze nadają się do tego celu dwóch powodów: struktura wywołuje tej funkcji raz na początku każdego zadania drukowania i, w odróżnieniu od [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting), ta funkcja ma dostęp do [CDC](../mfc/reference/cdc-class.md) Obiekt reprezentujący sterownika urządzenia. Te obiekty do użycia podczas wykonywania zadania drukowania można przechowywać przez definiowanie zmiennych Członkowskich w klasie widoku, które obiekty GDI (na przykład **cfont — \***  elementów członkowskich i tak dalej).  
  
 Aby użyć Obiekty GDI zostały utworzone, zaznacz je do kontekstu urządzenia drukarki w [OnPrint](../mfc/reference/cview-class.md#onprint) funkcję elementu członkowskiego. Jeśli potrzebujesz różnych obiektów GDI na różnych stronach dokumentu należy zbadać `m_nCurPage` członkiem [cprintinfo —](../mfc/reference/cprintinfo-structure.md) struktury i odpowiednio wybierz obiekt GDI. Jeśli potrzebujesz obiektów GDI na kolejnych stronach systemu Windows wymaga wybrania go do kontekstu urządzenia zawsze `OnPrint` jest wywoływana.  
  
 Aby cofnąć te obiekty GDI, Przesłoń [OnEndPrinting](../mfc/reference/cview-class.md#onendprinting) funkcję elementu członkowskiego. Struktura wywołuje tę funkcję na końcu każdego zadania drukowania, umożliwiając możliwość deallocate Obiekty GDI drukowanie specyficzne, zanim aplikacja powróci do innych zadań.  
  
## <a name="see-also"></a>Zobacz też  
 [Drukowanie](../mfc/printing.md)   
 [Jak jest wykonywane drukowanie domyślne](../mfc/how-default-printing-is-done.md)

