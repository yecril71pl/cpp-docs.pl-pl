---
title: "Operowanie listami obrazów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 80eeea133c953622151fba8b83e4995c9e5bd478
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="manipulating-image-lists"></a>Operowanie listami obrazów
[Zastąp](../mfc/reference/cimagelist-class.md#replace) funkcji członkowskiej zastępuje obraz w listy obrazów ([CImageList](../mfc/reference/cimagelist-class.md)) z nowego obrazu. Ta funkcja jest również przydatne w przypadku dynamicznie zwiększyć liczbę obrazów w obiekcie listy obrazów. [SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount) funkcja dynamicznie zmienia liczbę obrazy przechowywane na liście obrazów. Jeśli możesz zwiększyć rozmiar listy obrazów, wywołanie **Zastąp** dodać obrazy do nowych miejsc obrazu. Jeśli musisz zmniejszyć rozmiar listy obrazów, obrazy, poza nowy rozmiar są zwalniane.  
  
 [Usuń](../mfc/reference/cimagelist-class.md#remove) funkcji członkowskiej usuwa obraz z listy obrazów. [Kopiowania](../mfc/reference/cimagelist-class.md#copy) funkcji członkowskiej można skopiować lub wymiana obrazów w obrębie listy obrazów. Tej funkcji można określić, czy obraz źródłowy powinien zostać skopiowany do indeksu docelowego lub obraz źródłowy i docelowy powinien być zamieniona.  
  
 Aby utworzyć nową listę obrazu przez scalenie dwie listy obrazów, użyj odpowiedniego przeciążenia [Utwórz](../mfc/reference/cimagelist-class.md#create) funkcję elementu członkowskiego. To przeciążenie metody **Utwórz** scalenia listy pierwszy obraz istniejącego obrazu przechowuje Wynikowy obraz w nowym obiekcie listy obrazów. Nowy obraz jest tworzony za pomocą rysowania drugiego obrazu w sposób niewidoczny dla użytkownika za pośrednictwem pierwszego. Maska nowego obrazu jest wynik operacji operatora logicznego OR w bity maski dla dwóch istniejących obrazów.  
  
 To jest powtarzany, dopóki wszystkie obrazy zostaną scalone i dodane do nowego obiektu listy obrazów.  
  
 Można zapisać informacji o obrazie archiwum przez wywołanie metody [zapisu](../mfc/reference/cimagelist-class.md#write) funkcji członkowskiej i odczytu kopii go przez wywołanie metody [odczytu](../mfc/reference/cimagelist-class.md#read) funkcję elementu członkowskiego.  
  
 [GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle), [Attach](../mfc/reference/cimagelist-class.md#attach), i [Detach](../mfc/reference/cimagelist-class.md#detach) funkcje Członkowskie umożliwia manipulowanie dojście listy obrazów dołączonych do `CImageList` obiektu, gdy [DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist) funkcji członkowskiej usuwa listy obrazów, bez niszczenia `CImageList` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CImageList](../mfc/using-cimagelist.md)   
 [Formanty](../mfc/controls-mfc.md)

