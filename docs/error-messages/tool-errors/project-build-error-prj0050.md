---
title: Błąd PRJ0050 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ad17614f693e313190dba9cc767c023981dec34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318516"
---
# <a name="project-build-error-prj0050"></a>Błąd PRJ0050 kompilacji projektu
Nie można zarejestrować dane wyjściowe. Upewnij się, że masz odpowiednie uprawnienia do modyfikacji rejestru.  
  
 System kompilacji Visual C++ nie mógł zarejestrować dane wyjściowe kompilacji (plik dll lub .exe). Musisz być zalogowany jako administrator do modyfikacji rejestru.  
  
 Jeśli tworzysz Biblioteka DLL będzie można zarejestrować biblioteki dll, ręcznie przy użyciu regsvr32.exe, to należy wyświetlić informacje dotyczące niepowodzenia kompilacji.  
  
 Jeśli tworzysz nie Biblioteka DLL, sprawdź w dzienniku kompilacji dla polecenia, który powoduje błąd.