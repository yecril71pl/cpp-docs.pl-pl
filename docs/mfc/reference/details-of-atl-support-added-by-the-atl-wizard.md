---
title: "Szczegóły obsługi ATL dodane przez kreatora ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.atl.support
dev_langs: C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 49f17f1d5dd850034a802103ebd9208dc9bf8e87
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Szczegóły obsługi ATL dodanej przez kreatora ATL
Gdy zostanie [Dodaj obsługę ATL do istniejącego pliku wykonywalnego MFC lub biblioteki DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual C++ umożliwia następujące modyfikacje do istniejącego projektu MFC (w tym przykładzie nosi nazwę projektu `MFCEXE`):  
  
-   Zostaną dodane dwa nowe pliki (pliku .idl i pliku .rgs, używany do rejestrowania serwera).  
  
-   W aplikacji głównej nagłówka i implementacji (Mfcexe.h i Mfcexe.cpp) nową klasę (pochodną **CAtlMFCModule**) jest dodawany. Oprócz nowa klasa kodu jest dodawana do `InitInstance` rejestracji. Kod jest także dodawane do `ExitInstance` funkcji dla obiektu klasy odwołania. W pliku nagłówka koniec dwa nowe pliki nagłówka (pliku Initguid.h i Mfcexe_i.c) znajdują się w pliku implementacji, deklarowanie i Inicjowanie nowych identyfikatorów GUID dla **CAtlMFCModule**-klasy.  
  
-   Aby zarejestrować serwer poprawnie, wpis dla nowego pliku .rgs są dodawane do pliku zasobów projektu.  
  
## <a name="notes-for-dll-projects"></a>Uwagi dla projektów biblioteki DLL  
 Dodaj obsługę ATL do projektu MFC DLL, można zauważyć pewne różnice. Kod jest dodawany do **DLLRegisterServer** i **DLLUnregisterServer** funkcje rejestrowania i wyrejestrowania biblioteki DLL. Kod jest także dodawane do [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) i [metody DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa ATL w projekcie MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)   
 [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)   
 [Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../../ide/navigating-the-class-structure-visual-cpp.md)
