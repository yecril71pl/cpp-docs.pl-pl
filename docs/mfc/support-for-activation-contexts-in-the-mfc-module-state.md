---
title: Obsługa kontekstów aktywacji w stanie modułu MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- activation contexts [MFC]
- activation contexts [MFC], MFC support
ms.assetid: 1e49eea9-3620-46dd-bc5f-d664749567c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2713e0025c0587a4ab76813d4d07eed0825db447
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380712"
---
# <a name="support-for-activation-contexts-in-the-mfc-module-state"></a>Obsługa kontekstów aktywacji w stanie modułu MFC
MFC tworzy kontekst aktywacji przy użyciu zasobu manifestu podana przez moduł użytkownika. Aby uzyskać więcej informacji dotyczących sposobu tworzenia kontekstów aktywacji zobacz następujące tematy:  
  
-   [Konteksty aktywacji](http://msdn.microsoft.com/library/aa374153)  
  
-   [Manifesty aplikacji](http://msdn.microsoft.com/library/aa374191)  
  
-   [Manifesty](http://msdn.microsoft.com/library/aa374219)  
  
## <a name="remarks"></a>Uwagi  
 Podczas odczytywania w tych tematach zestaw Windows SDK, należy pamiętać, podobny kontekst aktywacji zestawu Windows SDK w mechanizm kontekstu aktywacji MFC, z wyjątkiem MFC nie używa interfejsu API systemu Windows SDK aktywacji kontekstu.  
  
 Kontekst aktywacji działa w aplikacjach MFC, użytkownik biblioteki dll i biblioteki DLL rozszerzenia MFC w następujący sposób:  
  
-   Aplikacje MFC używać zasobów ID 1 ich zasobu manifestu. W takim przypadku MFC nie tworzy własny kontekst aktywacji, ale korzysta z domyślnego kontekstu aplikacji.  
  
-   Użytkownik MFC biblioteki DLL zasobu identyfikator 2 przy użyciu ich zasobu manifestu. W tym miejscu MFC tworzy kontekstu aktywacji dla każdej biblioteki DLL użytkownika, więc inny użytkownik bibliotek DLL, możesz użyć innej wersji tego samego bibliotek (na przykład biblioteki formantów wspólnych).  
  
-   Biblioteki DLL rozszerzenia MFC polegają na ich hostingu aplikacji lub użytkownika biblioteki dll do ustanawiania ich kontekstu aktywacji.  
  
 Mimo że można modyfikować stanu kontekstu aktywacji przy użyciu procesów opisana w sekcji [przy użyciu interfejsu API kontekstu aktywacji](http://msdn.microsoft.com/library/aa376620), przy użyciu mechanizmu kontekstu aktywacji MFC mogą być przydatne podczas opracowywania oparte na bibliotekach DLL dodatku plug-in architektury Jeżeli nie jest łatwo (lub nie jest możliwe) do ręcznie przełączać stan aktywacji przed i po poszczególnych wywołań zewnętrznych wtyczek.  
  
 Kontekst aktywacji jest tworzony w [afxwininit —](../mfc/reference/application-information-and-management.md#afxwininit). Zostanie zniszczony w `AFX_MODULE_STATE` destruktora. Uchwyt kontekstu aktywacji jest przechowywany w `AFX_MODULE_STATE`. (`AFX_MODULE_STATE` jest opisany w [AfxGetStaticModuleState —](reference/extension-dll-macros.md#afxgetstaticmodulestate).)  
  
 [Afx_manage_state —](reference/extension-dll-macros.md#afx_manage_state) makro aktywuje i dezaktywuje kontekstu aktywacji. `AFX_MANAGE_STATE` jest włączone dla statycznych biblioteki MFC, jak również biblioteki DLL MFC, aby umożliwić kod wykonywany w kontekście prawidłowego aktywacji wybrane przez użytkownika biblioteki DLL MFC.  
  
## <a name="see-also"></a>Zobacz też  
 [Konteksty aktywacji](http://msdn.microsoft.com/library/aa374153)   
 [Manifesty aplikacji](http://msdn.microsoft.com/library/aa374191)   
 [Manifesty](http://msdn.microsoft.com/library/aa374219)   
 [Afxwininit —](../mfc/reference/application-information-and-management.md#afxwininit)   
 [AfxGetStaticModuleState —](reference/extension-dll-macros.md#afxgetstaticmodulestate)   
 [AFX_MANAGE_STATE —](reference/extension-dll-macros.md#afx_manage_state)

