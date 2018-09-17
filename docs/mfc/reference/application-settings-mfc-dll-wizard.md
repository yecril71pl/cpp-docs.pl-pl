---
title: Ustawienia aplikacji, Kreator biblioteki MFC DLL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.dll.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04fcf796c7d08cc2733edbf23b66c591e07ec71a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704980"
---
# <a name="application-settings-mfc-dll-wizard"></a>Ustawienia aplikacji, kreator biblioteki MFC DLL
Użyj tej strony Kreator biblioteki MFC DLL do projektowania i dodawanie podstawowych funkcji do nowego projektu biblioteki MFC DLL.  
  
## <a name="dll-type"></a>Typ biblioteki DLL  
 Wybierz typ biblioteki DLL, którą chcesz utworzyć.  
  
- **Regularne biblioteki MFC DLL za pomocą współdzielonej biblioteki DLL MFC**

   Wybierz tę opcję, aby połączyć program jako współdzieloną DLL biblioteki MFC. Korzystając z tej opcji nie można udostępniać obiektów MFC między biblioteką DLL i aplikacji wywołującej. Program sprawia, że wywołania do biblioteki MFC w czasie wykonywania. Tej opcji zmniejsza wymagania dotyczące dysku i pamięci programu, jeśli składa się z wielu plików wykonywania korzystające z biblioteki MFC. Programy Win32 i MFC można wywołać funkcji w bibliotece DLL. Należy ponownie rozesłać biblioteki MFC DLL za pomocą tego typu projektu.  
  
- **Połączone statycznie zwykłej biblioteki MFC DLL z MFC**

   Wybierz tę opcję, aby połączyć program statycznie biblioteki MFC w czasie kompilacji. Programy Win32 i MFC można wywołać funkcji w bibliotece DLL. Gdy ta opcja zwiększa rozmiar program, nie musisz redystrybuować MFC DLL za pomocą tego typu projektu. Nie można udostępniać obiektów MFC między biblioteką DLL i aplikacji wywołującej.  
  
- **Biblioteka DLL rozszerzenia MFC**

   Wybierz tę opcję, jeśli chcesz, aby program, aby wykonywać wywołania do biblioteki MFC w czasie wykonywania, a chcesz się podzielić obiektami MFC między biblioteką DLL i aplikacji wywołującej. Tej opcji zmniejsza wymagania programu, dysku i pamięci, jeśli składa się z wielu plików wykonywalnych, które używają biblioteki MFC. Tylko programy MFC można wywołać funkcji w bibliotece DLL. Należy ponownie rozesłać biblioteki MFC DLL za pomocą tego typu projektu.  
  
## <a name="additional-features"></a>Dodatkowe funkcje  

Wybierz, czy biblioteki MFC DLL powinien obsługiwać automatyzacji oraz czy powinien on obsługiwać Windows sockets.  
  
- **Automatyzacja**

   Wybierz **automatyzacji** umożliwiające programowi manipulowania obiektami zaimplementowane w innym programie. Wybieranie **automatyzacji** udostępnia również program innym klientom automatyzacji. Zobacz [automatyzacji](../../mfc/automation.md) Aby uzyskać więcej informacji.  
  
- **Windows sockets**

   Wybierz tę opcję, aby wskazać, że program obsługuje Windows sockets. Windows sockets umożliwiają pisanie programów, które komunikują się za pośrednictwem sieci TCP/IP.  
  
   Jeśli biblioteka DLL MFC przy użyciu Windows sockets pomocy technicznej jest tworzony, [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) Inicjuje obsługę gniazda, a plik nagłówka MFC StdAfx.h zawiera AfxSock.h.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator biblioteki MFC DLL](../../mfc/reference/mfc-dll-wizard.md)   
 [Tworzenie projektu MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)

