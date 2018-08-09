---
title: Definiowanie mnemonik (klucze dostępu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 960dcd17a1ff581db540aecfd536e9d2f2e98539
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645100"
---
# <a name="defining-mnemonics-access-keys"></a>Definiowanie mnemonik (klucze dostępu)
Zazwyczaj użytkownicy klawiatury przeniesienie fokusu wprowadzania z jednego formantu do drugiego w oknie dialogowym z **kartę** i **strzałkę** kluczy. Jednak można zdefiniować klawisz dostępu (nazwa mnemoników lub łatwa do zapamiętania) umożliwiający użytkownikom na wybór formantu przez naciśnięcie klawisza pojedynczego.  
  
### <a name="to-define-an-access-key-for-a-control-with-a-visible-caption-push-buttons-check-boxes-and-radio-buttons"></a>Aby zdefiniować klucza dostępu dla formantu za pomocą widoczne podpis (przyciski, pola wyboru i przyciski radiowe)  
  
1.  Wybierz kontrolkę w oknie dialogowym.  
  
2.  W [okno właściwości](/visualstudio/ide/reference/properties-window)w **podpis** właściwości, wpisz nową nazwę dla formantu, wpisując handlowe "i" (`&`) przed litery mają jako klucz dostępu dla tej kontrolki. Na przykład `&Radio1`.  
  
3.  Naciśnij klawisz **wprowadź**.  
  
     Podkreślenie pojawia się w wyświetlana nazwa, aby wskazać klawisz dostępu, na przykład **R**adio1.  
  
### <a name="to-define-an-access-key-for-a-control-without-a-visible-caption"></a>Aby zdefiniować klawisz dostępu bez podpisu widoczne kontrolki  
  
1.  Tworzenie podpisów dla formantu przy użyciu **tekst statyczny** w kontrolce [przybornika](/visualstudio/ide/reference/toolbox).  
  
2.  W podpisie tekst statyczny, wpisz znak (`&`) przed litery mają jako klucz dostępu.  
  
3.  Upewnij się, że formant statyczny tekst bezpośrednio poprzedza formant, który go etykiety w kolejności tabulacji.  
  
 Klucze dostępu w oknie dialogowym powinny być unikatowe.  
  
### <a name="to-check-for-duplicate-access-keys"></a>Aby sprawdzić, czy zduplikowany klucz dostępu  
  
1.  Na **Format** menu, kliknij przycisk **Sprawdź mnemonik**.  
  
 Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Wymagania  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty w oknach dialogowych](../windows/controls-in-dialog-boxes.md)   
 [Kontrolki](../mfc/controls-mfc.md)