---
title: Ponowna dystrybucja aplikacji ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2e5a91ffb267d413c980d2313efbf9b0c41c0932
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="redistributing-an-atl-application"></a>Ponowna dystrybucja aplikacji ATL
Począwszy od programu Visual Studio 2012 Active Template Library (ATL) jest tylko nagłówek biblioteki. Projekty ATL nie mają dynamiczne łącze do ATL opcji. Brak pakietu redystrybucyjnego biblioteki ATL jest wymagany.  
  
 Jeśli wszystkie aplikacja wykonywalna ATL, należy zarejestrować plik .exe (i zawarte w niej wszystkie formanty) wydając polecenie:  
  
```  
filename /regserver  
```  
  
 gdzie `filename` jest nazwą pliku wykonywalnego.  
  
 W programie Visual Studio 2010 Projekt ATL mogą być tworzone dla MinDependency lub konfiguracji MinSize. Konfiguracja MinDependency jest pobrać po ustawieniu **Użyj ATL** właściwości **statyczne łącze do ATL** na **ogólne** stronę właściwości i zestaw  **Biblioteka wykonawcza** właściwości **wielowątkowych (/ MT)** na **generowania kodu** strony właściwości (C/C++ folder).  
  
 Konfiguracja MinSize jest pobrać po ustawieniu **Użyj ATL** właściwości **dynamiczne łącze do ATL** na **ogólne** strony właściwości lub zestawu **środowiska wykonawczego Biblioteka** właściwości **Multi-threaded DLL (/ MD)** na **generowania kodu** strony właściwości (C/C++ folder).  
  
 MinSize sprawia, że dane wyjściowe pliku w małych, jak to możliwe, ale wymaga, aby ATL100.dll i pliku Msvcr100.dll (Jeśli wybrano **Multi-threaded DLL (/ MD)** opcji) znajdują się na komputerze docelowym. ATL100.dll powinny być rejestrowane na komputerze docelowym, aby upewnić się, że wszystkie funkcje ATL jest obecny. ATL100.dll zawiera ANSI i eksportuje Unicode.  
  
 Jeśli tworzysz Projekt ATL lub szablony OLE DB dla elementu docelowego MinDependency nie trzeba Zainstaluj i zarejestruj ATL100.dll na komputerze docelowym, mimo że można uzyskać większy obraz programu.  
  
 Jeśli wszystkie aplikacja wykonywalna ATL, należy zarejestrować plik .exe (i zawarte w niej wszystkie formanty) wydając polecenie:  
  
```  
filename /regserver  
```  
  
 gdzie `filename` jest nazwą pliku wykonywalnego.  
  
 Dla aplikacji szablony OLE DB upewnij się, że komputer docelowy ma najnowszej wersji plików programu Microsoft Data Access Components (MDAC). Aby uzyskać więcej informacji, zobacz [redystrybuowanie plików obsługi baz danych](../ide/redistributing-database-support-files.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Redystrybuowanie plików programu Visual C++](../ide/redistributing-visual-cpp-files.md)