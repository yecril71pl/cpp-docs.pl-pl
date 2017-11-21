---
title: "Kiedy warto korzystać z automatyzacji zdalnej? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Remote Automation, DCOM
ms.assetid: 4c4c8176-cfc0-44f7-bc87-b690f069ad2f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 101d34c9ed610cb375c0755e7698f45a1b16e935
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="where-does-remote-automation-fit-in"></a>Kiedy warto korzystać z automatyzacji zdalnej?
DCOM został wydany w 1996 i jest dostępne tylko na platformy 32-bitowe i 64-bitowych. Zespołu Visual Basic w firmie Microsoft ma zawsze występuje Visual Basic jako przy użyciu automatyzacji, aby umożliwić jego komunikację między składnikami. Brak wersji rozproszonej poważnie ograniczoną korzystanie z tych funkcji w środowiskach przedsiębiorstw, więc zespół opracowywanie Visual Basic 4.0 Enterprise Edition postanowiła zbadać tworzenie własny zestaw składników usług zdalnych dla automatyzacji części OLE i modelu COM. Wyraźnie widać głównych celem było upewnij się, że wynik będzie zgodny z i może zostać zastąpione przez protokół DCOM podczas stały się dostępne. Następnie one przystąpiła do zaimplementowania automatyzacji zdalnej (RA) dla platform Windows zarówno 16-bitowych, jak i 32-bitowych.  
  
 Automatyzacja zdalna nie jest związana z dowolnego języka, ale do wersji Visual C++ 4.2 Enterprise Edition, został wysłany tylko przy użyciu języka Visual Basic w wersji 4.0. Należy pamiętać, że w automatyzacji zdalnej jest całkowicie sytuacji przez protokół DCOM. Jeśli masz w aplikacjach za pomocą modelu DCOM zamiast automatyzacji zdalnej, należy zrobić. Istnieją jednak zastosowaniach automatyzacji zdalnej bardziej odpowiednie:  
  
-   Wszędzie tam, gdzie masz klientów 16-bitowych.  
  
-   Jeśli Twoja organizacja nie ma jeszcze wycofana włączoną DCOM wersji systemu Windows NT lub Windows 95.  
  
-   W przypadku uaktualniania istniejącego pakietu aplikacji używającej automatyzacji zdalnej do składników C++ Użyj zamiast jeden lub więcej składników programu Visual Basic.  
  
 Nie muszą istnieć różnic między programy utworzone, aby korzystać z automatyzacji zdalnej i utworzone do użycia automatyzacji za pośrednictwem modelu DCOM i narzędzia konfiguracji stał się bardzo proste przełączyć między automatyzacji zdalnej oraz modelu DCOM. W rezultacie nie jest trudne do uaktualniania aplikacji z automatyzacji zdalnej DCOM po infrastrukturę.  
  
## <a name="see-also"></a>Zobacz też  
 [Co oferuje zdalna Automatyzacja](what-does-remote-automation-provide-q.md)   
 [Historia modelu DCOM](../mfc/history-of-dcom.md)
