---
title: "Definiowanie mnemonik (klucze dostępu) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- access keys [C++], adding
- keyboard shortcuts [C++], controls
- dialog box controls, mnemonics
- access keys [C++], checking
- mnemonics, checking for duplicate
- mnemonics
- mnemonics, dialog box controls
- keyboard shortcuts [C++], uniqueness checking
- Check Mnemonics command
- controls [C++], access keys
- access keys [C++]
ms.assetid: 60a85435-aa30-4c5c-98b6-42fb045b9eb2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 167947e51ed773f765432148cbe879c926c57d5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="defining-mnemonics-access-keys"></a>Definiowanie mnemonik (klucze dostępu)
Zwykle użytkownicy klawiatury przenoszeniu fokus wprowadzania z jednego formantu w oknie dialogowym z kluczami kartę i strzałki. Można jednak zdefiniować klawisza dostępu (nazwę skrótu lub łatwych do zapamiętania), który umożliwia użytkownikom wybór formantu naciskając jednego klucza.  
  
### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Aby zdefiniować klucz dostępu dla formantu o widoczne podpis (przycisków, pól wyboru i przycisków radiowych)  
  
1.  Wybierz kontrolkę w oknie dialogowym.  
  
2.  W [okna właściwości](/visualstudio/ide/reference/properties-window)w **podpis** właściwości, wpisz nową nazwę dla formantu, wpisując znak (**&**) przed literą, który ma być jako klucz dostępu dla tego formantu. Na przykład `&Radio1`.  
  
3.  Naciśnij klawisz **wprowadź**.  
  
     Podkreślenie jest wyświetlana w wyświetlana nazwa, aby wskazać klawisz dostępu, na przykład **R**adio1.  
  
### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Aby zdefiniować klucz dostępu dla formantu bez podpisu widoczne  
  
1.  Tworzenie podpis dla formantu przy użyciu **tekst statyczny** kontroli w [przybornika](/visualstudio/ide/reference/toolbox).  
  
2.  W podpisie tekst statyczny, wpisz znak (**&**) przed literą, ma klucz dostępu.  
  
3.  Upewnij się, że formant tekst statyczny bezpośrednio przed formant, który go etykiety w kolejności tabulacji.  
  
 Klawisze dostępu w oknie dialogowym powinna być unikatowa.  
  
#### <a name="to-check-for-duplicate-access-keys"></a>Aby sprawdzić, czy klucze dostępu zduplikowane  
  
1.  Na **Format** menu, kliknij przycisk **Sprawdź Mnemoniki**.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)

