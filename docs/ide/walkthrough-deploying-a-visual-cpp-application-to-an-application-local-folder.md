---
title: "Wdrażanie aplikacji Visual C++ do folderu lokalnego aplikacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba12271fa4614b5ec0c7c70b3a7773152ebfec3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Wskazówki: wdrażanie aplikacji Visual C++ do folderu lokalnego aplikacji
Zawiera opis sposobu wdrażania aplikacji Visual C++ przez kopiowanie plików do folderu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
-   Komputer, który ma zainstalowanego programu Visual Studio.  
  
-   Inny komputer, który nie ma bibliotek języka Visual C++.  
  
### <a name="to-deploy-an-application-to-an-application-local-folder"></a>Aby wdrożyć aplikację do folderu lokalnego aplikacji  
  
1.  Tworzenie i kompilacja aplikacji MFC, wykonując kroki opisane w [wskazówki: Wdrażanie Visual C++ aplikacji za pomocą instalacji projektu](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).  
  
2.  Skopiuj odpowiednie pliki biblioteki MFC i C Run-Time (CRT) — na przykład dla x86 platformy i obsługi formatu Unicode, mfc100u.dll kopiowania i pliku msvcr100.dll z 10.0\VC\redist\x86\—and Visual Studio \Program Files\Microsoft następnie wklej je w folderze \Release\ Projekt MFC. Aby uzyskać więcej informacji na temat innych plików, które mogą wystąpić, aby skopiować zobacz [określania które biblioteki dll do ponownej dystrybucji](../ide/determining-which-dlls-to-redistribute.md).  
  
3.  Uruchom aplikację MFC na innym komputerze, który nie ma bibliotek języka Visual C++.  
  
    1.  Skopiuj zawartość folderu \Release\ i wklej je w folderze aplikacji na drugim komputerze.  
  
    2.  Uruchom aplikację na drugim komputerze.  
  
     Aplikacja zostanie uruchomiona pomyślnie bibliotek języka Visual C++ nie są dostępne w folderze lokalnego aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady wdrożeń](../ide/deployment-examples.md)