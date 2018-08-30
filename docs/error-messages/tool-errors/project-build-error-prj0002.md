---
title: Błąd PRJ0002 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0002
dev_langs:
- C++
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc0e48130c17e04c2671395161452c9e66000047
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195718"
---
# <a name="project-build-error-prj0002"></a>Błąd PRJ0002 kompilacji projektu

> wynik błędu zwrócony z '*wiersza polecenia*".

W poleceniu *wiersza polecenia*, który powstał z danych wejściowych użytkownika w **stron właściwości** pojawi się okno dialogowe, zwrócony kod błędu, ale żadne informacje w **dane wyjściowe** okna .

Rozwiązanie do tego błędu zależy od tego, jakiego narzędzia wygenerował błąd. Dla MIDL otrzymasz wyobrażenie o przyczynie niepowodzenia, jeśli nie zdefiniowano /o (przekierować dane wyjściowe).

Przyczyną tego błędu w pliku wsadowym, takich jak niestandardowego kroku budowania lub zdarzenia kompilacji, który nie jest zawierającego wiele użytecznych informacji o warunkach błędów mogą być również.