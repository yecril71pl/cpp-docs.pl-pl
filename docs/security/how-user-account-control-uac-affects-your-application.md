---
title: "Jak Kontrola konta użytkownika (UAC) wpływa na aplikację | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 742d84300a7139e392bda19142643fe469231bdc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Jak kontrola konta użytkownika (UAC) wpływa na aplikację?
Kontrola konta użytkownika (UAC) jest funkcją systemu Windows Vista, w którym użytkownik kont ma ograniczone uprawnienia. Można znaleźć szczegółowe informacje na temat funkcji Kontrola konta użytkownika w tych lokacjach:  
  
-   [Przewodnik krok po kroku kontroli konta użytkownika systemu Windows Vista](http://go.microsoft.com/fwlink/?linkid=53781)  
  
-   [Deweloper najlepsze rozwiązania i wskazówki dotyczące aplikacji w środowisku najniższych uprawnieniach](http://go.microsoft.com/fwlink/?linkid=82444)  
  
-   [Opis i konfigurowanie Kontrola konta użytkownika w systemie Windows Vista](http://go.microsoft.com/fwlink/?LinkId=82445)  
  
## <a name="building-projects-after-enabling-uac"></a>Kompilowanie projektów po włączeniu funkcji Kontrola konta użytkownika  
 W przypadku kompilowania projektu Visual C++ w systemie Windows Vista z funkcji Kontrola konta użytkownika jest wyłączone, a później włączyć funkcji Kontrola konta użytkownika, należy wyczyścić, skompiluj ponownie projekt, aby działał poprawnie.  
  
## <a name="applications-that-require-administrative-privileges"></a>Aplikacje, które wymagają uprawnień administratora  
 Być domyślnie, konsolidatora Visual C++ osadza fragmentu funkcji Kontrola konta użytkownika do manifestu aplikacji z poziomu wykonywania `asInvoker`. Jeśli aplikacja wymaga uprawnień administracyjnych do poprawnego działania (na przykład, jeśli modyfikuje węzła HKLM rejestru lub zapisuje w chronionych obszarach dysku, takie jak katalog systemu Windows), należy zmodyfikować aplikacji.  
  
 Pierwsza opcja jest aby zmodyfikować fragment UAC manifest, aby zmienić poziom wykonywania na *requireAdministrator*. Aplikacja zostanie następnie monit o podanie poświadczeń administracyjnych przed uruchomieniem. Aby dowiedzieć się, jak to zrobić, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Drugą opcją jest nie można osadzić fragmentu UAC w manifeście, określając **: No** — opcja konsolidatora. W takim przypadku aplikacja jest uruchamiana zwirtualizowanych. Wszystkie zmiany wprowadzane w rejestrze lub system plików nie zachowa po zakończeniu aplikacji.  
  
 Poniższy schemat opisano, jak aplikacja jest uruchamiana w zależności od tego, czy jest włączona funkcja Kontrola konta użytkownika i określa, czy aplikacja ma manifestu kontroli konta użytkownika:  
  
 ![Zachowanie modułu ładującego systemu Windows Vista](media/uacflowchart.png "UACflowchart")  
  
## <a name="see-also"></a>Zobacz też  
 [Najlepsze rozwiązania](security-best-practices-for-cpp.md)