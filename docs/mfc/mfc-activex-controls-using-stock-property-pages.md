---
title: "Formanty MFC ActiveX: Używanie stron właściwości standardowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
dev_langs: C++
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04f49395959ec3b62f20716ddfb4ba7f4d89032d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Kontrolki ActiveX MFC: używanie stron właściwości standardowych
W tym artykule omówiono stron właściwości standardowych dostępnych dla formantów ActiveX i sposobu ich używania.  
  
 Aby uzyskać więcej informacji na używanie stron właściwości formantu ActiveX zobacz następujące artykuły:  
  
-   [Formanty MFC ActiveX: Strony właściwości](../mfc/mfc-activex-controls-property-pages.md)  
  
-   [Formanty ActiveX MFC: Dodawanie dodatkowej niestandardowej strony właściwości](../mfc/mfc-activex-controls-adding-another-custom-property-page.md)  
  
 MFC udostępnia trzy stron właściwości standardowych do użycia z formantami ActiveX: **CLSID_CColorPropPage**, **CLSID_CFontPropPage**, i **CLSID_CPicturePropPage**. Te strony odpowiednio wyświetlenia interfejsu użytkownika dla standardowych kolorów, czcionki i właściwości obrazu.  
  
 Aby dołączyć te strony właściwości do kontrolki, dodaj ich identyfikatorów do kodu, który inicjuje formantu tablicę identyfikatorów stron właściwości. W poniższym przykładzie ten kod znajduje się w pliku implementacji (. Tablica ma zawierać wszystkie trzy stron właściwości standardowych i domyślne właściwości strony inicjuje CPP) (o nazwie `CMyPropPage` w tym przykładzie):  
  
 [!code-cpp[NVC_MFC_AxOpt#21](../mfc/codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]  
  
 Należy pamiętać, że liczba właściwości strony w `BEGIN_PROPPAGEIDS` makra, to 4. Jest to liczba stron właściwości jest obsługiwana przez kontrolkę ActiveX.  
  
 Po dokonaniu tych zmian, ponownie skompiluj projekt. Formant ma teraz strony właściwości czcionki, obrazu i właściwości kolorów.  
  
> [!NOTE]
>  Jeśli nie można uzyskać dostępu do stron właściwości standardowych kontroli, prawdopodobnie biblioteki MFC DLL (MFCxx.DLL) nie został prawidłowo zarejestrowany z bieżącym systemem operacyjnym. Zazwyczaj wynika to z instalowania programu Visual C++ wersji systemu operacyjnego innego niż aktualnie uruchomiony.  
  
> [!TIP]
>  Jeśli nie są widoczne stron właściwości standardowych (patrz Uwaga poprzedniej), zarejestruj plik DLL, uruchamiając RegSvr32.exe z wiersza polecenia o nazwie Pełna ścieżka do pliku DLL.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Formanty MFC ActiveX: Dodawanie właściwości standardowych](../mfc/mfc-activex-controls-adding-stock-properties.md)

