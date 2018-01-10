---
title: 'TN023: Standardowe zasoby MFC | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.resources
dev_langs: C++
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6fded011fda52dfde46804b03699dc93469e5e32
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tn023-standard-mfc-resources"></a>TN023: standardowe zasoby MFC
Ta uwaga opisuje standardowe zasoby podłączone do, a wymagane przez biblioteki MFC.  
  
## <a name="standard-resources"></a>Standardowe zasoby  
 MFC oferuje dwie kategorie wstępnie zdefiniowanych zasobów, których można użyć w aplikacji: zasobów pozyskiwać i standardowe zasoby.  
  
 Zasoby pozyskiwać są dodatkowe zasoby, które platformę nie zależy, ale które warto dodać do interfejsu użytkownika. W następujących zasobach pozyskiwać znajdują się w próbce ogólne MFC [CLIPART](../visual-cpp-samples.md):  
  
-   Common.RC: Jeden plik zasobów:  
  
    -   Kolekcja duże ikony, które reprezentują wiele firm i zadań przetwarzania danych.  
  
    -   Kilka typowe kursory (patrz także Afxres.rc).  
  
    -   Mapy bitowej do paska narzędzi, który zawiera kilka przycisków paska narzędzi.  
  
    -   Zasoby ikona i mapy bitowej, które są używane przez Commdlg.dll.  
  
-   Indicate.RC: Zawiera zasoby ciągów dla wskaźników klucza stanu paska stanu, takie jak "CAP" dla włączony klawisz Caps Lock.  
  
-   Prompts.RC: Zawiera zasoby ciągów menu wiersz dla każdego wstępnie zdefiniowanego polecenia, takie jak "Utwórz nowy dokument" `ID_FILE_NEW`.  
  
-   COMMDLG.RC: Visual C++ .rc zgodny plik zawierający standardowe szablony okna dialogowego pliku COMMDLG.  
  
 Standardowe zasoby są zasoby z identyfikatory zdefiniowane AFX ramach zależy od implementacji wewnętrznego. Rzadko należy zmieniać te zasoby zdefiniowane AFX. Jeśli to zrobisz, należy wykonać procedury opisane w dalszej części tego tematu.  
  
 Następujące zasoby struktury są zawarte w katalogu MFC\INCLUDE:  
  
-   Afxres.RC: Wspólnych zasobów używanych przez platformę.  
  
-   Afxprint.RC: Zasoby specyficzne dla drukowania.  
  
-   Afxolecl.RC: Zasoby specyficzne dla aplikacji klienckich OLE.  
  
-   Afxolev.RC: Zasoby specyficzne dla pełnej aplikacje serwera OLE.  
  
## <a name="using-clip-art-resources"></a>Korzystanie z zasobów pozyskiwać  
  
#### <a name="to-use-a-clip-art-binary-resource"></a>Aby użyć pozyskiwać zasobu binarnego  
  
1.  Otwórz plik zasobów aplikacji w programie Visual C++.  
  
2.  Otwórz Common.rc. Ten plik zawiera wszystkie zasoby pozyskiwać binarnego. Może to potrwać pewien czas, ponieważ plik Common.rc został skompilowany.  
  
3.  Przytrzymaj klawisz CTRL podczas przeciągania zasoby, które ma być używany z Common.rc do pliku zasobów aplikacji.  
  
 Aby korzystać z innych zasobów pozyskiwać, wykonaj te same czynności. Jedyna różnica polega na tym, czy plik .rc odpowiednie zamiast Common.rc zostanie otwarty.  
  
> [!NOTE]
>  Nie można więc przypadkowo trwale przenoszenia zasobów poza Common.rc. Przytrzymując klawisz CTRL podczas przeciągania zasobów, spowoduje utworzenie kopii. Jeśli użytkownik nie przytrzymaj klawisz CTRL podczas przeciągania, zasoby będą przeniesione. Jeśli dane mogą przypadkowo wprowadzone zmiany w pliku Common.rc, kliknij przycisk "Nie", po wyświetleniu pytania, czy zapisać zmiany w Common.rc.  
  
> [!NOTE]
>  .RC — pliki zasobów ma specjalnego `TEXTINCLUDE` w tych zasobów, które będą zapobiegać przypadkowemu zapisywania na standardowe .RC — pliki.  
  
### <a name="customizing-standard-framework-resources"></a>Dostosowywanie standardowe zasoby  
 Standardowe zasoby zwykle znajdują się w aplikacji przy użyciu # polecenie include w pliku zasobów aplikacji. Kreatorami AppWizard wygeneruje plik zasobów. Ten plik zawiera zasoby odpowiednie struktury standardowe, w zależności od tego, jakie opcje kreatorami AppWizard wybierz. Można przejrzeć, dodać lub usunąć zasobów, do których mają zostać uwzględnione zmiana dyrektywy kompilacji. Aby to zrobić, otwórz **zasobów** menu i wybierz **ustawić obejmuje**. Spójrz na edytowanie elementu "Dyrektywy kompilacji". Na przykład:  
  
```  
#include "afxres.rc"  
#include "afxprint.rc"  
```  
  
 Najbardziej typowych przypadkach dostosowywania standardowe zasoby jest dodanie lub usunięcie dodatkowych obejmuje do drukowania, klient OLE i obsługi serwera OLE.  
  
 W rzadkich przypadkach warto dostosować zawartość zasoby struktury standardowego dla określonej aplikacji nie tylko dodawać i usuwać całego pliku. Kroki po pokazują, jak można ograniczyć zasoby, które znajdują się:  
  
##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>Aby dostosować zawartość pliku zasobu standardowe  
  
1.  Otwórz plik zasobów w programie Visual C++.  
  
2.  Przy użyciu polecenia zasobów ustawić obejmuje usunięcie `#include` pliku .rc standardowe, który chcesz dostosować. Na przykład, aby dostosować paska narzędzi podglądu wydruku, Usuń `#include "afxprint.rc"` wiersza.  
  
3.  Otwieranie plików odpowiednie standardowe zasoby w MFC\INCLUDE. Następujący przykład we wcześniejszej części tego tematu odpowiedni plik jest MFC\Include\Aafxprint.rc  
  
4.  Skopiuj wszystkie zasoby z plik .rc standardowa do Twojego pliku zasobu aplikacji.  
  
5.  Zmodyfikuj kopię standardowe zasoby programu w pliku zasobów aplikacji.  
  
> [!NOTE]
>  Nie należy modyfikować zasobów bezpośrednio w standardowe .RC — pliki. W ten sposób spowoduje jej modyfikacji zasoby dostępne w każdej aplikacji, a nie tylko z tego, który pracuje obecnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

