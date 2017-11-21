---
title: "Automatyczne łączenie wersji biblioteki MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: defaultlib
dev_langs: C++
helpviewer_keywords:
- defaultlib in MFC
- automatic links [MFC]
- MFC libraries, linking to
- linking [MFC], automatic of MFC library version
- linking [MFC]
- linking [MFC], of MFC
- MFC libraries, versions
ms.assetid: 02af4a20-2034-4fce-b200-c2202c3c8311
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a9c9e9967fec6d52207e87803fa2d7a2bf42ccca
ms.sourcegitcommit: 0bbc9aac12c926b2b03726ae5b4a09d916e17d6b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2017
---
# <a name="automatic-linking-of-mfc-library-version"></a>Automatyczne łączenie wersji biblioteki MFC
W wersjach MFC przed w wersji 3.0 (przed Visual C++ w wersji 2.0) trzeba było ręcznie określić poprawną wersję biblioteki MFC na liście wejściowej biblioteki dla konsolidatora. Z MFC w wersji 3.0 i nowszych go nie trzeba już ręcznie określić wersji biblioteki MFC. Zamiast tego pliki nagłówków MFC automatycznie określić poprawną wersję biblioteki MFC, na podstawie wartości zdefiniowane z `#define`, takich jak **_DEBUG** lub **_unicode —**. Dodaj pliki nagłówków MFC **/defaultlib** dyrektywy poinstruowanie konsolidator łącze w określonej wersji biblioteki MFC.  
  
 Na przykład następujący fragment kodu z AFX. Plik nagłówka H powoduje, że konsolidator, aby łącze w obu NAFXCWD. LIB lub NAFXCW. Wersja biblioteki MFC, w zależności od tego, czy używasz wersji do debugowania MFC:  
  
```c++
#ifndef _UNICODE 
#ifdef _DEBUG
#pragma comment(lib, "nafxcwd.lib")
#else
#pragma comment(lib, "nafxcw.lib")
#endif
#else
#ifdef _DEBUG
#pragma comment(lib, "uafxcwd.lib")
#else
#pragma comment(lib, "uafxcw.lib")
#endif
#endif
```  
  
 Pliki nagłówkowe MFC również łącze w wszystkie wymagane biblioteki, włączając biblioteki MFC, biblioteki Win32, bibliotek OLE, bibliotek OLE zbudowane na podstawie próbek, biblioteki ODBC i tak dalej. Biblioteki Win32 obejmują Kernel32.Lib, User32.Lib i GDI32.Lib.  
  
## <a name="see-also"></a>Zobacz też  
 [Wersje biblioteki MFC](../mfc/mfc-library-versions.md)

