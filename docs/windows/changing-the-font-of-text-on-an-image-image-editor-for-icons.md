---
title: "Zmiana czcionki tekstu obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: fonts, changing on an image
ms.assetid: b8849d40-d401-4e06-808f-e615cb2bee3b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07dc7d7fd74ad9d4b0229ffef7cf4e96a4ea44b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-font-of-text-on-an-image-image-editor-for-icons"></a>Zmiana czcionki tekstu obrazu (Edytor obrazów dla ikon)
Poniższa procedura jest przykładem:  
  
-   Dodawanie tekstu do ikony w aplikacji systemu Windows  
  
-   Manipulowanie czcionki tekstu  
  
### <a name="to-change-the-font-of-text-on-an-image"></a>Zmiana czcionki tekstu obrazu  
  
1.  Tworzenie aplikacji formularzy Windows w języku C++. Aby uzyskać więcej informacji, zobacz [Tworzenie nowego projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa). [Szablon aplikacji formularzy systemu Windows](http://msdn.microsoft.com/en-us/1babdebf-ab3f-4a64-a608-98499a5b9cea) dodaje plik o nazwie domyślnej app.ico do projektu.  
  
2.  W Eksploratorze rozwiązań kliknij dwukrotnie plik app.ico. [Edytor obrazów](../windows/image-editor-for-icons.md) zostanie otwarty.  
  
3.  Z **obrazu** menu, wybierz opcję **narzędzia** , a następnie wybierz **narzędzia tekst**. [Okno dialogowe narzędzi tekstowych](../windows/text-tool-dialog-box-image-editor-for-icons.md) będą wyświetlane.  
  
4.  W okno dialogowe narzędzi tekstowych wpisz `C++` w obszarze pusty tekst. Ten tekst będzie wyświetlany w polu o zmiennym rozmiarze znajduje się w lewym górnym rogu app.ico, edytor obrazów.  
  
5.  W edytorze obrazów przeciągnij pole o zmiennych rozmiarach do Centrum app.ico, aby zwiększyć czytelność tekstu.  
  
6.  W oknie dialogowym narzędzia Tekst kliknij **czcionki** przycisku. [Okno dialogowe czcionki narzędzi tekstowych](../windows/text-tool-font-dialog-box-image-editor-for-icons.md) będą wyświetlane.  
  
7.  Okno dialogowe czcionki narzędzi tekstowych, wybierz **podzbiory** z listy dostępnych czcionek, które są wymienione w **czcionki** pola listy.  
  
8.  Wybierz **Bold** z listy stylów czcionek dostępnych na liście **styl czcionki** pola listy.  
  
9. Wybierz **10** z listy dostępnych punktów rozmiarów wymienionych w **rozmiar** pola listy.  
  
10. Kliknij przycisk **OK** przycisku. Okno dialogowe czcionki narzędzi tekstowych zostanie zamknięty i będzie stosować nowe ustawienia czcionki tekstu.  
  
11. Kliknij przycisk **Zamknij** przycisk w oknie dialogowym narzędzia tekst. Pole o zmiennym rozmiarze wokół tekstu zniknie z edytora obrazów.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Pasek narzędzi](../windows/toolbar-image-editor-for-icons.md)

