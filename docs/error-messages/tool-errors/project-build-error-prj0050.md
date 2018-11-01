---
title: Błąd PRJ0050 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: ec2490bad70d2b2eb72cbb48771900f09f8c2f67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593430"
---
# <a name="project-build-error-prj0050"></a>Błąd PRJ0050 kompilacji projektu

Nie można zarejestrować dane wyjściowe. Upewnij się, że masz odpowiednie uprawnienia do modyfikowania rejestru.

System kompilacji Visual C++ nie mógł zarejestrować dane wyjściowe kompilacji, (biblioteki dll lub .exe). Musisz zalogować się jako administrator, aby zmodyfikować rejestr.

Jeśli tworzysz dll może próbować zarejestrować plik .dll, ręcznie przy użyciu regsvr32.exe, powinno to wyświetlenie informacji na temat przyczyny niepowodzenia kompilacji.

Jeśli nie tworzysz dll, Przyjrzyj się polecenie, które powoduje błąd w dzienniku kompilacji.