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
ms.openlocfilehash: bb3949ea0db2f1667aecf1aeeefd922b192cbf41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100594"
---
# <a name="project-build-error-prj0050"></a>Błąd PRJ0050 kompilacji projektu

Nie można zarejestrować dane wyjściowe. Upewnij się, że masz odpowiednie uprawnienia do modyfikowania rejestru.

System kompilacji Visual C++ nie mógł zarejestrować dane wyjściowe kompilacji, (biblioteki dll lub .exe). Musisz zalogować się jako administrator, aby zmodyfikować rejestr.

Jeśli tworzysz dll może próbować zarejestrować plik .dll, ręcznie przy użyciu regsvr32.exe, powinno to wyświetlenie informacji na temat przyczyny niepowodzenia kompilacji.

Jeśli nie tworzysz dll, Przyjrzyj się polecenie, które powoduje błąd w dzienniku kompilacji.