---
title: "Błąd PRJ0050 kompilacji projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0050
dev_langs: C++
helpviewer_keywords: PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a712c370de6f5a3a8cc9d0fd96e7937deddd201e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0050"></a>Błąd PRJ0050 kompilacji projektu
Nie można zarejestrować dane wyjściowe. Upewnij się, że masz odpowiednie uprawnienia do modyfikacji rejestru.  
  
 System kompilacji Visual C++ nie mógł zarejestrować dane wyjściowe kompilacji (plik dll lub .exe). Musisz być zalogowany jako administrator do modyfikacji rejestru.  
  
 Jeśli tworzysz Biblioteka DLL będzie można zarejestrować biblioteki dll, ręcznie przy użyciu regsvr32.exe, to należy wyświetlić informacje dotyczące niepowodzenia kompilacji.  
  
 Jeśli tworzysz nie Biblioteka DLL, sprawdź w dzienniku kompilacji dla polecenia, który powoduje błąd.