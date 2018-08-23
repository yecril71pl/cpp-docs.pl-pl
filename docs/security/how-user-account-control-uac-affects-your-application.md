---
title: Jak Kontrola konta użytkownika (UAC) wpływa na aplikację | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23266ca4b4d32146ed8627c6ce3ab1cc878d59cd
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600655"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Jak kontrola konta użytkownika (UAC) wpływa na aplikację?
Kontrola konta użytkownika (UAC) jest funkcją systemu Windows Vista, w którym użytkownik konta ma ograniczone uprawnienia. Można znaleźć szczegółowe informacje na temat funkcji Kontrola konta użytkownika w tych lokacjach:  
  
-   [Przewodnik krok po kroku kontroli konta użytkownika Windows Vista](http://go.microsoft.com/fwlink/p/?linkid=53781)  
  
-   [Najlepsze rozwiązania dla deweloperów i wytyczne dotyczące aplikacji w środowisku o najniższych uprawnieniach](http://go.microsoft.com/fwlink/p/?linkid=82444)  
  
-   [Opis i konfigurowanie Kontrola konta użytkownika w Windows Vista](http://go.microsoft.com/fwlink/p/?linkid=82445)  
  
## <a name="building-projects-after-enabling-uac"></a>Kompilowanie projektów po włączeniu funkcji Kontrola konta użytkownika  
 Jeśli tworzysz projekt Visual C++ w Windows Vista z funkcji kontroli konta użytkownika jest wyłączona, a później włączyć funkcji Kontrola konta użytkownika, należy wyczyścić i ponownie skompiluj projekt, aby mogła działać prawidłowo.  
  
## <a name="applications-that-require-administrative-privileges"></a>Aplikacje, które wymagają uprawnień administratora  
 Być domyślny, konsolidator Visual C++ osadza fragmentu funkcji Kontrola konta użytkownika do manifestu aplikacji z poziomem wykonywania `asInvoker`. Jeśli aplikacja wymaga uprawnień administracyjnych do poprawnego działania (na przykład w przypadku, gdy modyfikuje węzłem HKLM rejestru lub zapisuje w chronionych obszarach dysku, takie jak katalog Windows), należy zmodyfikować aplikację.  
  
 Pierwsza opcja jest zmodyfikowanie fragmentu UAC manifestu, aby zmienić poziom wykonywania *requireAdministrator*. Aplikacja następnie będzie monitować użytkownika o poświadczenia administracyjne, zanim zostanie ona uruchomiona. Aby dowiedzieć się, jak to zrobić, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Drugą opcją jest osadzaj fragmentu funkcji Kontrola konta użytkownika do manifestu, określając `/MANIFESTUAC:NO` — opcja konsolidatora. W takim przypadku aplikacja jest uruchamiana zwirtualizowanych. Wszelkie zmiany wprowadzone do rejestru lub systemu plików zostanie usunięte podczas instalacji aplikacji została zakończona.  
  
 Następujące schemat blokowy opisano, jak aplikacja jest uruchamiana w zależności od tego, czy jest włączona funkcja Kontrola konta użytkownika i tego, czy aplikacja ma manifestu kontroli konta użytkownika:  
  
 ![Windows Vista Loader zachowanie](media/uacflowchart.png "UACflowchart")  
  
## <a name="see-also"></a>Zobacz też  
 [Najlepsze rozwiązania dotyczące zabezpieczeń](security-best-practices-for-cpp.md)