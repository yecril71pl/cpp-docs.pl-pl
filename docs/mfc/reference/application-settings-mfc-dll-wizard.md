---
title: Ustawienia aplikacji, kreator biblioteki MFC DLL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.dll.appset
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
ms.openlocfilehash: f021f2023af839413306c1e3d56dc741749cf216
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276601"
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

## <a name="see-also"></a>Zobacz także

[Kreator biblioteki MFC DLL](../../mfc/reference/mfc-dll-wizard.md)<br/>
[Tworzenie projektu MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)
