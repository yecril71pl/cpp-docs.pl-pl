---
title: "Initinstance — funkcja członkowska | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: InitInstance
dev_langs: C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c33a058c126cea4dc6ce6d51fb2d4866ceb9218f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="initinstance-member-function"></a>InitInstance — Funkcja członkowska
System operacyjny Windows umożliwia uruchamianie więcej niż jedną kopię lub "instance" tej samej aplikacji. `WinMain`wywołania [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) za każdym razem uruchamia nowe wystąpienie aplikacji.  
  
 Standardowe `InitInstance` implementacji tworzone przez Kreatora aplikacji MFC wykonuje następujące zadania:  
  
-   Jako jego centralnej akcja tworzy szablonów dokumentów, które z kolei tworzenie dokumentów, widoków i okien ramowych. Opis tego procesu, zobacz [Tworzenie szablonu dokumentu](../mfc/document-template-creation.md).  
  
-   Ładuje Opcje standardowego pliku z pliku ini lub rejestru systemu Windows, łącznie z nazwami ostatnio używanych plików.  
  
-   Rejestruje co najmniej jeden szablon dokumentu.  
  
-   Tworzy główne okno ramowe dla aplikacji MDI.  
  
-   Przetwarza wiersza polecenia, można otworzyć dokumentu, określona w wierszu polecenia lub, aby otworzyć nowy, pusty dokument.  
  
 Można dodać kodu inicjowania lub zmodyfikować kod napisany przez kreatora.  
  
> [!NOTE]
>  Aplikacje MFC musi zostać zainicjowany jako pojedynczy wątków typu apartment (STA). Jeśli należy wywołać [funkcja CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) w Twojej `InitInstance` zastępowania, określ `COINIT_APARTMENTTHREADED` (zamiast `COINIT_MULTITHREADED`). Aby uzyskać więcej informacji, zobacz PRB: MFC aplikacja przestaje odpowiadać podczas inicjowania aplikacji jako wielowątkowe apartamentu (828643) w [http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
## <a name="see-also"></a>Zobacz też  
 [CWinApp: Klasa aplikacji](../mfc/cwinapp-the-application-class.md)
