---
title: "Ograniczniki tagów dokumentacji Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 134605f86ef8019d34f5246fd75abbbf94d40fbc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Ograniczniki tagów dokumentacji Visual C++
Korzystanie z tagów dokumentacji wymaga ograniczników, które wskazują w kompilatorze, gdzie komentarzy dokumentacji rozpoczęcia i zakończenia.  
  
 Można użyć następujące rodzaje ograniczniki tagów dokumentacji XML:  
  
 `///`  
 Jest to formularz, który jest wyświetlany w przykładach dokumentacji i używane przez Szablony projektów Visual C++.  
  
 `/** */`  
 Są to wielowierszowy ograniczników.  
  
 Istnieją reguły niektóre formatowania w przypadku korzystania z `/** */` ogranicznik:  
  
-   Dla wiersza, który zawiera `/**` ogranicznik, jeśli do końca wiersza jest białe, wiersz nie został przetworzony przeznaczone do komentarzy. Jeśli pierwszym znakiem jest białe, czy biały znak jest ignorowane, a pozostałe wiersz jest przetwarzany. W przeciwnym razie cały tekst wiersza po `/**` ogranicznik jest przetwarzany jako część komentarza.  
  
-   Dla wiersza, który zawiera `*/` ogranicznik, jeśli istnieje tylko biały znak do `*/` ogranicznika wiersza jest ignorowana. W przeciwnym razie tekst w wierszu do `*/` ogranicznik jest przetwarzany jako część komentarza, opisane w poniższych punktor zasadom dopasowywanie do wzorca.  
  
-   Po tym, który rozpoczyna się od linii `/**` ogranicznik, kompilator szuka wspólnego wzorca na początku każdego wiersza składa się z opcjonalne białe oraz znak gwiazdki (`*`), a następnie opcjonalnie biały znak. Jeśli kompilator znajdzie ze wspólnego zestawu znaków na początku każdego wiersza, zignoruje ten wzorzec dla wszystkich wierszy po `/**` ogranicznika, prawdopodobnie łącznie wiersza, który zawiera `*/` ogranicznika.  
  
 Kilka przykładów:  
  
-   Tylko część następujące komentarz, który zostanie przetworzona jest wiersza, który rozpoczyna się od `<summary>`. Następujące dwa formaty utworzy komentarze w tym samym:  
  
    ```  
    /**  
    <summary>text</summary>   
    */  
    /** <summary>text</summary> */  
    ```  
  
-   Kompilator stosuje wzorzec "*" do ignorowania na początku linii drugiego i trzeciego.  
  
    ```  
    /**  
     * <summary>  
     *  text </summary>*/  
    ```  
  
-   Kompilator znajduje nie wzorca w komentarz, ponieważ nie istnieje żadne gwiazdki w drugim wierszu. W związku z tym cały tekst w wierszach drugiego i trzeciego do `*/`, będą przetwarzane w ramach komentarza.  
  
    ```  
    /**  
     * <summary>  
       text </summary>*/  
    ```  
  
-   Kompilator znajduje nie wzorca w komentarz dwóch powodów. Najpierw nie istnieje żaden wiersz rozpoczynający się spójne liczbę spacji przed znakiem gwiazdki. Drugie piątej wiersz rozpoczyna się od kartę, która jest niezgodna z spacji. W związku z tym cały tekst z drugiego wiersza do `*/` będą przetwarzane w ramach komentarza.  
  
    ```  
    /**  
      * <summary>  
      * text   
     *  text2  
       *  </summary>  
    */  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)