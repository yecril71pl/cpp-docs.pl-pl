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
ms.workload: cplusplus
ms.openlocfilehash: e9d9b123da2e32db0f695c31bc9643a481d352b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0050"></a>Błąd PRJ0050 kompilacji projektu
Nie można zarejestrować dane wyjściowe. Upewnij się, że masz odpowiednie uprawnienia do modyfikacji rejestru.  
  
 System kompilacji Visual C++ nie mógł zarejestrować dane wyjściowe kompilacji (plik dll lub .exe). Musisz być zalogowany jako administrator do modyfikacji rejestru.  
  
 Jeśli tworzysz Biblioteka DLL będzie można zarejestrować biblioteki dll, ręcznie przy użyciu regsvr32.exe, to należy wyświetlić informacje dotyczące niepowodzenia kompilacji.  
  
 Jeśli tworzysz nie Biblioteka DLL, sprawdź w dzienniku kompilacji dla polecenia, który powoduje błąd.