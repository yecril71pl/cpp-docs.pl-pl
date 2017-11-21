---
title: "Biblioteki DLL rozszerzeń: Omówienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- AFXDLL library
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: eb5e10b7-d615-4bc7-908d-e3e99b7b1d5f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 39ed1531be553a66f22ac8b93e898a91cf5006e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-extension-dlls-overview"></a>Biblioteki DLL rozszerzeń MFC: omówienie
Rozszerzenia MFC DLL jest bibliotekę DLL, która zwykle implementuje klasy wielokrotnego użytku, pochodnych istniejące klasy Microsoft Foundation Class Library. Biblioteki DLL rozszerzenia MFC są tworzone przy użyciu wersji biblioteki DLL MFC (znanej także jako udostępniony wersja MFC). Tylko MFC pliki wykonywalne (aplikacji lub MFC dll), które są tworzone przy użyciu udostępnionych wersji biblioteki MFC, można użyć rozszerzenia MFC DLL. Z rozszerzeniem MFC DLL może wyprowadzać nowe klasy w niestandardowych z MFC i następnie oferowanie ta rozszerzona wersja MFC, aby aplikacje, które wywołują biblioteki DLL.  
  
 Biblioteki DLL rozszerzeń można również może być przekazywany pochodnych MFC obiektów między aplikacją a biblioteki DLL. Funkcje Członkowskie skojarzony z obiektem przekazany istnieje w module, w której został utworzony obiekt. Ponieważ te funkcje są poprawnie eksportowane, używając udostępnionych wersja biblioteki DLL MFC, za darmo można przekazać MFC lub wskaźniki obiektu pochodnego MFC pomiędzy aplikacją i ładuje biblioteki DLL rozszerzenia MFC.  
  
 Na przykład bibliotekę DLL, która spełnia podstawowych wymagań biblioteki DLL rozszerzenia MFC Zobacz przykład MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk). W szczególności sprawdź pliki Testdll1.cpp i Testdll2.cpp.  
  
 Należy pamiętać, że termin AFXDLL nie jest już używany w dokumentacji Visual C++. Biblioteka DLL rozszerzenia MFC ma takie same charakterystyki jak wcześniejsze AFXDLL.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Inicjowanie biblioteki DLL rozszerzenia MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Biblioteki DLL rozszerzeń MFC](../build/extension-dlls.md)  
  
-   [Przy użyciu bazy danych, OLE i MFC gniazda biblioteki DLL rozszerzeń w zwykłych bibliotekach DLL MFC](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
-   [Biblioteki DLL innego typu niż MFC: omówienie](../build/non-mfc-dlls-overview.md)  
  
-   [Regularne biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Tworzenie biblioteki DLL MFC](../mfc/reference/mfc-dll-wizard.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Rodzaje bibliotek DLL](../build/kinds-of-dlls.md)