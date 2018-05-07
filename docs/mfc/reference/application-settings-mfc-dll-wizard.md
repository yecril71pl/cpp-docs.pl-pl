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
ms.openlocfilehash: 1a243b790881452a983c43fb92d8ebea18c26bcc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="application-settings-mfc-dll-wizard"></a>Ustawienia aplikacji, kreator biblioteki MFC DLL
Użyj tej strony Kreator biblioteki MFC DLL do projektowania i dodać podstawowe funkcje do nowego projektu biblioteki MFC DLL.  
  
## <a name="dll-type"></a>Typ biblioteki DLL  
 Wybierz typ biblioteki DLL, którego chcesz utworzyć.  
  
 **Regularne biblioteki MFC DLL przy użyciu współdzielonej biblioteki DLL MFC**  
 Wybierz tę opcję, aby połączyć program jako Wspólnej bibliotece DLL biblioteki MFC. Przy użyciu tej opcji, nie mogą współużytkować obiektów MFC między biblioteki DLL i wywołania aplikacji. Program wykonywania wywołań do biblioteki MFC w czasie wykonywania. Tej opcji zmniejsza wymagania dotyczące dysków i pamięci programu, jeśli składa się z wielu plików wykonywania korzystające z biblioteki MFC. Programy zarówno Win32 i MFC wywołaniem funkcji w bibliotece DLL. Należy ponownie rozesłać biblioteki MFC DLL z tego typu projektu.  
  
 **Regularne biblioteki MFC DLL z MFC statycznie połączone.**  
 Wybierz tę opcję, aby połączyć program statycznie do biblioteki MFC w czasie kompilacji. Programy zarówno Win32 i MFC wywołaniem funkcji w bibliotece DLL. Gdy ta opcja spowoduje zwiększenie rozmiaru program, nie trzeba ponownie rozesłać biblioteki MFC DLL z tego typu projektu. Obiekty MFC nie mogą współużytkować między biblioteki DLL i wywołania aplikacji.  
  
 **Biblioteka DLL rozszerzenia MFC**  
 Wybierz tę opcję, jeśli chcesz, aby program w celu wykonywania wywołań do biblioteki MFC w czasie wykonywania, a chcesz udostępnić obiektów MFC między biblioteki DLL i aplikacja wywołująca. Tej opcji zmniejsza wymagania dotyczące dysków i pamięci programu, jeśli składa się z wielu plików wykonywalnych, które używają biblioteki MFC. Tylko programy MFC wywołaniem funkcji w bibliotece DLL. Należy ponownie rozesłać biblioteki MFC DLL z tego typu projektu.  
  
## <a name="additional-features"></a>Dodatkowe funkcje  
 Wybierz, czy biblioteki DLL MFC powinna obsługiwać automatyzacji oraz czy powinna obsługiwać usługi Windows sockets.  
  
 **Automatyzacja**  
 Wybierz **automatyzacji** aby umożliwić programowi manipulowania obiektami zaimplementowana w innym programie. Wybieranie **automatyzacji** udostępnia również dla innych klientów automatyzacji programu. Zobacz [automatyzacji](../../mfc/automation.md) Aby uzyskać więcej informacji.  
  
 **Windows sockets**  
 Wybierz tę opcję, aby wskazać, że program obsługuje Windows sockets. Windows sockets umożliwiają pisania programów, które komunikują się za pośrednictwem sieci TCP/IP.  
  
 Gdy gniazda biblioteki DLL MFC z systemem Windows jest tworzony pomocy technicznej, [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) Inicjuje obsługę sockets i nagłówek MFC pliku StdAfx.h obejmuje AfxSock.h.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator biblioteki MFC DLL](../../mfc/reference/mfc-dll-wizard.md)   
 [Tworzenie projektu MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)

