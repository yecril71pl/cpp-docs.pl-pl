---
title: Zmiana kolejności kart formantów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], tab order
- focus, tab order
- tab controls, tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls, tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 33e6e9624e7e927860a184361d45f855f3a1e4f6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="changing-the-tab-order-of-controls"></a>Zmiana kolejności kart formantów
Kolejność tabulacji to kolejność, w którym klawisz TAB przenosi fokus wprowadzania z jednego formantu do następnego okna dialogowego. Zazwyczaj kolejności tabulacji przebieg od lewej do prawej i od góry do dołu w oknie dialogowym. Każdy formant ma **Tabstop** właściwość, która określa, czy formant uzyskuje fokus wprowadzania.  
  
### <a name="to-set-input-focus-for-a-control"></a>Aby ustawić fokus wprowadzania kontrolki  
  
1.  W [okna właściwości](/visualstudio/ide/reference/properties-window), wybierz pozycję **True** lub **False** w **Tabstop** właściwości.  
  
 Nawet formantów, które nie mają właściwości Tabstop ustawioną wartość True, muszą być częścią kolejności tabulacji. Może to być istotne, na przykład, gdy użytkownik [zdefiniować klucze dostępu (klawiszy skrótu)](../windows/defining-mnemonics-access-keys.md) dla formantów, które nie mają podpisy. Statyczny tekst, który zawiera klucz dostępu do pokrewnej kontrolki musi bezpośrednio poprzedzać pokrewnej kontrolki w kolejności tabulacji.  
  
> [!NOTE]
>  Jeśli Twoje okno dialogowe zawiera nakładające się formanty, zmiana kolejności kart może zmienić sposób wyświetlania kontrolki. Formanty, które są dostarczane później w kolejności tabulacji są zawsze wyświetlane u góry nakładające się formantów, które należy poprzedzić je w kolejności tabulacji.  
  
#### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Aby wyświetlić bieżące kolejności tabulacji dla wszystkich kontrolek w oknie dialogowym  
  
1.  Na **Format** menu, kliknij przycisk **kolejności tabulacji**.  
  
 \- lub -  
  
-   Naciśnij klawisze CTRL + D.  
  
#### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Aby zmienić kolejność tabulacji dla wszystkich kontrolek w oknie dialogowym  
  
1.  Na **Format** menu, kliknij przycisk **kolejności tabulacji**.  
  
     Liczba w lewym górnym rogu każdej kontrolki zawiera jego miejsce w bieżącej kolejności tabulacji.  
  
2.  Ustawianie kolejności tabulacji, klikając każdego formantu w kolejności, w jakiej ma klawisz TAB, aby wykonać.  
  
3.  Naciśnij klawisz **ENTER** aby zakończyć **kolejności tabulacji** tryb.  
  
    > [!TIP]
    >  Po wprowadzeniu tryb kolejności tabulacji, naciśnij klawisz ESC lub ENTER, aby wyłączyć możliwość zmiany kolejności tabulacji.  
  
#### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Aby zmienić kolejność tabulacji dla dwóch lub więcej formantów  
  
1.  Z **Format** menu, wybierz **kolejności tabulacji**.  
  
2.  Określ, gdzie rozpocznie się zmiany w kolejności. Aby to zrobić, przytrzymaj **CTRL** klucza, a następnie kliknij przycisk kontroli przed jednym miejscu zmienione kolejność, aby rozpocząć.  
  
     Na przykład jeśli chcesz zmienić kolejność formanty 7 do 9, przytrzymaj klawisz CTRL, a następnie najpierw wybrać formant 6.  
  
    > [!NOTE]
    >  Aby ustawić określonego formantu o numerze 1 (pierwszy w kolejności tabulacji), kliknij dwukrotnie formant.  
  
3.  Zwolnij klawisz CTRL, a następnie kliknij formanty w kolejności, w jakiej ma klawisz TAB, aby postępować zgodnie z tego punktu.  
  
4.  Naciśnij klawisz **ENTER** aby zakończyć **kolejności tabulacji** tryb.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Rozmieszczenie formantów w oknach dialogowych](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)

