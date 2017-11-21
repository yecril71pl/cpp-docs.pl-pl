---
title: "Ograniczenia dotyczące wartości symbolu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.restrictions.value
dev_langs: C++
helpviewer_keywords:
- symbols, value restrictions
- restrictions, symbol values
ms.assetid: 32467ec3-690b-4cd0-a4d0-7d189a3296cb
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9c3edccbf88ea6aeb975b9861ebd80817362c245
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="symbol-value-restrictions"></a>Ograniczenia dotyczące wartości symbolu
Wartości symboli może być liczbą całkowitą, wyrażone w normalnym trybie dla #define dyrektywy preprocesora. Poniżej przedstawiono przykładowe wartości symboli:  
  
```  
18  
4001  
0x0012  
-3456  
```  
  
 Wartości symboli dla zasobów (akceleratorów, mapy bitowe, kursorów, okna dialogowe, ikony, menu, tabele ciągów i informacje o wersji) muszą być liczbami dziesiętnymi z zakresu od 0 do 32 767 (ale nie może być szesnastkowym). Wartości symboli dla części zasoby, takie jak formantów okna dialogowego lub pojedyncze ciągi w tabeli ciągów może być z zakresu od 0 do 65 534 lub od-32 768 do 32 767.  
  
 Symbole zasobów są liczbami 16-bitowych. Możesz wprowadzić je jako podpisem lub bez znaku, jednak są one używane wewnętrznie jako liczb całkowitych bez znaku. Dlatego ujemne będzie można rzutować na ich odpowiednich wartość dodatnią.  
  
 Poniżej przedstawiono niektóre ograniczenia dotyczące wartości symbolu:  
  
-   Środowisko projektowe Visual Studio i MFC korzystać z niektórych liczba zakresów do celów specjalnych. Wszystkie numery z najbardziej znaczących bitem (-32 -1 lub 32768 do 65 534, w zależności od znak 768) są zastrzeżone przez MFC.  
  
-   Nie można zdefiniować wartość symbolu przy użyciu innych ciągów symbolu. Na przykład następujący definicji symboli nie jest obsługiwana:  
  
    ```  
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported  
    ```  
  
-   Makra preprocesora argumentów nie można używać jako definicje wartości. Na przykład:  
  
    ```  
    #define   IDD_ABOUT  ID(7) //not supported  
    ```  
  
     nie jest prawidłowym wyrażeniem niezależnie od tego, co `ID` daje w wyniku w czasie kompilacji.  
  
-   Aplikacja może mieć istniejący plik zawierający symbole zdefiniowane za pomocą wyrażeń. Aby uzyskać więcej informacji na temat sposobu dołączać symbole jako symbole tylko do odczytu, zobacz [przy użyciu udostępnionych (tylko do odczytu) lub symbole obliczane](../windows/including-shared-read-only-or-calculated-symbols.md).  
  
 Aby uzyskać więcej informacji na Liczba zakresów, zobacz [TN023: standardowe zasoby MFC](../mfc/tn023-standard-mfc-resources.md).  
  

  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiana wartości numerycznej symbolu](../windows/changing-a-symbol-s-numeric-value.md)   
 [Ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md)   
 [Wstępnie zdefiniowane symbole identyfikatorów](../windows/predefined-symbol-ids.md)