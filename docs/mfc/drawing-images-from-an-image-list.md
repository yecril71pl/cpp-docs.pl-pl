---
title: Rysowanie obrazów z poziomu listy obrazów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86983506770b9719972170dfbb70b02c8026e108
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345212"
---
# <a name="drawing-images-from-an-image-list"></a>Rysowanie obrazów z poziomu listy obrazów
Aby narysować obrazu, należy użyć [CImageList::Draw](../mfc/reference/cimagelist-class.md#draw) funkcję elementu członkowskiego. Określa wskaźnik do obiektu kontekstu urządzenia, indeks obrazu do rysowania lokalizacji kontekstu urządzenia, w którym do rysowania obrazu i zestaw flag, aby wskazać styl rysowania.  
  
 Po określeniu `ILD_TRANSPARENT` styl **rysowania** używa dwuetapowego procesu do rysowania maskowanego obrazu. Po pierwsze, wykonuje logiczną- i operacji na bitów obrazu i bity maski. Następnie wykonuje operację logicznej XOR wyniki pierwszej operacji i bitów tła kontekstu urządzenia docelowego. Ten proces tworzy przezroczystych obszarów w obraz wynikowy; oznacza to, że każdy białe bit maski powoduje, że odpowiadający mu bit Wynikowy obraz, który ma być przezroczysty.  
  
 Przed narysowaniem obrazu maskowanego na pełny kolor tła, należy użyć [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) funkcji członkowskiej, aby ustawić kolor tła listy obrazów na tym samym kolor jako miejsce docelowe. Ustawianie koloru eliminuje potrzebę tworzenie obszarów przezroczystych obrazu i umożliwia **rysowania** wystarczy skopiować obraz do kontekstu urządzenia docelowego, co spowoduje znaczne zwiększenie wydajności. Rysowanie obrazów, określ `ILD_NORMAL` stylów podczas wywoływania **rysowania**.  
  
 Można ustawić kolor tła dla listy maskowanego obrazu ([CImageList](../mfc/reference/cimagelist-class.md)) w dowolnej chwili, tak aby poprawnie rysuje w dowolnej jednolite tło. Ustawianie koloru tła `CLR_NONE` powoduje, że obrazy, aby być rysowany jako przezroczysty domyślnie. Aby uzyskać kolor tła listy obrazów, użyj [GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) funkcję elementu członkowskiego.  
  
 `ILD_BLEND25` i `ILD_BLEND50` style symulacja obrazu z kolorem wyróżnienie systemu. Te style są przydatne, jeśli używasz obrazu maskowanego reprezentujący obiekt, który użytkownik może wybrać. Na przykład można użyć `ILD_BLEND50` styl rysowania obrazu, gdy użytkownik wybierze opcję.  
  
 Nonmasked obrazu jest kopiowany do docelowego urządzenia kontekstu przy użyciu **SRCCOPY** rastrowe operacji. Kolory obrazu są wyświetlane takie same, niezależnie od koloru tła kontekst urządzenia. Style rysowania określonego w **rysowania** również nie mają wpływu na wygląd nonmasked obrazu.  
  
 Oprócz funkcję członkowską Draw innej funkcji [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), rozszerza możliwości, by renderować obraz. `DrawIndirect` przyjmuje jako parametr [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) struktury. Ta struktura może służyć do dostosowywania renderowania bieżącego obrazu, łącznie z użyciem rastrowe kody operacji (przycinanie —). Aby uzyskać więcej informacji na kody przycinanie — zobacz [kody operacji rastrowe](http://msdn.microsoft.com/library/windows/desktop/dd162892) i [map bitowych jako pędzle](http://msdn.microsoft.com/library/windows/desktop/dd183378) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CImageList](../mfc/using-cimagelist.md)   
 [Kontrolki](../mfc/controls-mfc.md)

